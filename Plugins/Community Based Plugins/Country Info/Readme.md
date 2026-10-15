# Plugin do Security Copilot: informações sobre países

### **Este plugin obtém informações sobre países usando um banco de dados disponível publicamente.**

### Pré-requisitos

-   [Security Copilot habilitado](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
-   [Acesso para carregar plugins personalizados](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)
-   [Workspace do Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-onboard) criado.
-   Parâmetros do plugin KQL: nome do workspace do Microsoft Sentinel, ID da assinatura, nome do grupo de recursos e ID do locatário do Entra.

### Instruções

#### Carregar o plugin personalizado

1.  Obtenha o arquivo KQL_Plugin_country_info.yaml deste diretório.
2.  Modifique o arquivo yaml para especificar Entra TentantId, SubscriptionId, ResourceGroupName e WorkspaceName de sua instância do Sentinel.
3.  Carregue o plugin personalizado.

Para obter mais informações, consulte: [Plugin do Security Copilot: informações sobre países](https://rodtrent.substack.com/p/copilot-for-security-plugin-country)
