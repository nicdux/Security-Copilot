# Security Copilot-isUserTravel
Autor: Yaniv Shasha





Ativar o botão 'Deploy' inicia a implantação de um Azure Logic App integrado às ações do Security Copilot, usando um gatilho de incidente do Microsoft Sentinel.
O Logic App é configurado para ser executado quando um novo incidente é criado no Sentinel. Este Logic App funciona melhor com os seguintes tipos de incidente:<br>

- **Comportamento suspeito: atividade de país ou região incomum** </br>
- **Comportamento suspeito: atividade de viagem impossível** </br>

Depois que o Copilot realiza uma investigação, ele identifica o gestor do usuário (na tabela UEBA do Sentinel) e envia um email perguntando sobre a situação de viagem do usuário. Se o gestor responder "sim", é provável que se trate de um falso positivo. Nesse caso, o Copilot adiciona a resposta do gestor ao contexto e redige um relatório que a inclui.</br>
Se o gestor responder que o usuário não está viajando, a investigação prossegue com foco nos prompts de identidade.</br>



### Pré-requisitos

Antes de iniciar o processo de instalação, confirme que você atende aos seguintes pré-requisitos: <br>
• O usuário que implantará este Logic App precisa ter a função Contributor.<br>
• A licença do Security Copilot está habilitada em seu locatário. <br>
• O usuário autenticado na ação do Logic App do Copilot tem permissão para enviar emails.<br>


<br>

• Este Logic App pode ser executado manual ou automaticamente. Se você escolher a execução automática, precisará criar uma nova regra de automação no Sentinel e configurar este Logic App como uma ação.<br>


<br>

### Implantação

Para implantar o Logic App acima:<br>
•   Selecione a opção Deploy, sua assinatura e o grupo de recursos (escolha o mesmo locatário em que o Security Copilot está habilitado).<br>

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FSecurity-Copilot%2Fmain%2FLogic%2520Apps%2FCopilot-isUserTravel%2Fazuredeploy.json" target="_blank">
    <img src="https://aka.ms/deploytoazurebutton"/>
</a>



<br>

### Pós-implantação

•   Autentique-se com os usuários mencionados acima (você pode usar usuários diferentes para as ações do Copilot e do Sentinel).<br>
•   Para executar o Logic App manualmente, abra a página de incidentes do Microsoft Sentinel, clique com o botão direito em um incidente específico e selecione Run playbook; depois, selecione o Logic App recém-implantado e escolha Run.<br>
•   Para executar o Logic App automaticamente, crie uma regra de automação no Sentinel e conecte este playbook como ação da regra.<br>



<img src="./images/designer.png"/>

#### Exemplo de pergunta por email

</br>
<img src="./images/email.png"/>

</br>
