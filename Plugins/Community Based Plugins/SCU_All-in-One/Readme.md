# Plugin do Security Copilot: SCU All-in-One

### **Este plugin reúne plugins anteriores em uma única solução completa para capturar e responder com a atividade do Security Copilot. Ele será atualizado à medida que novas atividades de monitoramento forem disponibilizadas e identificadas.**

### Pré-requisitos

-   [Security Copilot habilitado](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
-   [Acesso para carregar plugins personalizados](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)
-   [Workspace do Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-onboard) criado.
-   Parâmetros do plugin KQL: nome do workspace do Microsoft Sentinel, ID da assinatura, nome do grupo de recursos e ID do locatário do Entra.

### Instruções

#### Carregar o plugin personalizado

1.  Obtenha o arquivo SCU_All-in-One.yaml deste diretório.
2.  Modifique o arquivo yaml para especificar Entra TentantId, SubscriptionId, ResourceGroupName e WorkspaceName de sua instância do Sentinel.
3.  Carregue o plugin personalizado.

Para obter mais informações, consulte: [Plugin personalizado completo de atividades do Security Copilot](https://rodtrent.substack.com/p/copilot-for-security-activity-all)
