# Copilot-For-Security-Investigate-FailedSignins
Autor: Sean Wasonga
## Visão geral
Este playbook é um componente fundamental de nossas operações de segurança, dedicado a identificar usuários com várias tentativas de entrada com falha e a realizar investigações detalhadas dos endereços IP associados usando fontes de inteligência contra ameaças. Além disso, analisa minuciosamente diversos fatores de risco vinculados ao usuário, incluindo o status de associação a grupos, a conformidade do dispositivo e outras questões pertinentes.

## Instruções de pré-implantação

Antes de iniciar o processo de instalação, confirme que você atende aos seguintes pré-requisitos:
1. O usuário que implantará este Logic App precisa ter a função Contributor.
2. A licença do Security Copilot está habilitada em seu locatário.
3. O usuário autenticado na ação do Logic App do Copilot tem permissão para enviar emails.
4. Defina o endereço de email para o qual o Logic App diário deverá enviar as mensagens.

## Implantação


<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FSecurity-Copilot%2Fmain%2FLogic%2520Apps%2FInvestigateFailedSignins%2Fazuredeploy.json" target="_blank">
    <img src="https://aka.ms/deploytoazurebutton"/>
</a>


### Instruções pós-implantação

1. Selecione a frequência com que o Logic App deverá ser executado.
2. Autentique os prompts do Copilot com um usuário que tenha acesso ao Security Copilot.
3. Execute o Logic App e aguarde os resultados.


![Investigar tentativas de entrada com falha](https://github.com/Azure/Copilot-For-Security/blob/main/Logic%20Apps/InvestigateFailedSignins/investigatefailedsignins.png)
