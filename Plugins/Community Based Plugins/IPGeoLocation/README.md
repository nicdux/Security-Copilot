# Plugin personalizado do Copilot for Security — API — Obter informações de IP no IP Geo Location

#### Plugin do Copilot for Security para coletar a localização e o ISP (organização) de um endereço IP usando o IP Geo Location

### Pré-requisitos

* [Copilot for Security habilitado](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
* [Acesso para carregar plugins personalizados](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)
* [Chave de API](https://app.ipgeolocation.io/signup) do IP Geo Location

### Instruções
#### Carregar o plugin personalizado

1. Obtenha o arquivo [ipgl-manifest.yaml](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/IPGeoLocation/ipgl-manifest.yaml) deste diretório.
2. [Carregue o plugin personalizado](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#add-custom-plugins) e verifique se ele está ativado.
3. Após carregar o plugin, insira sua [chave de API do IP Geo Location](https://learn.microsoft.com/en-us/security-copilot/plugin_api#configure-authentication-1).

![CopilotForSecurity](https://learn.microsoft.com/en-us/security-copilot/media/add-plugin-button.png)

### Uso do plugin

A seguir estão algumas consultas de exemplo que você pode usar para acionar este plugin:

* Resuma as informações do IP 1.1.1.1 no IP Geo Location.
* Resuma em tópicos as informações do IP 4.4.4.4 no IP Geo Location.
* Forneça a localização, o ISP e a pontuação de reputação do endereço IP 8.8.8.8 no IP Geo Location em formato de tabela.
<br>
<img src="https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Images/ipgl-example-screenshot-1.png"/>
<br>
<img src="https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Images/ipgl-example-screenshot-2.png"/>