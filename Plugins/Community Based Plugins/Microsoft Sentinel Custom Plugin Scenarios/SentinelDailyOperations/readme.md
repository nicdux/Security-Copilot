# Plugin personalizado do Security Copilot — KQL do Sentinel — SentinelDailyOperations

### Pré-requisitos

* [Security Copilot habilitado](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
* [Acesso para carregar plugins personalizados](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)
* [Workspace do Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-onboard) criado.
* Parâmetros do plugin KQL: nome do workspace do Microsoft Sentinel, ID da assinatura, nome do grupo de recursos e ID do locatário do Entra.

### Instruções
#### Carregar o plugin personalizado

1. Obtenha o arquivo [KQL_SentinelDailyOperationsSample.yaml](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Sentinel%20Custom%20Plugin%20Scenarios/SentinelDailyOperations/KQL_SentinelDailyOperationsSample.yml) deste diretório.
2. Modifique o arquivo yaml para especificar Entra `TentantId`, `SubscriptionId`, `ResourceGroupName` e `WorkspaceName` de sua instância do Sentinel.
3. Carregue o plugin personalizado.