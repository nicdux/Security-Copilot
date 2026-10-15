# Plugin do Security Copilot: problemas de ingestão de tabelas do Sentinel

### **Esta consulta procura processos raramente observados que são iniciados como serviço em um ponto de extremidade protegido pelo MDE. Modifique a consulta para adicionar à lista de permissões os processos esperados em seu ambiente.**

### Pré-requisitos

-   [Security Copilot habilitado](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
-   [Acesso para carregar plugins personalizados](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)
-   [Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender)

-   O plugin usa as permissões do usuário que o configura.

### Instruções

#### Carregar o plugin personalizado

1.  Obtenha o arquivo RareProcessAsAService.yaml deste diretório.
