# Copilot-For-Security-DailyThreatExposureReport 
## Visão geral

Este playbook usa os recursos da habilidade Microsoft Defender Threat Intelligence para verificar proativamente as ameaças direcionadas à sua organização. Ele resume detalhadamente as vulnerabilidades identificadas e, além disso, envia informações práticas diretamente para sua caixa de entrada por email, permitindo que você tome medidas rápidas e fundamentadas.

## Instruções de pré-implantação

Antes de iniciar o processo de instalação, confirme que você atende aos seguintes pré-requisitos:
- O usuário que implantará este Logic App precisa ter a função Contributor.
- A licença do Security Copilot está habilitada em seu locatário.
- O usuário autenticado na ação do Logic App do Copilot tem permissão para enviar emails.
- Defina o endereço de email para o qual o Logic App diário deverá enviar as mensagens.

## Implantação

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FSecurity-Copilot%2Fmain%2FLogic%2520Apps%2FDailyThreatExposureReport-Copilot%2Fazuredeploy.json"
 target="_blank">
    <img src="https://aka.ms/deploytoazurebutton"/>
</a>


### Instruções pós-implantação

1. Selecione a frequência com que o Logic App deverá ser executado.
2. Autentique os prompts do Copilot com um usuário que tenha acesso ao Security Copilot.
3. Execute o Logic App e aguarde os resultados.


**Exibição do Logic App**

![Exposição diária a ameaças](https://github.com/Azure/Copilot-For-Security/blob/main/Images/Logicapp%20images/Dailythreatexposure.png)

**Resultados do Logic App**

![Exposição diária a ameaças 2](https://github.com/Azure/Copilot-For-Security/blob/main/Images/Logicapp%20images/Dailythreatexposure2.png)
