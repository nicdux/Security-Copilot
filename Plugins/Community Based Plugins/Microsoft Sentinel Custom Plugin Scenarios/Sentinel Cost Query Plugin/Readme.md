# Plugin personalizado do Security Copilot — KQL do Sentinel — Custos do Sentinel

#### Plugin do Security Copilot para executar uma consulta KQL dinâmica e estimar os custos do Microsoft Sentinel em um intervalo específico de data e hora consultando a tabela Usage no Microsoft Sentinel.

### Pré-requisitos

* [Security Copilot habilitado](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
* [Acesso para carregar plugins personalizados](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)
* [Workspace do Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-onboard) criado.
* Parâmetros do plugin KQL: nome do workspace do Microsoft Sentinel, ID da assinatura, nome do grupo de recursos e ID do locatário do Entra.

### Instruções
#### Carregar o plugin personalizado

1. Obtenha o arquivo [KQL-Sentinel-SentinelCost.yaml](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Sentinel%20Custom%20Plugin%20Scenarios/Sentinel%20Cost%20Query%20Plugin/KQL-SentinelCost.yaml) deste diretório.
2. Modifique o arquivo yaml para especificar Entra TentantId, SubscriptionId, ResourceGroupName e WorkspaceName de sua instância do Sentinel. Você também pode modificar a consulta KQL no final do plugin para ajustar sua tarifa específica em dólares por GB de ingestão de dados do Sentinel (size * 4.3).



3. [Carregue o plugin personalizado](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#add-custom-plugins) e verifique se ele está ativado.

![CopilotForSecurity](https://learn.microsoft.com/en-us/security-copilot/media/add-plugin-button.png)

### Uso do plugin

A seguir estão algumas consultas de exemplo que você pode usar para acionar este plugin. Sempre inclua um intervalo de data e hora.

* Verifique quais foram meus custos do Sentinel nos últimos sete dias.
* Forneça um resumo dos meus custos totais do Sentinel entre 1º e 15 de março de 2024.
* Forneça um resumo detalhado dos meus custos totais do Sentinel nos últimos 90 dias. Explique a finalidade de cada tabela no Sentinel e o valor de segurança que ela oferece. Some todos os custos para fornecer uma média mensal e apresente recomendações de economia com base na minha ingestão de dados.

![Logs do O365](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Images/sentinel-cost.png)
![Logs do O365](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Images/sentinel-cost-2%20.png)
