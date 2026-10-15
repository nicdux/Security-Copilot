# Plugin personalizado do Security Copilot — KQL — Avaliação de agentes de servidor com o Defender Vulnerability Management

A habilidade deste plugin personalizado obtém as versões dos componentes de software Arc, AMA, MMA e MDE em execução nos servidores Windows e Linux. A obtenção é feita por uma consulta KQL ao recurso Advanced Hunting do Defender XDR usando os dados de inventário dos servidores coletados pelo Microsoft Defender Vulnerability Management.

### Siglas:
* Arc -> Azure Arc
* AMA -> Azure Monitoring Agent
* MMA -> Microsoft Monitoring Agent
* MDE -> Microsoft Defender for Endpoint
* MDVM -> Microsoft Defender Vulnerability Management
* XDR -> eXtended Detection and Response


### Referências das versões desses componentes:
* MMA for Windows Server: https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/oms-windows#agent-and-vm-extension-version
* MMA for Linux: https://learn.microsoft.com/en-us/azure/virtual-machines/extensions/oms-linux
* AMA for Windows Server  and Linux: https://learn.microsoft.com/en-us/azure/azure-monitor/agents/azure-monitor-agent-extension-versions
* MDE for Windows Server: https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/windows-whatsnew?view=o365-worldwide
* MDE for Linux: https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/linux-whatsnew?view=o365-worldwide
* Arc for Windows Server and Linux: https://learn.microsoft.com/en-us/azure/azure-arc/servers/agent-release-notes


### Pré-requisitos:
* Microsoft Defender for Endpoint (MDE) ou Microsoft Defender Vulnerability Management (MDVM) em execução nesses servidores (o inventário de software é realizado pelo MDVM).


### Limitações:
Atualmente, a habilidade não consegue obter a versão do agente AMA em execução nos servidores Windows.


### Instruções:
1. Baixe o arquivo YAML desta pasta. Salve-o localmente em seu computador e abra-o para editar o conteúdo.
2. Adicione o plugin carregando o YAML no Security Copilot (https://learn.microsoft.com/en-us/copilot/security/manage-plugins?tabs=securitycopilotplugin)
