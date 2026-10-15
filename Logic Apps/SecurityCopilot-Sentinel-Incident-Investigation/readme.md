# SecurityCopilot-Sentinel-Incident-Investigation
**Autores: Pratik Lal, Innocent Wafula, Stefano Pescosolido**

## Visão geral

Este Logic App automatiza a investigação de incidentes no Microsoft Sentinel usando prompts e habilidades internas do Microsoft Security Copilot. Ele foi projetado para:
- Ler as entidades de incidentes do Microsoft Sentinel.
- Processar e normalizar as entidades.
- Enviar prompts ao Security Copilot para analisar cada tipo de entidade.
- Resumir as saídas em um formato predefinido.
- Atualizar os comentários do incidente do Microsoft Sentinel para análise pelo investigador (a gravação no incidente do Sentinel pode ser desabilitada para facilitar os testes iniciais).
- Opcionalmente, enviar por email o resultado da investigação.

Ao usar este Logic App, as equipes do Centro de Operações de Segurança (SOC) e de resposta a incidentes podem reduzir significativamente o tempo de investigação, obter resultados de análise consistentes e aprimorar o processo de resposta a incidentes.

## Pré-requisitos
- O usuário ou a entidade de serviço que implanta este Logic App deve ter a função Contributor no grupo de recursos do Azure.
- O Microsoft Security Copilot deve estar habilitado no locatário do Azure.
- O usuário deve ter acesso ao Microsoft Security Copilot para enviar prompts por meio da autenticação no conector do Microsoft Security Copilot no Logic App.
- O workspace do Microsoft Sentinel deve estar configurado.
- Opcionalmente, obtenha uma chave de API do AbuseIPDB para verificar a reputação de endereços IP. [Saiba mais.](https://learn.microsoft.com/en-us/copilot/security/plugin-abuseipdb)
- Nas configurações do Copilot, habilite os plugins Defender, Sentinel, Entra, Intune, MDTI e AbuseIPDB para a conta de usuário configurada na conexão de API do Logic App com o Security Copilot.


## Implantação


<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FSecurity-Copilot%2Fmain%2FLogic%2520Apps%2FSecurityCopilot-Sentinel-Incident-Investigation%2Fazuredeploy.json" target="_blank">
<img src="https://aka.ms/deploytoazurebutton"/>
</a>
<br>

## Pós-implantação
- Autentique os conectores do Microsoft Sentinel e do Security Copilot no Logic App. Para o gatilho do Microsoft Sentinel, você pode escolher a autenticação baseada em OAuth, entidade de serviço ou identidade gerenciada.
     <br>
     <img src="https://github.com/pratik-lal/Security-Copilot/blob/SecurityCopilot-Sentinel-Incident-Investigation/Logic%20Apps/SecurityCopilot-Sentinel-Incident-Investigation/images/sentinel-trigger-authentication.png"/></br>
- Escolha Client Certificate Auth ou OAuth (usando uma conta de usuário que possa enviar prompts) para criar a conexão com o conector dos Logic Apps para o Microsoft Security Copilot.
     <br>
     <img src="https://github.com/pratik-lal/Security-Copilot/blob/SecurityCopilot-Sentinel-Incident-Investigation/Logic%20Apps/SecurityCopilot-Sentinel-Incident-Investigation/images/copilot-for-security-authentication.png"/>
     </br>
- Importante: a conta selecionada para autenticação no Security Copilot deve ter a função Contributor no Security Copilot e privilégios de leitor no Defender, Sentinel, Entra e Intune.
- Da mesma forma, autentique a conexão de API com o Exchange Online (a configuração correta da conexão é necessária mesmo que o Logic App esteja configurado para não enviar emails).<br>
- Atribua a função 'Microsoft Sentinel Responder' à identidade gerenciada do Logic App no grupo de recursos que contém o workspace do Log Analytics do Sentinel.<br>
- Defina os valores dos parâmetros do Logic App.<br>
<img src="./images/params.png"/>
- Automatize a investigação de incidentes do Sentinel adicionando o Logic App a uma regra de automação do Microsoft Sentinel. Como alternativa, este Logic App pode ser chamado sob demanda: clique com o botão direito em um incidente do Sentinel e escolha a opção **Run Playbook**.

## Habilidades do Microsoft Security Copilot
- As habilidades internas a seguir são usadas para investigar cada tipo de entidade de incidente.

| Entidade do incidente | Habilidade do Security Copilot |
| --------------- | -------------------------- |
| Nome do processo/linha de comando | ProcessAnalyzer |
| Nome da conta | GetEntraUserDetails |
| Nomes das contas | GetEntraRiskyUsers |
| Nome do dispositivo | GetIntuneDevices |
| Endereço IP | AbuseIPDB |
| Indicador de comprometimento (IoC) | GetReputationsForIndicators |


## Modelo de investigação de incidentes
- O resumo da investigação automatizada do incidente segue a ordem abaixo. Modifique o prompt para reordenar ou alterar o modelo de investigação.
    - Visão geral do incidente,
    - Descrição do incidente,
    - Análise de endereços IP,
    - Análise de contas,
    - Análise de risco dos usuários,
    - Análise de dispositivos,
    - Análise de processos,
    - Análise de indicadores do MDTI,
    - Possíveis etapas de mitigação e conclusão
<br>
<img src="https://github.com/pratik-lal/Security-Copilot/blob/SecurityCopilot-Sentinel-Incident-Investigation/Logic%20Apps/SecurityCopilot-Sentinel-Incident-Investigation/images/copilot-for-security-investigation-prompt.png"/>
</br>
