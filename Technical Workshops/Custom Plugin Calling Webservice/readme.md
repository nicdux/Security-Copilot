# Introdução
![Logotipo do Security CoPilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)
### Criar um plugin personalizado que chama um serviço Web
#### 🎓 Nível: 200 (intermediário)

### Objetivos

Esta pasta contém três plugins para enviar dados por GET (com e sem parâmetros) e POST (parâmetros enviados por JSON). Os plugins fazem chamadas REST para um site baseado em Python/Flask, disponível na pasta FlaskWebsite. O objetivo dos arquivos YAML dos plugins e do site Flask é mostrar como chamar uma API REST específica e criar os prompts corretos para que o planejador/orquestrador do Security Copilot selecione seu plugin e faça a chamada REST. Como as chamadas são feitas para um serviço Web personalizado, você pode observar o tipo de troca de dados que ocorre entre o Security Copilot e seu serviço Web.

### Etapas

1. Embora seja possível usar qualquer aplicativo padrão que exponha uma API REST, será mais fácil e claro do lado do servidor se criarmos um serviço Web simples e fizermos nosso plugin chamá-lo. Criamos esse serviço Web em Python com o framework Web Flask. Primeiro, faça o serviço funcionar em sua máquina local e teste-o em um navegador inserindo a URL http://127.0.0.1:5000

2. Depois de comprovar que seu aplicativo Web Flask está em execução localmente, será necessário executar o site acima em um host acessível pela Internet, pois o Security Copilot é um aplicativo baseado em nuvem. A melhor opção é usar o Azure App Service. As instruções para hospedar e executar um aplicativo Web Python no Azure App Service estão disponíveis [aqui](https://learn.microsoft.com/en-us/azure/app-service/quickstart-python?tabs=flask%2Cwindows%2Cazure-cli%2Czip-deploy%2Cdeploy-instructions-azportal%2Cterminal-bash%2Cdeploy-instructions-zip-azcli). O Azure App Service também adiciona uma camada TLS ao site (permitindo usar HTTPS), mesmo que nosso serviço Web não use TLS. Outra opção é executar o servidor Web em uma VM hospedada no Azure, mas você não terá o benefício de uma camada TLS. Embora o Security Copilot possa chamar sites HTTP e HTTPS, o TLS é indispensável em qualquer aplicativo de produção.

3. Carregue o documento OpenAPI (com _OAPI_ no nome do arquivo) em um local acessível pela Internet ou baixe-o deste GitHub. Você também pode usar o serviço Web Flask para fornecê-lo movendo os arquivos para a pasta <i>Files</i>.

4. Verifique se as URLs do documento de especificação OpenAPI estão corretas nos arquivos YAML principais (aqueles sem _OAPI_). Haverá um arquivo YAML principal correspondente para cada arquivo YAML com _OAPI_ no nome.

5. Carregue o documento YAML principal (um para cada plugin) no Copilot e confirme se o carregamento foi bem-sucedido. Agora você pode começar a usar o plugin.

Mais instruções sobre o uso desses plugins estão disponíveis neste [artigo](https://techcommunity.microsoft.com/t5/microsoft-security-copilot-blog/how-to-build-a-copilot-for-security-api-plugin-part-1/ba-p/4107604) da Microsoft Tech Community.