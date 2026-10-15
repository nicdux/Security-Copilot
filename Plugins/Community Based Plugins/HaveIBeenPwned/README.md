# Plugin personalizado do Security Copilot — API — Obter informações de violações de uma conta de usuário no Have I Been Pwned

#### Plugin do Security Copilot para coletar a lista de violações de uma conta de usuário usando o Have I Been Pwned

### Pré-requisitos

* [Security Copilot habilitado](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
* [Acesso para carregar plugins personalizados](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)
* [Chave de API](https://haveibeenpwned.com/API/Key) do Have I Been Pwned

### Instruções
#### Carregar o plugin personalizado

1. Obtenha o arquivo [hibp-manifest.yaml](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/HaveIBeenPwned/hibp-manifest.yaml) deste diretório.
2. [Carregue o plugin personalizado](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#add-custom-plugins) e verifique se ele está ativado.
3. Após carregar o plugin, insira sua [chave de API do Have I Been Pwned](https://learn.microsoft.com/en-us/security-copilot/plugin_api#configure-authentication-1).

![Copilot for Security](https://learn.microsoft.com/en-us/security-copilot/media/add-plugin-button.png)

### Uso do plugin

A seguir estão algumas consultas de exemplo que você pode usar para acionar este plugin.
Observação: você pode usar a palavra-chave 'Have I Been Pwned' ou 'HIBP' em suas consultas.

* Verifique se o usuário test@email.com faz parte de alguma violação de dados no Have I Been Pwned.
* Forneça a lista de violações do usuário test@email.com no Have I Been Pwned em tópicos.
* Resuma a lista de violações de dados do usuário test@email.com no Have I Been Pwned.
<br>
<img src="https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Images/hibp-example-screenshot.png"/>
