# Plugin personalizado do Security Copilot — KQL do ADX — Obter logs de entrada do Entra no Azure Data Explorer

#### Plugin do Security Copilot para obter logs de entrada do Entra ID em um cluster do Azure Data Explorer.

### Pré-requisitos

* [Security Copilot habilitado](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
* [Acesso para carregar plugins personalizados](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)
* [Um cluster do Azure Data Explorer](https://techcommunity.microsoft.com/t5/microsoft-sentinel-blog/using-azure-data-explorer-for-long-term-retention-of-microsoft/ba-p/1883947) com logs de entrada do Entra ID exportados da tabela Signinlogs do Sentinel para o ADX.

### Instruções
#### Carregar o plugin personalizado

1. Obtenha o arquivo [KQL-ADX-SignInLogs.yaml](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Sentinel%20Custom%20Plugin%20Scenarios/HuntSignInLogs-ADX/KQL-ADX-SignInLogs.yaml) deste diretório.
2. Modifique o arquivo .yaml e especifique os parâmetros *ADX Cluster URL*, *ADX Database* e *Entra TenantId*.
  
3. [Carregue o plugin personalizado](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#add-custom-plugins) e verifique se ele está ativado.

![CopilotForSecurity](https://learn.microsoft.com/en-us/security-copilot/media/add-plugin-button.png)

### Uso do plugin

A seguir estão algumas consultas de exemplo que você pode usar para acionar este plugin. Você pode combinar os parâmetros UPN e endereço IP ou usar apenas um deles, mas sempre inclua um intervalo de data e hora.

 * Descreva em detalhes, em alguns parágrafos, os resultados dos logs de entrada de user@contoso.com no armazenamento de arquivo de longo prazo do ADX entre 23 e 27 de outubro de 2023.
* Descreva em detalhes, em alguns parágrafos, os resultados dos logs de entrada do IP 165.87.34.123 no armazenamento de arquivo de longo prazo do ADX nos últimos 30 dias.
 * Descreva em detalhes as entradas de user@contoso.com cujo estado do Acesso Condicional foi uma falha no armazenamento de arquivo de longo prazo do ADX durante dezembro de 2023. Inclua os carimbos de data/hora das atividades de entrada.
<br>

![ADX](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Images/adx-masked.png)
