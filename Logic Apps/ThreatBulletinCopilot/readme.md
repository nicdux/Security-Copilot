# Security Copilot-ThreatBulletin
Autor: Sean Wasonga
## Visão geral
Este playbook é um componente fundamental do Security Copilot, pois facilita a integração com o Microsoft Defender Threat Intelligence (MDTI) para fornecer rapidamente os boletins de ameaças mais recentes referentes a artigos sobre ameaças. Ao consolidar essa conexão, os usuários podem acessar com eficiência informações abrangentes desses artigos. Com o tempo, este playbook básico poderá ser ampliado para incorporar outros recursos.

## Instruções de pré-implantação

Antes de iniciar o processo de instalação, confirme que você atende aos seguintes pré-requisitos:
- O usuário que implantará este Logic App precisa ter a função Contributor.
- A licença do Security Copilot está habilitada em seu locatário.
- O usuário autenticado na ação do Logic App do Copilot tem permissão para enviar emails.
- Defina o endereço de email para o qual o Logic App diário deverá enviar as mensagens.

## Implantação

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FSecurity-Copilot%2Fmain%2FLogic%2520Apps%2FThreatBulletinCopilot%2Fazuredeploy.json" target="_blank">
    <img src="https://aka.ms/deploytoazurebutton"/>

</a>


### Instruções pós-implantação

1. Selecione a frequência com que o Logic App deverá ser executado.
2. Autentique os prompts do Copilot com um usuário que tenha acesso ao Security Copilot.
3. Execute o Logic App e aguarde os resultados.

Exibição do Logic App
![Logic App de boletim de ameaças](https://github.com/Azure/Copilot-For-Security/blob/main/Logic%20Apps/ThreatBulletinCopilot/threatbulletinlogicapp.png)

Resultados do Logic App
![Imagem do boletim de ameaças](https://github.com/Azure/Copilot-For-Security/blob/main/Logic%20Apps/ThreatBulletinCopilot/Threatbulletin.png)
