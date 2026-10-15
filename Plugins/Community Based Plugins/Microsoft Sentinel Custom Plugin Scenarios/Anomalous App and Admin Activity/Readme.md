# Plugin KQL personalizado do Security Copilot — Detectar atividades anômalas de aplicativos e usuários usando insights da UEBA do Microsoft Sentinel

#### Plugin do Security Copilot que usa dados dos insights da UEBA do Microsoft Sentinel, concentrando-se em anomalias relacionadas a aplicativos e à atividade de usuários administrativos. Para obter detalhes, consulte esta publicação:
 [link](https://techcommunity.microsoft.com/t5/microsoft-security-copilot-blog/harnessing-the-power-of-kql-plugins-for-enhanced-security/ba-p/4221891)

### Pré-requisitos

* [Security Copilot habilitado](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
* [Acesso para carregar plugins personalizados](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)
* [Workspace do Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-onboard) criado.
* [UEBA do Microsoft Sentinel habilitada](https://learn.microsoft.com/en-us/azure/sentinel/identify-threats-with-entity-behavior-analytics)
* Parâmetros do plugin KQL: nome do workspace do Microsoft Sentinel, ID da assinatura, nome do grupo de recursos e ID do locatário do Entra.

### Instruções
#### Carregar o plugin personalizado

1. Obtenha o arquivo [AnomalousAppandUserActivity.yaml](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Sentinel%20Custom%20Plugin%20Scenarios/Anomalous%20App%20and%20Admin%20Activity/AnomalousAppandAdminActivity.yaml) deste diretório.
2. Modifique a consulta KQL conforme necessário para atender aos seus requisitos. Uma possível alteração é o fuso horário convertido nesta linha:  | where datetime_utc_to_local(TimeGenerated, "US/Eastern") between ( fromDateTime .. toDateTime ).


3. [Carregue o plugin personalizado](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#add-custom-plugins) e, na caixa de diálogo exibida, insira o ID do locatário, o ID da assinatura, o nome do workspace e o grupo de recursos que hospeda o workspace do Sentinel. Verifique se o plugin está ativado.

![Copilot for Security](https://learn.microsoft.com/en-us/security-copilot/media/add-plugin-button.png)


4. [Insira os detalhes do workspace na interface do Security Copilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/KQL Plugin images/Workspacedetails.png)


