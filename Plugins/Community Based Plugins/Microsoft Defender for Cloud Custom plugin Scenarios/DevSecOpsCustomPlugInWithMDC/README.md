# Plugin personalizado do Security Copilot — KQL — DevSecOps com o Defender for Cloud (baseado no GhAS e no GAzDO)

Este plugin personalizado contém duas habilidades:
* A primeira habilidade (GetNewDevSecOpsAlertsInTheLastTimespan) retorna a lista de novos alertas relacionados ao DevSecOps e gerados em um período anterior definido pelo usuário em relação ao carimbo de data/hora atual. O usuário deve especificar o intervalo a considerar (por exemplo, 1d para um dia, 4h para quatro horas etc.). Somente novos alertas são exibidos: se um alerta for repetido, mas já tiver sido disparado com informações idênticas antes do intervalo considerado, ele não será retornado.
* A segunda habilidade (GetDevSecOpsAlertsInTheLastTimespan) retorna a lista de todos os alertas exclusivos relacionados ao DevSecOps e gerados em um período anterior definido pelo usuário em relação ao carimbo de data/hora atual. O usuário deve especificar o intervalo a considerar (por exemplo, 1d para um dia, 4h para quatro horas etc.). Todos os alertas são considerados, mas cada um é listado apenas uma vez, incluindo todos os detalhes (nome do alerta, recursos de destino etc.). Para cada alerta exclusivo, a consulta também retorna o carimbo de data/hora da primeira e da última ocorrência dentro do intervalo considerado, bem como o número de ocorrências.

### Pré-requisitos:
* DevOps Security habilitado no Defender for Cloud (https://learn.microsoft.com/en-us/azure/defender-for-cloud/devops-support)
* Continuous Export habilitado no Defender for Cloud (https://learn.microsoft.com/en-us/azure/defender-for-cloud/continuous-export)

### Observações:
* Os alertas de DevSecOps retornados por essas habilidades são produzidos por Code Scanning (SAST por meio do CodeQL), Dependency Scanning (SCA), Secrets Scanning e Infrastructure as Code (IaC) Scanning. Code Scanning, Dependency Scanning e Secrets Scanning são disponibilizados pelo GitHub Advanced Security (GhAS) no GitHub e pelo GitHub Advanced Security for Azure DevOps (GAzDO) no Azure DevOps. O Infrastructure as Code (IaC) Scanning é disponibilizado ao habilitar o recurso DevOps Security do Defender for Cloud (Defender CSPM) no GitHub ou no Azure DevOps.
* O DevOps Security no Defender for Cloud também é compatível com ambientes do GitLab Enterprise, mas o KQL deste plugin não oferece suporte a essa fonte.


### Instruções:
1. Baixe o arquivo YAML desta pasta. Salve-o localmente em seu computador e abra-o para editar o conteúdo.
2. Defina os valores destes parâmetros:
    * TenantId: [Insira o ID do locatário]
    * SubscriptionId: [Insira o ID da assinatura]
    * ResourceGroupName: [Insira o nome do grupo de recursos]
    * WorkspaceName: [Insira o nome do workspace do Log Analytics ou do Sentinel]
   Observação: esses parâmetros devem ser definidos nas duas habilidades especificadas no arquivo YAML.
3. Adicione o plugin carregando o YAML personalizado no Security Copilot (https://learn.microsoft.com/en-us/copilot/security/manage-plugins?tabs=securitycopilotplugin)
