# Plugin do Security Copilot: uso do Security Copilot com plugins KQL baseados no ASIM em cenários de investigação

### **Obtenha informações do Microsoft Sentinel usando consultas independentes de fonte baseadas no ASIM — Advanced Security Information Model**

### Pré-requisitos

-   [Security Copilot habilitado](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
-   [Acesso para carregar plugins personalizados](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)
-   [Workspace do Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-onboard) criado.
-   Parâmetros do plugin KQL: nome do workspace do Microsoft Sentinel, ID da assinatura, nome do grupo de recursos e ID do locatário do Entra.

### Instruções

#### Carregar o plugin personalizado

1.  Obtenha o arquivo PotentialNetworkBeaconingActivity.yaml deste diretório.
2.  Carregue o plugin personalizado.
3.  Na caixa de diálogo exibida no Security Copilot, insira Entra TentantId, SubscriptionId, ResourceGroupName e WorkspaceName específicos.

### Link para a publicação

Consulte a publicação neste [link](https://techcommunity.microsoft.com/blog/securitycopilotblog/leveraging-asim-based-kql-plugins-in-microsoft-security-copilot-for-investigatio/4357680).
