# Sec-Copilot-UserReportedPhishing
Autor: Yaniv Shasha




Ao iniciar o processo de implantação, você configurará um Azure Logic App integrado às ações do Security Copilot.<br>
Essa configuração é ativada quando um usuário relata uma tentativa de phishing no Outlook.<br>
Conforme configurado pelo Defender for Office, esses emails relatados são redirecionados para uma caixa de correio compartilhada designada.<br>
Cada novo email que chega a essa caixa de correio compartilhada aciona a automação do Security Copilot e inicia um processo de investigação automatizado.<br>
Durante essa fase, o Security Copilot examina o email para determinar a probabilidade de ser uma tentativa de phishing.<br>
Dependendo do nível de risco avaliado, o sistema envia um email de notificação.<br>
Além disso, se a probabilidade de phishing for superior a 75%, um incidente do Sentinel será gerado automaticamente.<br>


### Antes de iniciar a instalação, verifique se você atende a estes pré-requisitos:

• O usuário que implanta este Logic App deve ter a função Contributor.<br>
• A licença do Security Copilot deve estar habilitada em seu locatário.<br>
• O usuário autenticado na ação do Logic App do Copilot deve ter permissões de Security Admin e a função Microsoft Sentinel Contributor, necessárias para criar comentários em incidentes.<br>
• Carregue e habilite o plugin KQL personalizado no mesmo perfil de usuário que executa a automação. <br>

<img src="./images/upload01.png"/>

<img src="./images/enable_skill.png"/>

 
<br>

<br>





### Implantação

Para implantar o Logic App acima:<br>
•   Selecione a opção Deploy, sua assinatura e o grupo de recursos (escolha o mesmo locatário em que o Security Copilot está habilitado).<br>


<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FSecurity-Copilot%2Fmain%2FLogic%2520Apps%2FSecCopilot-UserReportedPhishing%2Fazuredeploy.json" target="_blank">
<img src="https://aka.ms/deploytoazurebutton"/>



### Exibição completa do Logic App

<img src="./images/full_view.png"/>