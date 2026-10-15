# Security-Copilot-KQLMigrator
Autores: Hiten Sharma e Hesham Abdelaal
## Visão geral
Este playbook enfatiza a capacidade de converter e migrar consultas e regras personalizadas de SIEM e EDR/XDR para KQL.

## Instruções de pré-implantação

Antes de iniciar o processo de instalação, confirme que você atende aos seguintes pré-requisitos:
- O usuário que implantará este Logic App precisa ter a função Contributor.
- A licença do Security Copilot está habilitada em seu locatário.
- O usuário autenticado na ação do Logic App do Copilot tem permissão para acessar o ambiente do M365 Defender/Microsoft Sentinel.
- O usuário autenticado na ação do Logic App do Copilot tem permissão para criar e gerenciar regras de análise no Microsoft Sentinel.


## Implantação

 <a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FCopilot-For-Security%2Fmain%2FLogic%2520Apps%2FKQL-Migrator%2FKQLMigratorPlaybook-SecCopilot.json" target="_blank">
  <img src="https://aka.ms/deploytoazurebutton"/>
</a>

Suas configurações de ambiente.


### Instruções pós-implantação

1. Selecione a frequência com que o Logic App deverá ser executado.
2. Autentique os prompts do Copilot com um usuário que tenha acesso ao Security Copilot.
3. Carregue e defina o item da lista de observação do Microsoft Sentinel que deseja usar no playbook (há dois exemplos: um para consultas AQL e outro para regras YARA). Configure também o registro do aplicativo se quiser automatizar a criação de regras de análise do Microsoft Sentinel pelo playbook. Lembre-se de que talvez seja necessário editar o playbook do Logic App com as listas de observação necessárias.
3. Execute o Logic App e aguarde os resultados.


Resultados do Logic App
![KQLMigrator](https://github.com/Azure/Security-Copilot/blob/main/Logic%20Apps/KQL-Migrator/KQLMigratorPlaybook.png)
