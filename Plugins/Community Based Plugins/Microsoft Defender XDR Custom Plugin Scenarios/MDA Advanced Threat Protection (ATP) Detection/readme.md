# Plugin do Copilot for Security: detecção do MDA Advanced Threat Protection (ATP)

### **Este plugin KQL permite que analistas e gerentes do SOC obtenham informações sobre possíveis malwares nos ambientes de aplicativos de nuvem com base nas tabelas CloudAppEvents do Defender for Cloud Apps e OfficeActivity do Sentinel.**

### Pré-requisitos

-   [Copilot for Security habilitado](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
-   [Acesso para carregar plugins personalizados](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)

### Instruções

#### Carregar o plugin personalizado

1.  Obtenha o arquivo MDA_Advanced_Threat_Protection_Detection.yaml deste diretório.
2.  Carregue o plugin personalizado.

### Uso do plugin

#### Habilidades

- **GetCloudAppATPEvents**: obtém uma lista de eventos do Advanced Threat Protection em um período especificado.
- **GetOfficeActivityATPEvents**: obtém uma lista de eventos do Advanced Threat Protection em um período especificado.

#### Prompts de exemplo

- Obtenha uma lista de eventos de malware do Advanced Threat Protection nos aplicativos de nuvem nas últimas 24 horas.
- Obtenha uma lista de eventos de malware do Advanced Threat Protection na atividade do Office nos últimos 30 dias.
- Liste os eventos de malware do ATP nos aplicativos de nuvem nas últimas 24 horas.
- Obtenha uma lista de eventos de malware do ATP na atividade do Office nos últimos 30 dias.

#### Exemplo de uso

1. Um gerente do SOC está preparando um relatório para a alta liderança sobre o impacto de malwares na organização.
2. A habilidade GetCloudAppATPEvents resume todos os arquivos colocados em quarentena nos últimos 30 dias.
3. O plugin Microsoft Defender Threat Intelligence (MDTI) é usado para obter o contexto das assinaturas e famílias de malware detectadas.
4. O plugin Generic é usado para resumir os prompts anteriores e recomendar controles adicionais que possam proteger contra as famílias de malware observadas.
