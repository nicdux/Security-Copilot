
# Pré-requisitos

> <img src="https://raw.githubusercontent.com/Azure/Security-Copilot/refs/heads/main/Logic%20Apps/ciso-reporting/images/yt.png" alt="YouTube" width="28" height="20"> <a href="https://youtu.be/O4gT5yRwIpI" target="_blank">Minivídeo que apresenta os pré-requisitos (2 min): [Relatórios para CISO com o Security Copilot — configuração do protótipo — **#0** Pré-requisitos]</a>

1. A abordagem e a lógica usadas nesta solução podem ser aplicadas com o Security Copilot conectado a qualquer fonte de dados.
   No entanto, os plugins personalizados e os Promptbooks de exemplo fornecidos foram projetados para funcionar em um ambiente no qual a segurança é gerenciada pelo portal do SOC unificado (Defender + Sentinel).

2. Este procedimento pressupõe que você já tenha alguma experiência com o Security Copilot e uma capacidade computacional de base implantada.
   Caso contrário, antes de iniciar as etapas descritas abaixo, crie uma capacidade mínima de pelo menos 1 SCU, necessária para acessar e configurar o Security Copilot.
   Mais adiante no procedimento, você será instruído a aumentar o número de SCUs para o teste inicial e para a execução agendada.<br>

4. Os Logic Apps personalizados que chamam o Security Copilot o acessam por uma conexão OAuth autenticada com credenciais de usuário.
   O Security Copilot acessa os sistemas de origem de destino por meio de um modelo de acesso por representação. Portanto, as credenciais usadas na conexão OAuth do Logic App
   devem ter o direito de ler os dados de segurança nos sistemas de origem de destino. Nos Promptbooks fornecidos nesta solução, as fontes são Defender, Entra e Sentinel.
   Até o momento da redação deste documento, não é possível especificar 'Managed Identities' na conexão dos Logic Apps com o Security Copilot.
   Portanto, são necessárias 'credenciais de usuário', embora geralmente elas não sejam usadas por pessoas, mas apenas por este Logic App.
   Como pré-requisito para prosseguir com a instalação, é necessário criar credenciais de usuário com, no mínimo, as seguintes permissões 'ativas'
   (observe que permissões 'qualificadas' no PIM não são adequadas para uso em automação):
   - Security Reader no nível do locatário (para ler dados no Defender e no Entra)
   - Microsoft Sentinel Reader no nível do grupo de recursos do Sentinel (para ler dados no workspace do Sentinel)
   - Contributor no Microsoft Security Copilot (para acessar e interagir com o Security Copilot)<br>
   
   Essas credenciais também precisam ter uma licença do Microsoft 365 Exchange Online atribuída, pois serão usadas para enviar o email do relatório agendado.
   Recomendamos criar e usar um usuário dedicado com um nome claro, como 'Security Copilot Automation Account', e monitorar seu uso para garantir que
   qualquer tentativa anômala de entrada com essas credenciais gere um alerta.<br>
   Antes de iniciar este procedimento de configuração, recomendamos preparar uma sessão do navegador autenticada com as credenciais da nova Security Copilot Automation Account,
   na qual você já tenha acessado com êxito:
   - A caixa de correio do usuário no Exchange Online pelo acesso Web do Outlook
   - O portal do SOC unificado (Defender + Sentinel, security.microsoft.com)
   - A folha do Sentinel no Azure (portal.azure.com)
   - O portal do Security Copilot (no primeiro acesso, é necessário confirmar alguns tópicos introdutórios)

6. Para gerar um relatório sobre as recomendações identificadas pelo Defender for Cloud, como no terceiro prompt do Promptbook de exemplo de análise de postura documentado e compartilhado aqui,
   você também precisa habilitar a exportação contínua do Defender for Cloud, nas assinaturas relevantes do Azure, para o Log Analytics/Sentinel.
   
7. Antes de iniciar este procedimento de configuração, tenha as seguintes informações disponíveis:
   - Credenciais da "Security Copilot Automation Account"
   - Parâmetros de identificação do Sentinel (Subscription ID, Resource Group Name, Sentinel Workspace Name)
# Procedimento de configuração

## [**ETAPA 1**] Criar os Promptbooks

   > <img src="https://raw.githubusercontent.com/Azure/Security-Copilot/refs/heads/main/Logic%20Apps/ciso-reporting/images/yt.png" alt="YouTube" width="28" height="20"> <a href="https://youtu.be/JflMLaEJEQ0" target="_blank">Minivídeo que apresenta a criação dos Promptbooks (3 min): [Relatórios para CISO com o Security Copilot — configuração do protótipo — **#1** Criar Promptbooks]</a>

No portal do Security Copilot, acessado com credenciais que tenham a função Owner:
- [promptbook-incident-analysis](https://github.com/Azure/Security-Copilot/blob/main/Logic%20Apps/ciso-reporting/promptbook-incident-analysis.md)
- [OPCIONAL] [promptbook-posture-analysis](https://github.com/Azure/Security-Copilot/blob/main/Logic%20Apps/ciso-reporting/promptbook-posture-analysis.md)\
  OBSERVAÇÕES:
  - Este Promptbook de análise de postura e a automação relacionada estão em uma versão preliminar.
    Além de os prompts não estarem otimizados quanto ao consumo de capacidade computacional, o Promptbook como um todo ainda está bastante incompleto.
    Consulte [este artigo](https://www.linkedin.com/pulse/periodic-reporting-security-managers-cisos-using-stefano-pescosolido-fm80f/)
    para obter mais detalhes.<br>
  - Se você não habilitou o recurso de exportação contínua no Defender for Cloud, não inclua o terceiro prompt neste Promptbook de exemplo.

## [**ETAPA 2**] Implantar o Logic App [ciso-get-users-status.json](https://github.com/Azure/Security-Copilot/blob/main/Logic%20Apps/ciso-reporting/ciso-get-users-status.json), usado por uma das habilidades do plugin personalizado para análise de incidentes

   > <img src="https://raw.githubusercontent.com/Azure/Security-Copilot/refs/heads/main/Logic%20Apps/ciso-reporting/images/yt.png" alt="YouTube" width="28" height="20"> <a href="https://youtu.be/ETpt88CddQU" target="_blank">Minivídeo que apresenta a criação do Logic App **ciso-get-users-status** (>2 min): [Relatórios para CISO com o Security Copilot — configuração do protótipo — **#2** Instalar o GetUsersStatus]</a>

No portal do Azure, acessado com credenciais que tenham uma função administrativa:
  - OBSERVAÇÃO: atualmente, não há um botão "Deploy in Azure"; é necessário realizar uma implantação manual.
  - Edite a conexão com o Security Copilot e autentique-se com as credenciais da Security Copilot Automation Account.

## [**ETAPA 3**] Implantar o Logic App [CfS-SendPromptbookResultsByEmail](https://github.com/Azure/Security-Copilot/tree/main/Logic%20Apps/CfS-SendPromptbookResultsByEmail) para criar a automação "**CISO Incidents Analysis**"

   > <img src="https://raw.githubusercontent.com/Azure/Security-Copilot/refs/heads/main/Logic%20Apps/ciso-reporting/images/yt.png" alt="YouTube" width="28" height="20"> <a href="https://youtu.be/F3PMAPl7ptc" target="_blank">Minivídeo que apresenta a criação do Logic App **CISO Incidents Analysis** (>5 min): [Relatórios para CISO com o Security Copilot — configuração do protótipo — **#3** Instalar a automação de análise de incidentes]</a>

No portal do Azure, acessado com credenciais que tenham uma função administrativa:
  - Use o botão "Deploy in Azure".
  - Edite a conexão com o Security Copilot e autentique-se com as credenciais da Security Copilot Automation Account.
  - Edite a conexão com o Office 365 e autentique-se com as credenciais da Security Copilot Automation Account.
  - Escolha o Promptbook "promptbook-incident-analysis" e especifique seus parâmetros. Normalmente, você pode definir:
    - TOP_INCIDENTS_NUMBER = 10
    - SEVERITIES = High and Medium
    - TIME_FRAME = last week (OBSERVAÇÃO: se alterar esse valor, você deverá modificar de modo correspondente o conteúdo do parâmetro ReplacePromptsInOutput do fluxo de trabalho)
    - RESPONSE_LANGUAGE = defina um idioma compatível com o Security Copilot
    - RESPONSE_LANGUAGE = 10
    - TOP_IMPACTED_USERS_NUMBER = 5 (esse número afeta significativamente o consumo e, portanto, os custos da solução.)
  - Defina todos os parâmetros do Logic App. Especificamente, verifique se você definiu:
    - O título e o assunto do email
    - EmailRecipients
    - SkipPromptsInOutput e ReplacePromptsInOutput conforme especificado no final do arquivo
      [promptbook-incident-analysis](https://github.com/Azure/Security-Copilot/blob/main/Logic%20Apps/ciso-reporting/promptbook-incident-analysis.md)
  - Defina a recorrência. Normalmente, ela deve ser configurada para uma execução semanal, por exemplo, às segundas-feiras, às 6h.
  - Por enquanto, mantenha o Logic App desabilitado. Ele será habilitado quando todas as configurações necessárias estiverem prontas.
 

## [**ETAPA 4**] [OPCIONAL] Implantar o Logic App [CfS-SendPromptbookResultsByEmail](https://github.com/Azure/Security-Copilot/tree/main/Logic%20Apps/CfS-SendPromptbookResultsByEmail) para criar a automação "**CISO Posture Analysis**"<br>
  OBSERVAÇÃO: esta automação e o Promptbook relacionado estão em uma versão preliminar.
  Além de os prompts não estarem otimizados quanto ao consumo de capacidade computacional, o Promptbook como um todo ainda está bastante incompleto.
  Consulte [este artigo](https://www.linkedin.com/pulse/periodic-reporting-security-managers-cisos-using-stefano-pescosolido-fm80f/)
  para obter mais detalhes sobre como esse Promptbook deve ser aprimorado.

   > <img src="https://raw.githubusercontent.com/Azure/Security-Copilot/refs/heads/main/Logic%20Apps/ciso-reporting/images/yt.png" alt="YouTube" width="28" height="20"> <a href="https://youtu.be/yBmJhBJohMg" target="_blank">Minivídeo que apresenta a criação do Logic App **CISO Posture Analysis** (~4 min): [Relatórios para CISO com o Security Copilot — configuração do protótipo — **#4** Instalar a automação de análise de postura]</a>
  
  - Use o botão "Deploy in Azure".
  - Edite a conexão com o Security Copilot e autentique-se com as credenciais da Security Copilot Automation Account.
  - Edite a conexão com o Office 365 e autentique-se com as credenciais da Security Copilot Automation Account.
  - Escolha o Promptbook "promptbook-posture-analysis" e especifique seus parâmetros. Normalmente, você pode definir:
    - WORDS_NUMBER = 50
    - NUMBER_OF_DAYS = 30
    - NUMBER_OF_RECOMMENDATIONS = 10
    - SEVERITIES = High and Medium 
  - Defina todos os parâmetros do Logic App. Especificamente, verifique se você definiu:
    - HtmlBodyHeader para alterar o tom de cor do email
      (consulte [promptbook-posture-analysis](https://github.com/Azure/Security-Copilot/blob/main/Logic%20Apps/ciso-reporting/promptbook-posture-analysis.md))
    - O título e o assunto do email
    - EmailRecipients
  - Defina a recorrência. Normalmente, ela deve ser configurada para uma execução semanal, por exemplo, às segundas-feiras, às 6h.
  - Por enquanto, mantenha o Logic App desabilitado. Ele será habilitado quando todas as configurações necessárias estiverem prontas.

## [**ETAPA 5**] Implantar os plugins personalizados

   > <img src="https://raw.githubusercontent.com/Azure/Security-Copilot/refs/heads/main/Logic%20Apps/ciso-reporting/images/yt.png" alt="YouTube" width="28" height="20"> <a href="https://youtu.be/SKWVNzeDx6g" target="_blank">Minivídeo que apresenta a criação dos plugins personalizados (8 min): [Relatórios para CISO com o Security Copilot — configuração do protótipo — **#5** Plugins personalizados]</a>
  
  - Prepare e implante o plugin personalizado [ciso-incidents-summary-man](https://github.com/Azure/Security-Copilot/blob/main/Logic%20Apps/ciso-reporting/ciso-incidents-summary-man.yaml)
    (usado pela automação "**CISO Incidents Analysis**").<br>
    OBSERVAÇÕES:
    - Este plugin personalizado percorre os usuários especificados na entrada e consulta o Entra para obter o status de habilitação e de risco de cada um.
      Devido à existência do loop, ele pode consumir muitas unidades computacionais. Avalie se essa evidência agrega valor ao relatório.
      Para incluir essa evidência no relatório de saída, recomendamos limitar o número de usuários incluídos no loop
      definindo um valor baixo no parâmetro TOP_IMPACTED_USERS_NUMBER especificado no Logic App "**CISO Posture Analysis**" para a chamada ao Promptbook
      [promptbook-incident-analysis](https://github.com/Azure/Security-Copilot/blob/main/Logic%20Apps/ciso-reporting/promptbook-incident-analysis.md)
      .
      Se decidir remover a chamada a esse loop, remova também o prompt relacionado no Promptbook e reorganize de modo correspondente
      os valores dos parâmetros SkipPromptsInOutput e ReplacePromptsInOutput no mesmo Logic App "**CISO Posture Analysis**".
    - Nesta primeira versão preliminar da solução, o arquivo de especificação OpenAPI
      [ciso-incidents-summary-api-spec.yaml](https://github.com/Azure/Security-Copilot/blob/main/Logic%20Apps/ciso-reporting/ciso-incidents-summary-api-spec.yaml)
      contém dois espaços reservados cujos valores devem ser substituídos de acordo com os componentes da URL completa do gatilho do Logic App implantado
      [ciso-get-users-status.json](https://github.com/Azure/Security-Copilot/blob/main/Logic%20Apps/ciso-reporting/ciso-get-users-status.json).
      Especificamente, defina:
      - <BASE_PATH> como o caminho base dessa URL (por exemplo, https://prod-32.northeurope.logic.azure.com:443)
      - <WORKFLOW_ID> como a Workload ID dessa URL (por exemplo, 836c758b842f46549f57c861ca856c7b)
      Em seguida, salve o arquivo editado em um armazenamento público na Internet que seja acessível ao Security Copilot, por exemplo, em outro repositório público do GitHub.
      Depois, modifique sua cópia do arquivo [ciso-incidents-summary-man.yaml](https://github.com/Azure/Security-Copilot/blob/main/Logic%20Apps/ciso-reporting/ciso-incidents-summary-man.yaml)
      substituindo o espaço reservado do parâmetro OpenApiSpecUrl pela URL pública do arquivo de especificação OpenAPI modificado.
  - [OPCIONAL] Implante o plugin personalizado [ciso-posture-summary-man](https://github.com/Azure/Security-Copilot/blob/main/Logic%20Apps/ciso-reporting/ciso-incidents-summary-man.yaml)
    (usado pela automação "**CISO Posture Analysis**"). Essa implantação não requer personalização específica: basta baixar
    o arquivo do modelo no GitHub e carregá-lo no Security Copilot.<br>
  - [OPCIONAL] Implante o plugin personalizado [Sentinel-SOC-Optimization-CustomPlugin] https://github.com/stefanpems/cfs/tree/main/Sentinel-SOC-Optimization-CustomPlugin
    (usado pela automação "**CISO Posture Analysis**"). Essa implantação não requer personalização específica: basta baixar
    o arquivo do modelo no GitHub e carregá-lo no Security Copilot.<br>
    OBSERVAÇÕES:
    - Ao adicionar esse plugin personalizado, forneça os parâmetros de identificação do Sentinel (Subscription ID, Resource Group Name, Sentinel Workspace Name).
    - Se não quiser instalar esse plugin personalizado, remova o segundo prompt do
      [promptbook-posture-analysis](https://github.com/Azure/Security-Copilot/blob/main/Logic%20Apps/ciso-reporting/promptbook-posture-analysis.md) implantado em uma das etapas anteriores.


## [**ETAPA 6**] Habilitar a automação "**CISO Incidents Analysis**" e aguardar a conclusão da primeira execução automática

   > <img src="https://raw.githubusercontent.com/Azure/Security-Copilot/refs/heads/main/Logic%20Apps/ciso-reporting/images/yt.png" alt="YouTube" width="28" height="20"> <a href="https://youtu.be/eX5VCtuWTac" target="_blank">Minivídeo que apresenta a primeira execução da automação de análise de incidentes (4 min): [Relatórios para CISO com o Security Copilot — configuração do protótipo — **#6** Executar análise de incidentes]</a>

   No portal do Security Copilot, acessado com as credenciais da Security Copilot Automation Account:
   - [**ETAPA 6.1**] Verifique se todos os plugins personalizados recém-instalados estão habilitados.
     Opcionalmente, teste o Logic App [ciso-get-users-status.json](https://github.com/Azure/Security-Copilot/blob/main/Logic%20Apps/ciso-reporting/ciso-get-users-status.json)
     chamando a habilidade "CISO Get Users Staus" de [ciso-incidents-summary-man](https://github.com/Azure/Security-Copilot/blob/main/Logic%20Apps/ciso-reporting/ciso-incidents-summary-man.yaml).
     Para isso, use as seguintes entradas:
     - api-version = 2016-10-01
     - sp = /triggers/AnalyzeUPNsCall/run
     - sv = 1.0
     - users_upn = uma ou mais UPNs de usuários do seu locatário separadas por vírgulas


   No portal do Security Copilot, acessado com credenciais que tenham a função Owner:
   - [**ETAPA 6.2**] Aumente temporariamente o número de SCUs para garantir que as primeiras execuções de "teste" sejam concluídas com êxito.
  
   No portal do Azure, acessado com credenciais que tenham uma função administrativa:<br>
   - [**ETAPA 6.3**] Habilite a automação "**CISO Incidents Analysis**" e aguarde sua primeira execução automática.
  
## [**ETAPA 7**] Habilitar a automação "**CISO Posture Analysis**" e aguardar a conclusão da primeira execução automática

   > <img src="https://raw.githubusercontent.com/Azure/Security-Copilot/refs/heads/main/Logic%20Apps/ciso-reporting/images/yt.png" alt="YouTube" width="28" height="20"> <a href="https://youtu.be/4wZ4vEebCEo" target="_blank">Minivídeo que apresenta a primeira execução da automação de análise de postura (~1 min): [Relatórios para CISO com o Security Copilot — configuração do protótipo — **#7** Executar análise de postura]</a>
  
   No portal do Azure, acessado com credenciais que tenham uma função administrativa:<br>
   - Habilite a automação "**CISO Posture Analysis**" e aguarde sua primeira execução automática.

## [**ETAPA 8**] Agendar a execução dos relatórios e o aumento periódico necessário de SCUs

   > <img src="https://raw.githubusercontent.com/Azure/Security-Copilot/refs/heads/main/Logic%20Apps/ciso-reporting/images/yt.png" alt="YouTube" width="28" height="20"> <a href="https://youtu.be/Z6UKUyInMGY" target="_blank">Minivídeo que apresenta a configuração da atribuição periódica de SCUs e da recorrência das automações de relatório (>8 min): [Relatórios para CISO com o Security Copilot — configuração do protótipo — **#8** Agendar SCUs e relatórios]</a>
   
  - Defina a recorrência no Logic App "**CISO Incidents Analysis**".
  - Defina a recorrência no Logic App "**CISO Posture Analysis**".
  - Agende a implantação automática das unidades computacionais (SCUs) dedicadas à execução dessas automações
    para garantir capacidade suficiente, além da capacidade "de base" usada pelos usuários e por outras automações, sempre que elas forem executadas.
    Por exemplo, implante duas instâncias do Logic App [cfs-set-X-SCUs](https://github.com/stefanpems/cfs/tree/main/cfs-set-X-SCUs):
    - Uma para aumentar a capacidade em N SCUs acima da base
    - Outra para reduzir a capacidade em N SCUs quando a execução dessas automações for concluída
    
