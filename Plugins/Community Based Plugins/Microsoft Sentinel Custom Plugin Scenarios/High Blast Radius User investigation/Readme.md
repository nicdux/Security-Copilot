# Plugin KQL personalizado do Security Copilot — Investigar ameaças baseadas em identidade com o Security Copilot e o Microsoft Sentinel

#### Plugin do Security Copilot que usa dados de anomalias gerados pela UEBA do Microsoft Sentinel referentes a usuários de grande raio de impacto.

### Pré-requisitos

* [Security Copilot habilitado](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
* [Acesso para carregar plugins personalizados](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)
* [Workspace do Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-onboard) criado.
* [UEBA do Microsoft Sentinel habilitada](https://learn.microsoft.com/en-us/azure/sentinel/identify-threats-with-entity-behavior-analytics)
* Parâmetros do plugin KQL: nome do workspace do Microsoft Sentinel, ID da assinatura, nome do grupo de recursos e ID do locatário do Entra.

### Instruções
#### Carregar o plugin personalizado

### Pré-requisitos

-   [Security Copilot habilitado](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
-   [Acesso para carregar plugins personalizados](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)
-   [Workspace do Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-onboard) criado.
-   Parâmetros do plugin KQL: nome do workspace do Microsoft Sentinel, ID da assinatura, nome do grupo de recursos e ID do locatário do Entra.

### Instruções

#### Carregar o plugin personalizado

1.  Obtenha o arquivo HighBlastRadiusUserInvestigation.yaml deste diretório.
2.  Carregue o plugin personalizado.
3.  Na caixa de diálogo exibida no Security Copilot, insira Entra TentantId, SubscriptionId, ResourceGroupName e WorkspaceName específicos.