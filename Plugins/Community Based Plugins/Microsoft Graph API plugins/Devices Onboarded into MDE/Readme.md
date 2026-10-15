# Plugin para obter dispositivos integrados ao Microsoft Defender for Endpoint (MDE)

## Visão geral
Este plugin permite obter uma lista de dispositivos integrados ao **Microsoft Defender for Endpoint (MDE)** usando a **Microsoft Graph API**. Ele fornece informações valiosas sobre os dispositivos, o estado de conformidade, os níveis de risco e outros dados, facilitando o monitoramento de segurança e a resposta a incidentes.

## Recursos
- Obtém detalhes dos dispositivos, incluindo **nome, sistema operacional, fabricante, modelo, número de série e endereço MAC**.
- Identifica o **estado de conformidade** e o **nível de risco** dos dispositivos integrados.
- Obtém dispositivos com base na **data da última observação**.
- Permite filtrar dispositivos pelo **estado de ingresso no Azure AD, estado de conformidade e plataforma do sistema operacional**.

## Ponto de extremidade da API
**Base URL:** `https://graph.microsoft.com/v1.0`


### Instruções de configuração
#### Carregar o manifesto do plugin

1. Obtenha neste diretório os arquivos de manifesto [MDEOnboardedDevicesPlugin.yaml](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Graph%20API%20/Devices%20Onboarded%20into%20MDE/MDEOnboardedDevicesPlugin.yaml) e de especificação OpenAPI [MDEOnboardedDevices-OpenAPISpec.yaml](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Graph%20API%20/Devices%20Onboarded%20into%20MDE/MDEOnboardedDevices-OpenAPISpec.yaml).
2. Baixe o arquivo de especificação e mova-o para o local de sua preferência, garantindo que ele esteja acessível ao Security Copilot.


3. [Carregue o plugin personalizado](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#add-custom-plugins).

## Exemplos de consultas em linguagem natural
Use estes prompts de exemplo para obter dados relevantes pelo **Security Copilot**:
- "Obtenha os dispositivos integrados ao MDE cujo estado de conformidade seja 'Non-compliant'."
- "Obtenha a lista de dispositivos não conformes entre os dispositivos integrados ao MDE."
- "Obtenha uma lista de dispositivos integrados ao MDE cujo nível de risco seja 'High'."
- "Obtenha no MDE os dispositivos registrados há menos de 14 dias a partir de hoje."
- "Obtenha uma lista de pontos de extremidade do MDE cuja última observação ocorreu há menos de um dia."
- "Obtenha no MDE os dispositivos que usam o sistema operacional iOS."


---
Para obter mais detalhes, consulte a **[documentação da Microsoft Graph API](https://learn.microsoft.com/en-us/graph/)**.
