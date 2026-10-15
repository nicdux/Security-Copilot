# Tutorial: gerar relatórios de incidentes de risco com o Security Copilot

Objetivo: como analista ou gerente de SecOps, quero criar automaticamente relatórios detalhados de incidentes que resumam as tarefas críticas de investigação e as evidências dos incidentes de maior risco da minha organização.

A [habilidade de relatório de incidentes](https://learn.microsoft.com/en-us/defender-xdr/security-copilot-m365d-create-incident-report) do Copilot for Security gera um relatório detalhado do incidente com base nas ações automatizadas, nos analistas envolvidos na resposta ao incidente e nos comentários dos analistas. Independentemente de as equipes de segurança usarem o Microsoft Sentinel, o Defender XDR ou ambos, todos os dados relevantes do incidente são adicionados ao relatório gerado.

Uma forma de coletar automaticamente evidências críticas relacionadas a um incidente é usar o [Sentinel Triage Assistant (STAT)](https://techcommunity.microsoft.com/t5/microsoft-sentinel-blog/introducing-the-microsoft-sentinel-triage-assistant-stat/ba-p/3845846). O STAT coleta, por meio de vários [módulos do STAT](https://github.com/briandelmsft/SentinelAutomationModules/tree/main/Modules), todas as evidências relacionadas às entidades do incidente e as adiciona como comentários no incidente. Assim, a habilidade de relatório de incidentes do Copilot for Security pode usar essas evidências ao gerar um relatório. O STAT também tem um [módulo de pontuação de risco](https://github.com/briandelmsft/SentinelAutomationModules/tree/main/Modules/ScoringModule), que permite gerar um valor inteiro para indicar o nível geral de risco de um incidente. Com a pontuação de risco do incidente, podemos marcar os incidentes com um valor inteiro associado ao risco total e procurar regularmente aqueles com maior nível de risco para gerar relatórios usando o Copilot for Security.

Esses relatórios podem ser executados após o incidente, durante sua criação (depois da execução do STAT) ou conforme um agendamento, para verificar por amostragem como os analistas concluíram o trabalho.

## Pré-requisitos

Microsoft Sentinel configurado com a nova [versão prévia do SOC unificado](https://learn.microsoft.com/en-us/azure/sentinel/connect-microsoft-365-defender?tabs=MDE) habilitada.

[Sentinel Triage Assistant (STAT)](https://github.com/briandelmsft/SentinelAutomationModules) implantado, com todos os módulos adicionando comentários, o módulo de pontuação configurado e os incidentes do Sentinel marcados como "Risk Score - totalRiskScore".

[Microsoft Copilot for Security](https://learn.microsoft.com/en-us/copilot/security/get-started-security-copilot) implantado com capacidade de SCU disponível.

## Etapa 1: implantar este Logic App em sua organização

Se o ambiente do Azure atender aos pré-requisitos e você souber usar modelos do Azure Resource Manager, estas etapas ajudarão a entrar diretamente no Azure e a abrir o modelo do Azure Resource Manager no portal do Azure. Para obter mais informações, consulte o artigo [Implantar recursos com modelos do Azure Resource Manager e o portal do Azure](https://docs.microsoft.com/azure/azure-resource-manager/templates/overview).

Selecione a imagem a seguir para entrar com sua conta do Azure e abrir o Logic App no portal do Azure:

   [![Implantar no Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FSecurity-Copilot%2Fmain%2FLogic%2520Apps%2FGet-CfS-Risky-Incidents-Report%2Fazuredeploy.json)

1. No portal, na página **Custom deployment**, insira ou selecione estes valores:

   | Propriedade | Valor | Descrição |
   |----------|-------|-------------|
   | **Subscription** | <*Azure-subscription-name*> | Nome da assinatura do Azure que será usada |
   | **Resource group** | <*Azure-resource-group-name*> | Nome de um grupo de recursos do Azure novo ou existente |
   | **Region** |  <*Azure-region-for-all-resources*> | Região do Azure a ser usada por todos os recursos, se for diferente do valor padrão. Este exemplo usa o valor padrão, que é a localização do grupo de recursos. |
   | **Playbook Name**|  <*PlaybookName*> | Nome do Logic App implantado. |
   | **Incident Count** | <*incidentCount*> | Número máximo de incidentes a serem retornados (por exemplo, 10) |
   | **Look Back Days** | <*lookBack*> | Número de dias anteriores que serão consultados (por exemplo, -7) |
   | **Min Risk Score** | <*minRiskScore*> | Pontuação de risco mínima dos incidentes no STAT (por exemplo, 0) |

1. Quando terminar, selecione **Review + Create** e, por fim, **Create**.

## Etapa 2: autenticar o Logic App no Azure Monitor, no Teams e no Copilot for Security

Edite o Logic App e modifique as conexões das seguintes ações:

**Get Riskiest Incidents** — modifique esta conexão usando uma identidade com permissão para se conectar ao workspace do Log Analytics onde residem os incidentes do Sentinel. Selecione Subscription, Resource Group, Resource Type e Resource Name de modo que apontem para o workspace do Log Analytics.

**Cfs Risk Incident Report** — modifique esta conexão usando uma identidade com permissões para se conectar à sua instância do Copilot for Security.

**Post Risk Incident Report in Teams Channel** — modifique esta conexão usando uma identidade com permissões para publicar uma mensagem em um canal do Teams. Não se esqueça de escolher a equipe e a ID do canal.

**Add Risk Incident Report to Incident** e **Tag Risk Incident with Copilot Summary** — modifique estas conexões usando uma identidade com acesso para alterar os incidentes no workspace do Sentinel.

![Get-CFS-Risky-Incidents-Report](https://github.com/Azure/Copilot-For-Security/blob/main/Images/Logicapp%20images/Get-CFS-Risky-Incidents-Report.png)

## Próximas etapas

Este Logic App é agendado para execução semanal. Você pode modificar o agendamento na etapa inicial de recorrência.

Você pode modificar a consulta KQL na ação **Get Riskiest Incidents**. Por padrão, essa consulta examina a tabela SecurityIncident no Sentinel e analisa a pontuação de risco do STAT marcada na coluna de rótulos. Em seguida, ela retorna os dez incidentes de maior risco com base na pontuação total marcada nos incidentes do STAT. Modifique a consulta conforme necessário para examinar todos os incidentes, apenas incidentes com determinado status (por exemplo, Closed ou Resolved), incidentes atribuídos a um analista específico etc.

1. Acione manualmente o Playbook ou aguarde sua execução agendada.
2. O Copilot for Security gera relatórios para cada incidente encontrado, adiciona o relatório ao incidente por meio de um comentário do Sentinel, marca o incidente com "Copilot Summary" e publica o relatório no canal desejado do Teams.

## Exemplos de relatórios de incidentes

Os exemplos de relatórios de incidentes a seguir foram gerados apenas com um único prompt usando a [habilidade de relatório de incidentes](https://learn.microsoft.com/en-us/defender-xdr/security-copilot-m365d-create-incident-report) do Copilot for Security em incidentes submetidos à triagem pelo [Sentinel Triage Assistant (STAT)](https://github.com/briandelmsft/SentinelAutomationModules).

---------------------------------------------------------------------------------------------------------

26 de abril de 2024, 10h15
**Relatório de incidente**
pelo Copilot — 26 de abril de 2024, 10h15

Título do incidente
Multi-stage incident on one endpoint

**Detalhes do incidente**
**Analistas** Analyst@contoso.com
**Hora de criação** 04/18/2024 02:29:44
**Primeiro log** 04/26/2024 02:41:12
**Último log** 04/26/2024 03:05:02
**Hora de fechamento** 04/26/2024 02:59:53

**Resumo do incidente**
O incidente de gravidade alta intitulado 'Multi-stage incident on one endpoint' ocorreu entre 2024-04-18 02:29:44 UTC e 2024-04-26 10:29:44 UTC.
**Impacto:** o incidente começou em 2024-04-18 02:29:44 UTC, quando uma correspondência de inteligência contra ameaças (TI) foi encontrada entre uma entidade IP e um W3CIISLog. O IP 185.224.128.43 estava afetando o computador 'CONTOSO-ADMIN'.
Mais tarde naquele dia, às 2024-04-18 10:29:44 UTC, outra correspondência de TI foi encontrada, desta vez envolvendo os endereços IP 45.56.108.128 e 57.129.23.166, que novamente afetavam o computador 'CONTOSO-ADMIN'.
**CredentialAccess:** o incidente se agravou em 2024-04-26 01:52:34 UTC, quando houve um número excessivo de tentativas de entrada com falha em um servidor Web IIS provenientes de endereços IP desconhecidos. Os IPs envolvidos eram 45.128.232.229 e 185.224.128.43, e o computador afetado era novamente 'CONTOSO-ADMIN'. Isso sugere uma tentativa de obter acesso não autorizado ao sistema.

**Classificação**
**Positivo benigno — teste de segurança**
O incidente fazia parte de um exercício de teste de segurança envolvendo um honeypot. O computador envolvido, CONTOSO-ADMIN, aceitou uma conexão de entrada de um endereço IP associado a uma botnet. No entanto, não foram encontrados alertas relacionados ao incidente nem entidades em risco.

**Ações de investigação**
Megan Bowen foi atribuída ao incidente pelo Playbook 'LA-ASI-ShiftAssignment_v3'.
O endereço IP 185.224.128.43, localizado em Wormer, Noord-Holland, Países Baixos, e associado à organização Alsycon B.V., foi identificado como parte do incidente.
O endereço IP foi sinalizado pelos dados de inteligência contra ameaças com uma pontuação de confiança de 100, indicando que faz parte de uma botnet.
O endereço IP foi denunciado 8299 vezes por abuso e está listado no AbuseIPDB.
O computador envolvido no incidente, CONTOSO-ADMIN, aceitou uma conexão de entrada do endereço IP mencionado na porta 80 usando o protocolo TCP.
A pontuação de risco total calculada para o incidente foi 20, principalmente devido ao risco de inteligência contra ameaças.
O incidente foi identificado como parte de um exercício de teste de segurança que envolvia um honeypot.
Os playbooks "LA-ASI-ShiftAssignment_v3" e "Get-SOCGPT-Triage-V2" foram acionados durante o incidente.
Não foram encontrados alertas relacionados ao incidente nem entidades em risco.

**Ações de correção**
Ainda não há ações de correção

**Ações de acompanhamento**
Ainda não há ações de acompanhamento

---------------------------------------------------------------------------------------------------------

25 de abril de 2024, 19h33
**Relatório de incidente**
pelo Copilot — 25 de abril de 2024, 19h27

**Título do incidente**
Bitsadmin abuse by domain user account on one endpoint

**Detalhes do incidente**
Analistas analyst@contoso.com
Hora de criação 04/26/2024 00:00:01
Primeiro log 04/26/2024 00:15:44
Último log 04/26/2024 02:22:17
Hora de fechamento 04/26/2024 02:22:17

**Resumo do incidente**
O incidente de gravidade alta 'Bitsadmin abuse by domain user account on one endpoint' ocorreu em 2024-04-26 00:00:01 UTC.
DefenseEvasion: o incidente envolveu o usuário 'user' no dispositivo 'contoso-util' (WindowsServer2019). O usuário estava associado ao abuso do Bitsadmin, uma ferramenta de linha de comando usada pelos administradores para criar trabalhos de download ou upload e monitorar seu progresso. O abuso envolveu os processos 'bitsadmin.exe' e 'cmd.exe', indicando uma possível tentativa de evitar a detecção ou as defesas do sistema.

**Classificação**
**Positivo benigno — teste de segurança**
O incidente foi classificado como "BenignPositive" porque foi confirmado como uma simulação. O usuário envolvido, user@contoso.com, era analista de SecOps no departamento de Operações de Segurança e tinha várias funções administrativas. Apesar da presença de sete alertas relacionados, o nível de risco do usuário era baixo, sem falhas de MFA, fraudes de MFA, detecções de risco ou relatórios de atividade suspeita. O usuário também constava na lista de observação VIP. A pontuação de risco dos dispositivos usados pelo usuário e presentes no incidente era média, com baixo nível de exposição. A pontuação de ameaça do usuário era 70 e apresentava tendência de alta. No entanto, não foram encontrados dados correspondentes de inteligência contra ameaças, o que reforçou a classificação.

**Ações de investigação**
O incidente foi atribuído a Megan Bowen pelo Playbook 'LA-ASI-ShiftAssignment_v3' para investigação.
Foram encontrados sete alertas relacionados, inclusive Bitsadmin abuse by domain user account, User and IP address reconnaissance (SMB), Firewall tampering by domain user account, User and group membership reconnaissance (SAMR) e Anomalous account lookups.
O nível de risco do usuário foi avaliado como baixo, sem falhas de MFA, fraudes de MFA, detecções de risco ou relatórios de atividade suspeita.
Foi observada a presença do usuário na lista de observação VIP.
Foi realizada uma pesquisa por dados correspondentes de inteligência contra ameaças, mas nenhum foi encontrado.
A pontuação de risco dos dispositivos usados pelo usuário e presentes no incidente foi avaliada como média, com baixo nível de exposição.
A pontuação de ameaça do usuário foi calculada como 70 e apresentava tendência de alta.
Dois registros de atividades de DLP de ponto de extremidade de user@contoso.com foram encontrados na pesquisa do Sentinel, envolvendo a cópia de arquivos confidenciais para um compartilhamento de rede.
A pontuação de risco total calculada para o incidente foi 106; o maior risco era decorrente dos alertas relacionados e da presença do usuário na lista de observação.

Ações de correção
Ainda não há ações de correção

Ações de acompanhamento
Ainda não há ações de acompanhamento

---------------------------------------------------------------------------------------------------------
