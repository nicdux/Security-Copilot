# Plugin personalizado do Security Copilot — KQL do Sentinel — Logs do GCPAudit

#### Plugin do Security Copilot para executar uma consulta KQL dinâmica nos logs do GCPAudit em um workspace do Microsoft Sentinel para determinado usuário, endereço IP e intervalo de data e hora.

### Pré-requisitos

* [Security Copilot habilitado](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
* [Acesso para carregar plugins personalizados](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)
* [Workspace do Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-onboard) criado.
* [Conector de logs de auditoria do GCP](https://learn.microsoft.com/en-us/azure/sentinel/connect-google-cloud-platform?tabs=terraform%2Cauditlogs) do Microsoft Sentinel habilitado.
* Parâmetros do plugin KQL: nome do workspace do Microsoft Sentinel, ID da assinatura, nome do grupo de recursos e ID do locatário do Entra.

### Instruções
#### Carregar o plugin personalizado

1. Obtenha o arquivo [KQL-Sentinel-GCP.yaml](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Sentinel%20Custom%20Plugin%20Scenarios/GCP%20Audit%20Logs/KQL-Sentinel-GCP.yaml) deste diretório.
2. Modifique o arquivo yaml para especificar Entra TentantId, SubscriptionId, ResourceGroupName e WorkspaceName de sua instância do Sentinel.



3. [Carregue o plugin personalizado](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#add-custom-plugins) e verifique se ele está ativado.

### Uso do plugin

A seguir estão algumas consultas de exemplo que você pode usar para acionar este plugin. Você pode combinar os parâmetros UPN e endereço IP ou usar apenas um deles, mas sempre inclua um intervalo de data e hora.

* Descreva em detalhes, em alguns parágrafos, as operações do log de auditoria do GCP associadas a user@contoso.com nos últimos 90 dias.
* Descreva em detalhes, em alguns parágrafos, as operações do log de auditoria do GCP associadas ao IP 165.234.23.52 entre 4 de março de 2024 e 7 de março de 2024.

![Logs do O365](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Images/gcp-masked.png)
