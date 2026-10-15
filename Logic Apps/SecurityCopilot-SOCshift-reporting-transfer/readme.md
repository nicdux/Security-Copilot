# SecurityCopilot-SOCshift-reporting-transfer
Autor: Yaniv Shasha





Ativar o botão 'Deploy' inicia a implantação de um Azure Logic App integrado às ações do Security Copilot, que usa um gatilho de incidente do Microsoft Sentinel. <br>
O Logic App é configurado para execução diária e gera um relatório de todos os incidentes do Defender abertos nas últimas 24 horas e ainda em andamento. Em seguida, o Copilot consolida esses relatórios de incidentes e os envia por email ao endereço designado do gerente do SOC.


### Pré-requisitos

Antes de iniciar o processo de instalação, confirme que você atende aos seguintes pré-requisitos: <br>
• O usuário que implantará este Logic App precisa ter a função Contributor.<br>
• A licença do Security Copilot está habilitada em seu locatário. <br>
• O usuário autenticado na ação do Logic App do Copilot tem permissão para enviar emails.<br>


<br>

• Este Logic App pode ser agendado para execução regular. Recomendamos alinhar o agendamento às trocas de turno do SOC da sua organização. Atualmente, ele é executado a cada 24 horas e obtém os incidentes do Defender das 24 horas anteriores. No entanto, esse agendamento pode ser ajustado conforme a necessidade.<br>


<br>

### Implantação

Para implantar o Logic App acima:<br>
•   Selecione a opção Deploy, sua assinatura e o grupo de recursos (escolha o mesmo locatário em que o Security Copilot está habilitado).<br>

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FSecurity-Copilot%2Fmain%2FLogic%2520Apps%2FSecurityCopilot-SOCshift-reporting-transfer%2Fazuredeploy.json" target="_blank">
    <img src="https://aka.ms/deploytoazurebutton"/>
</a>
<br>

### Pós-implantação

•   Autentique-se com os usuários mencionados acima (você pode usar usuários diferentes para as ações do Copilot e do Sentinel).<br>
•   Para executar o Logic App manualmente, abra a página de incidentes do Microsoft Sentinel, clique com o botão direito em um incidente específico e selecione Run playbook; depois, selecione o Logic App recém-implantado e escolha Run.<br>
•   Para executar o Logic App automaticamente, crie uma regra de automação no Sentinel e conecte este playbook como ação da regra.<br>



<img src="./images/designer.png"/>

#### Exemplo de relatório por email

</br>
<img src="./images/email_report.png"/>

</br>
