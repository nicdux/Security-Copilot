# Introdução
![Logotipo do Security CoPilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)
#### ⌛ Tempo estimado para concluir este laboratório: 10 minutos
#### 🎓 Nível: 100 (iniciante)

#### Objetivos

Ao concluir este guia técnico, você terá as seguintes habilidades:<br>

* Carregar um plugin personalizado do Microsoft Security Copilot do tipo Logic App.<br>
* Implantar um Azure Logic App capaz de processar prompts do Microsoft Security Copilot.<br>
* Criar uma sessão do Microsoft Security Copilot que acione esse Logic App.<br>

#### Cenário
Neste workshop técnico, os participantes aprenderão a carregar um plugin personalizado do Microsoft Security Copilot do tipo Logic App e implantar o Logic App correspondente. Para concluir esta tarefa com êxito, você precisa atender aos seguintes pré-requisitos:<br>

* Você precisa ter seu próprio locatário e uma instância do Microsoft Security Copilot.<br>
* Você precisa ter permissão para carregar um plugin personalizado.<br>
* Você precisa ter permissão para implantar um Logic App.<br>


#### Instruções

## Implantar o aplicativo lógico

	1. Implante o Logic App acima clicando no botão "Implantar no Azure".

Selecione a assinatura, o grupo de recursos e o nome do aplicativo lógico.

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FYaniv-Shasha%2FSecurityCopilot%2Fmain%2FWorkshop%2FCustom_Plugin%2FTask01_Send_jokeByemail%2FWorkshop01-sendJokeByemail%2Fazuredeploy.json" target="_blank">
    <img src="https://aka.ms/deploytoazurebutton"/>
</a>
<br>

<img src="./Images/deploy_logic_app.jpg"/>

<br>
	2. Depois que o Logic App for criado, localize-o e autentique a ação "enviar email" com um usuário que tenha uma caixa de correio no O365.

<img src="./Images/auth_logicapp.jpg"/>

<br>

### Carregar o plugin personalizado

Baixe uma cópia local do arquivo "SendJokeByEmail.yml" localizado na mesma pasta e edite-o.<br>
Adicione as seguintes informações:

1. O SubscriptionId em que você implantou seu Logic App.
2. O ResourceGroup em que você implantou o Logic App.
2. Se você alterou o nome padrão do aplicativo lógico, ajuste o nome no arquivo.

<img src="./Images/yaml_subid.jpg"/>

3. Carregue o plugin personalizado e verifique se ele está ativado.

<img src="./Images/upload_plugin.jpg"/>


<img src="./Images/check_if_plugin_isON.jpg"/>

4. **Execute os seguintes prompts:**

* Conte-me uma piada relacionada à segurança para hoje.<br>
* Execute a lógica para enviar a piada acima para este email: <youremailaddress@email.com>..<br>

<img src="./Images/prompts.jpg"/>

5. Para monitorar o processo, abra o Logic App que acabou de criar e verifique as últimas execuções.

<img src="./Images/run_history.jpg"/>

6. Abra sua caixa de entrada e examine o email.<br>

### Até a próxima tarefa!