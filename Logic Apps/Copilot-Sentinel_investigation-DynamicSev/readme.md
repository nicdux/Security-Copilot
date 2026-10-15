# Security-Copilot-Sentinelinvestigation-DynamicSev
Autor: Yaniv Shasha





Ativar o botão 'Deploy' inicia a implantação de um Azure Logic App integrado às ações do Security Copilot, que usa um gatilho de incidente do Microsoft Sentinel. <br>
Este Logic App altera o status do incidente para ativo, gera marcas dinâmicas (rótulos) e as adiciona às marcas do incidente do Sentinel.  <br>
Além disso, a automação determina e ajusta a gravidade do incidente com base no enriquecimento do MDTI.  <br>
Ela também documenta de forma abrangente as descobertas da investigação e a lógica da classificação na seção de comentários do incidente do Sentinel. <br>


### Pré-requisitos

Antes de iniciar o processo de instalação, confirme que você atende aos seguintes pré-requisitos: <br>
• O usuário que implantará este Logic App precisa ter a função Contributor.<br>
• A licença do Security Copilot está habilitada em seu locatário. <br>
• O usuário autenticado na ação do Logic App do Copilot precisa ter a permissão Security Admin e a função Microsoft Sentinel Contributor, pois é necessário criar comentários no incidente.<br>

<img src="https://github.com/Yaniv-Shasha/SecurityCopilot/blob/00853308e8949cc7279640aa9743759f586bb190/Playbooks/Copilot-Sentinel_investigation-DynamicSev/images/copilot_auth.jpg"/>

<br>

<img src="https://github.com/Yaniv-Shasha/SecurityCopilot/blob/00853308e8949cc7279640aa9743759f586bb190/Playbooks/Copilot-Sentinel_investigation-DynamicSev/images/Sentinel_auth.jpg"/>

<br>

• Este Logic App pode ser executado manual ou automaticamente. Se você escolher a execução automática, precisará criar uma nova regra de automação no Sentinel e configurar este Logic App como uma ação.<br>


<br>

### Implantação

Para implantar o Logic App acima:<br>
•   Selecione a opção Deploy, sua assinatura e o grupo de recursos (escolha o mesmo locatário em que o Security Copilot está habilitado).<br>

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FSecurity-Copilot%2Fmain%2FLogic%2520Apps%2FCopilot-Sentinel_investigation-DynamicSev%2Fazuredeploy.json" target="_blank">
<img src="https://aka.ms/deploytoazurebutton"/>
</a>
<br>

### Pós-implantação

•   Autentique-se com os usuários mencionados acima (você pode usar usuários diferentes para as ações do Copilot e do Sentinel).<br>
•   Para executar o Logic App manualmente, abra a página de incidentes do Microsoft Sentinel, clique com o botão direito em um incidente específico e selecione Run playbook; depois, selecione o Logic App recém-implantado e escolha Run.<br>
•   Para executar o Logic App automaticamente, crie uma regra de automação no Sentinel e conecte este playbook como ação da regra.<br>


<img src="https://github.com/Yaniv-Shasha/SecurityCopilot/blob/ccbd305c539800eea2a1f7c1a0905aff954e2e25/Playbooks/Copilot-Sentinel_investigation-DynamicSev/images/full_logic_app.jpg"/>
