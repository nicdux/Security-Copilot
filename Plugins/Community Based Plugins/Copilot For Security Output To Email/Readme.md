![Visão geral do Security Copilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)
# Plugins personalizados do Microsoft Security Copilot — Enviar saída do Copilot por email

# Plugin para enviar a saída do Copilot por email

## Visão geral

O plugin "Send Copilot Output to Email" foi desenvolvido para se integrar perfeitamente ao Microsoft Security Copilot. Sua principal finalidade é obter uma saída gerada pelo Copilot e enviá-la a um endereço de email especificado. Esse plugin amplia a flexibilidade do Copilot ao permitir que os usuários recebam alertas e notificações de segurança importantes diretamente na caixa de entrada.

## Componentes da solução

A solução do plugin é composta pelos seguintes componentes:

1. **Arquivo YAML**: contém as configurações necessárias ao funcionamento correto do plugin. Os usuários precisam modificar esse arquivo para especificar o endereço de email ao qual a saída do Copilot deve ser enviada.

2. **Logic App**: responsável por acionar o processo de envio de email com base na saída do Copilot. O aplicativo recebe os dados provenientes do Copilot e os processa para enviar um email ao destinatário especificado.

## Implantação

Para implantar o plugin "Send Copilot Output to Email", siga estas etapas:

1. **Modificar a configuração YAML**: atualize o arquivo YAML incluído na solução com o endereço de email ao qual deseja enviar a saída do Copilot.

2. **Implantar o Logic App**: implante o Logic App incluído na solução em seu ambiente do Azure. Verifique se ele está configurado corretamente e conectado ao Copilot.

   <a href="https://portal.azure.com/#create/Microsoft.Template/uri/https://github.com/Azure/Copilot-For-Security/blob/main/Custom%20Plugins/Community%20Based%20Plugins/Copilot%20For%20Security%20Output%20To%20Email/SendCopilotOutputToEmail%20Logic%20App/azuredeploy.json" target="_blank">
    <img src="https://aka.ms/deploytoazurebutton"/>
</a>

3. **Adicionar o plugin ao Copilot**: depois que o Logic App estiver implantado e configurado, adicione o plugin "Send Copilot Output to Email" à sua instância do Copilot. Forneça os detalhes de autorização ou conexão necessários para que o plugin se comunique com o Copilot e acione o processo de envio de email.

4. **Testar**: teste o plugin gerando uma saída de exemplo no Copilot e verificando se o email é enviado ao endereço especificado.

## Uso

- Depois de implantar e configurar o plugin, o Copilot enviará automaticamente a saída ao endereço de email especificado sempre que ocorrerem eventos de segurança relevantes.
- Os usuários podem enviar a saída por email.
- Investigação e ação do Copilot usando o plugin personalizado para enviar a saída por email.

Veja um exemplo:
![Saída do Copilot para email](https://github.com/Azure/Copilot-For-Security/blob/main/Custom%20Plugins/Community%20Based%20Plugins/Images/Copilotoutputtoemail1.png)

A saída recebida por email:
![Saída do Copilot para email](https://github.com/Azure/Copilot-For-Security/blob/main/Custom%20Plugins/Community%20Based%20Plugins/Images/Copilotoutputtoemail2.png)
