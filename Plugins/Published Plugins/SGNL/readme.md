# SGNL Access Intelligence
**Autor: Marc Jordan**
**Publicador: SGNL**

Este plugin permite que administradores da SGNL usem o Microsoft Security Copilot para compreender e identificar decisões e tendências de acesso detalhadas em toda a organização.

[Blog técnico](https://sgnl.ai/2023/11/sgnl-for-microsoft-security-copilot/)

**Observação**
Antes de continuar, verifique se sua conta tem permissão suficiente para ler os SGNL Access Decision Logs.

## **Pré-requisitos**
1. Autentique-se na SGNL (pelo Console ou pela API) e obtenha seu Tenant ID (Admin-->Environment) e seu ID Token. Esses dados serão necessários para configurar o Security Copilot.


## Selecione ou carregue o arquivo de manifesto anexado no console do Security Copilot
1. No gerenciador de plugins, localize o plugin SGNL e habilite-o.
![Habilitar plugin](images/plugin-manager.png)
  

2. Ao configurar o plugin, use seu Tenant ID como Username e seu ID Token como senha, por exemplo:
	```
	Username: 4b1...
    Password: eyJ......
	```
    ![Configurar plugin](images/config.png)
3. Salve a configuração.


## Habilidades e prompts
1. Habilidade 1: informe sobre acessos da SGNL.
- Exemplos de prompt: Resuma os logs da SGNL de hoje; Quais entidades de segurança acessaram ativos confidenciais hoje; Informe sobre os acessos de [Principal] nos últimos 7 dias; Quais entidades de segurança acessaram [Asset]
- Entradas: [Principal], [Asset], [Action]


## Perguntas frequentes (FAQ)
1. **Importante**
   Se os prompts não funcionarem, verifique se você está usando um dos prompts compatíveis acima. Caso contrário, use a invocação direta de habilidade "/".
