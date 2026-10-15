# Security Copilot-ThreatActor
Autor: Sean Wasonga
## Visão geral
Este playbook enfatiza a capacidade de criar perfis detalhados de agentes de ameaça, pesquisar artigos e CVEs relacionados a ameaças e realizar uma busca abrangente em todo o ambiente. Aproveitando a integração do Security Copilot com o Microsoft Defender Threat Intelligence (MDTI), os usuários podem coletar com eficiência inteligência sobre agentes de ameaça, artigos relacionados e CVEs, ampliando a compreensão de possíveis ameaças. Além disso, o playbook facilita a investigação proativa ao resumir as descobertas das atividades de busca, permitindo que os usuários fortaleçam sua postura de segurança. À medida que este playbook básico evoluir, ele deverá aprimorar ainda mais os recursos de coleta e investigação de inteligência contra ameaças.

## Instruções de pré-implantação

Antes de iniciar o processo de instalação, confirme que você atende aos seguintes pré-requisitos:
- O usuário que implantará este Logic App precisa ter a função Contributor.
- A licença do Security Copilot está habilitada em seu locatário.
- O usuário autenticado na ação do Logic App do Copilot tem permissão para acessar o ambiente do M365 Defender.
- O usuário autenticado na ação do Logic App do Copilot tem permissão para enviar emails.

Defina o endereço de email para o qual o Logic App diário deverá enviar as mensagens.

## Implantação

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FSecurity-Copilot%2Fmain%2FLogic%2520Apps%2FThreatactorCopilot%2Fazuredeploy.json" target="_blank">
  <img src="https://aka.ms/deploytoazurebutton"/>
</a>


### Instruções pós-implantação

1. Selecione a frequência com que o Logic App deverá ser executado.
2. Autentique os prompts do Copilot com um usuário que tenha acesso ao Security Copilot.
3. Defina o agente de ameaça que deseja usar no playbook. Por exemplo, este playbook vem predefinido com APT 28.
3. Execute o Logic App e aguarde os resultados.


Resultados do Logic App
![Agente de ameaça](https://github.com/KwachSean/SecurityCopilot/raw/main/playbooks/ThreatactorCopilot/threatactor.png)
