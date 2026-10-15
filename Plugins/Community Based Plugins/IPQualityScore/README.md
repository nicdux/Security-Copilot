# Plugin personalizado do Security Copilot — API — Obter informações de IP no IP Quality Score

#### Plugin do Security Copilot para coletar o tipo, a localização, a pontuação de reputação e a velocidade de abuso de um endereço IP usando o IP Quality Score

### Pré-requisitos

* [Security Copilot habilitado](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
* [Acesso para carregar plugins personalizados](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)
* [Chave de API](https://www.ipqualityscore.com/proxy-vpn-tor-detection-service) do IP Quality Score

### Instruções
#### Carregar o plugin personalizado

1. Obtenha o arquivo [ipqs-manifest.yaml](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/IPQualityScore/ipqs-manifest.yaml) deste diretório.
2. [Carregue o plugin personalizado](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#add-custom-plugins) e verifique se ele está ativado.
3. Após carregar o plugin, insira sua [chave de API do IPQS](https://learn.microsoft.com/en-us/security-copilot/plugin_api#configure-authentication-1).

![CopilotForSecurity](https://learn.microsoft.com/en-us/security-copilot/media/add-plugin-button.png)

### Uso do plugin

A seguir estão algumas consultas de exemplo que você pode usar para acionar este plugin:

* Resuma as informações do IP 1.1.1.1 no IPQS.
* Resuma em tópicos as informações do IP 4.4.4.4 no IPQS.
* Forneça a localização, o ISP e a pontuação de reputação do endereço IP 8.8.8.8 no IPQS em formato de tabela.
<br>
<img src="https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Images/ipqs-example-screenshot-1.png"/>
<br>
<img src="https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Images/ipqs-example-screenshot-2.png"/>
