# Plugin personalizado do Security Copilot para acompanhar alterações de SCU

## Conheça as alterações de SCU diretamente no Security Copilot.

### Pré-requisitos

-   [Security Copilot habilitado](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
-   [Acesso para carregar plugins personalizados](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)
-   [Workspace do Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-onboard) criado.
-   Parâmetros do plugin KQL: nome do workspace do Microsoft Sentinel, ID da assinatura, nome do grupo de recursos e ID do locatário do Entra.

### Instruções

#### Carregar o plugin personalizado

1.  Obtenha o arquivo KQL_Plugin_SCU_Changes.yaml deste diretório.
2.  Modifique o arquivo yaml para especificar Entra TentantId, SubscriptionId, ResourceGroupName e WorkspaceName de sua instância do Sentinel.
3.  Carregue o plugin personalizado.

Para obter mais informações, consulte: [Plugin personalizado do Security Copilot para acompanhar alterações de SCU](https://rodtrent.substack.com/p/copilot-for-security-custom-plugin)
