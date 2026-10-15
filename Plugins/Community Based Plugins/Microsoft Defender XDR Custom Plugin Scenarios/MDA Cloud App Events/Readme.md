# Plugin do Copilot for Security: MDA Cloud App Events

### Este plugin KQL permite que analistas do SOC investiguem eventos relacionados a contas e objetos no Office 365 e em outros aplicativos e serviços de nuvem usando dados do Defender for Cloud Apps provenientes da tabela CloudAppEvents.

A tabela CloudAppEvents contém logs enriquecidos de todos os aplicativos SaaS conectados ao MDA, incluindo aplicativos do Office 365, como:
- OneDrive
- SharePoint
- Exchange Online
- Teams

### Pré-requisitos

-   [Copilot for Security habilitado](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
-   [Acesso para carregar plugins personalizados](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)

### Instruções

#### Carregar o plugin personalizado

1.  Obtenha o arquivo MDA_Cloud_App_Events.yaml deste diretório.
2.  Carregue o plugin personalizado.

### Uso do plugin

#### Habilidades

- **GetOneDriveActivtyForUser**: obtém uma lista da atividade de um usuário no OneDrive em um período especificado.
- **GetSharePointActivityForUser**: obtém uma lista da atividade de um usuário no SharePoint em um período especificado.
- **GetExchangeOnlineActivityForUser**: obtém uma lista da atividade de um usuário no Exchange Online em um período especificado.
- **GetTeamsActivityForUser**: obtém uma lista da atividade de um usuário no Teams em um período especificado.

#### Prompts de exemplo

- Obtenha uma lista da atividade de someone@example.com no OneDrive nas últimas duas horas.
- Obtenha uma lista da atividade de someone@example.com no SharePoint no último dia.
- Liste toda a atividade de someone@example.com no Exchange Online nas últimas duas horas.
- Obtenha uma lista da atividade de someone@example.com no Teams no último dia.

#### Exemplo de uso

1. Um analista do SOC está investigando um alerta do Purview Insider Risk Management.
2. A habilidade GetOneDriveActivtyForUser é usada para obter um resumo da atividade do usuário uma hora antes do alerta.
3. A habilidade GetTeamsActivityForUser é usada para identificar se o usuário compartilhou algum conteúdo pelo Teams.
4. O plugin Entra ID é usado para resumir o nível de risco do usuário.
