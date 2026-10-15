# Análise de caminhos de ataque com o Defender CSPM no Defender for Cloud (plugin personalizado para o Security Copilot)

A habilidade deste plugin personalizado permite obter a lista de "Attack Paths" identificados pelo recurso Defender CSPM (Cloud Security Posture Management) do Microsoft Defender for Cloud nos ambientes de nuvem protegidos do Azure, AWS e GCP.


### Pré-requisitos:
* Defender CSPM com Attack Paths habilitado no Defender for Cloud (https://learn.microsoft.com/en-us/azure/defender-for-cloud/how-to-manage-attack-path)
* Continuous Export habilitado no Defender for Cloud (https://learn.microsoft.com/en-us/azure/defender-for-cloud/continuous-export)


### Instruções:
1. Baixe o arquivo YAML desta pasta. Salve-o localmente em seu computador e abra-o para editar o conteúdo.
2. Defina os valores destes parâmetros:
    * TenantId: [Insira o ID do locatário]
    * SubscriptionId: [Insira o ID da assinatura]
    * ResourceGroupName: [Insira o nome do grupo de recursos]
    * WorkspaceName: [Insira o nome do workspace do Log Analytics ou do Sentinel]
3. Adicione o plugin carregando o YAML no Security Copilot (https://learn.microsoft.com/en-us/copilot/security/manage-plugins?tabs=securitycopilotplugin)


### Referências adicionais:
* [Como operacionalizar insights de caminhos de ataque](https://techcommunity.microsoft.com/t5/microsoft-defender-for-cloud/operationalizing-attack-path-insights/ba-p/4121643), por Giulio Astori
* [Compartilhando minhas primeiras experiências na criação de plugins KQL personalizados para o Security Copilot](https://www.linkedin.com/feed/update/urn:li:activity:7199175292278505472/), minha publicação sobre como este plugin foi projetado e desenvolvido
