![Logotipo do Security Copilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)

**AVISO DE ISENÇÃO DE RESPONSABILIDADE**: este método de carregamento de Promptbooks usa chamadas de API não publicadas, que estão sujeitas a alterações sem aviso prévio. Este método não tem suporte oficial da Microsoft e não há garantia de que funcionará em seu ambiente. Não é possível abrir tíquetes de suporte relacionados a essa funcionalidade.

# PowerShell do Microsoft Security Copilot para gerenciar Promptbooks

Há dois scripts do PowerShell: um para carregamento e outro para download.

# Download de Promptbooks
O script do PowerShell 'PromptBooksDownload.ps1' permite baixar todos os seus Promptbooks para o disco local, dentro da pasta './Downloads'. Os Promptbooks são armazenados no formato JSON, cada um em seu próprio arquivo JSON. Cada arquivo recebe o nome do Promptbook, sem espaços nem caracteres especiais. Para baixar todos os Promptbooks, execute o seguinte comando.

Powershell -file PromptBooksDownload.ps1 -token <authorization token> -namecontains "CVE"

O parâmetro '-namecontains' é opcional. Quando ele é especificado, o script baixa apenas os Promptbooks cujo nome contém a expressão definida pelo parâmetro '-namecontains' ("CVE", neste caso). Informe a expressão entre aspas duplas.

A descrição do formato JSON e as instruções para obter o token de autorização são apresentadas abaixo.

IMPORTANTE: durante o processo de download, determinados campos do Promptbook que podem identificar a origem (tenant, hora de criação etc.) são removidos por motivos de segurança. Além disso, a visibilidade de todos os Promptbooks é definida como 'Private'. Assim, se os Promptbooks baixados forem carregados em outro tenant, permanecerão privados e precisarão ser alterados manualmente para ficarem visíveis na organização. O campo 'Plugins', atribuído a cada prompt de um Promptbook, também é removido.

# Carregamento de Promptbooks

O script do PowerShell 'PromptBooksUpload.ps1' permite carregar vários Promptbooks de uma só vez. Os Promptbooks devem estar no formato JSON, cada um em seu próprio arquivo JSON. Depois de criados, os arquivos JSON devem ser colocados na pasta ./Uploads. Em seguida, execute o comando abaixo para carregá-los em sua instância do Copilot:

Powershell -file PromptBooksUpload.ps1 -token <authorization token>

A descrição do formato JSON e as instruções para obter o token de autorização são apresentadas abaixo:

# Formato JSON de Promptbook

O exemplo a seguir é um modelo de formato JSON para um Promptbook que executa prompts em sequência. A maioria dos nomes de propriedades JSON é autoexplicativa. Verifique se a variável usada nas entradas do Promptbook corresponde à especificação nos prompts, respeitando maiúsculas e minúsculas.

```
{"name":"Sample promptbook to use as a template",
"description":"This is sample promptbook JSON that can be used to generate other promptbooks",
"prompts":
[
 {"promptType":"Prompt","content":"Give me more information on <user>"},
 {"promptType":"Prompt","content":"Is this user considered risky"},
 {"promptType":"Prompt","content":"Are they other Defender incidents concerning this user"},
 {"promptType":"Prompt","content":"Give a summary of all results so far"}
],
"promptbookinputs":
[
 {"name":"user","description":"User input"}
],
"visibility":"Private","tags":null}
```

Vários arquivos JSON de Promptbook foram disponibilizados na pasta Uploads para servir como referência.

# Token de acesso

No momento, o comando de entrada da Azure CLI não consegue obter o token do Security Copilot. Portanto, você precisará obter o token de acesso de uma sessão existente no navegador. No Microsoft Edge, entre no console do Security Copilot e, depois de concluir o processo de autenticação, incluindo MFA, pressione 'F12' para abrir as ferramentas de desenvolvimento do navegador.

![Ferramentas do navegador](https://github.com/Azure/Copilot-For-Security/blob/main/Images/Promptbook_images/promptBook_devtools.png)

Em seguida, acesse os Promptbooks no console e filtre por 'Promptbooks' nas ferramentas de desenvolvimento, na guia de rede. Você pode obter o token de acesso nos cabeçalhos da solicitação GET feita à URI de Promptbooks (https://api.securitycopilot.microsoft.com/geo/eastus/promptbooks). Copie o token inteiro da solicitação, sem incluir a palavra-chave 'Bearer' nem espaços adicionais.

Você também pode obter o token de outras URIs no console do Copilot; acessar os Promptbooks é apenas uma das opções. Depois de copiar o token, você estará pronto para executar o PowerShell.

![Copiar o token de acesso](https://github.com/Azure/Copilot-For-Security/blob/main/Images/Promptbook_images/promptBook_token.png)

# Execução de download e carregamento

Acesse a pasta na qual estão os arquivos 'PromptBooksDownload.ps1' e 'PromptBooksUpload.ps1'. Essa mesma pasta deve conter as subpastas 'Downloads' e 'Uploads'. A subpasta 'Uploads' deve conter todos os arquivos JSON de Promptbook que você pretende carregar em sua instância do Security Copilot.

Se a instância do Security Copilot não estiver em 'eastus', altere a URI na linha 11 para que ela contenha a região correta. O carregamento falhará se isso não for corrigido.

Execute o comando a seguir, colando o token copiado do navegador depois do argumento de linha de comando -token.

Download: Powershell -file PromptBooksDownload.ps1 -token <authorization token>

Upload: Powershell -file PromptBooksUpload.ps1 -token <authorization token>

A captura de tela a seguir mostra o processo de carregamento:

![Linha de comando do PowerShell](https://github.com/Azure/Copilot-For-Security/blob/main/Images/Promptbook_images/promptBook_commandLine.png)

Durante a execução, o PowerShell exibirá o nome do arquivo e o status de cada carregamento. No caso de downloads, será exibido o nome do arquivo que está sendo gravado. Se ocorrer um erro, consulte a seção de solução de problemas.

![Execução bem-sucedida do PowerShell](https://github.com/Azure/Copilot-For-Security/blob/main/Images/Promptbook_images/promptBook_results.png)

IMPORTANTE: depois que o download ou carregamento for concluído com êxito, saia explicitamente do console do Security Copilot para invalidar o token de autorização. Embora o token seja válido apenas por um período determinado, essa saída explícita impede que ele seja reutilizado.

# Solução de problemas:

- Se você receber HTTP 401, verifique se o token é válido. Ele não deve estar expirado nem conter espaços à esquerda ou à direita quando for colado. Confira também se a URI no script do PowerShell especifica a região correta.
- Se você receber HTTP 400, verifique se o arquivo JSON do prompt está correto. Se estiver usando uma variável, confirme especificamente se ela tem o mesmo nome nos prompts e na seção 'promptbookinputs'. O nome da variável diferencia maiúsculas de minúsculas, e o nome do token e sua descrição não podem ter o mesmo texto.
- Se você receber HTTP 500, verifique o formato JSON. Um JSON com uma vírgula ausente ou adicional é inválido; recomendamos processá-lo em um formatador para identificar problemas.

**Documentação**
- [Usar Promptbooks | Microsoft Learn](https://learn.microsoft.com/en-us/security-copilot/using-promptbooks)
- [Criar seus próprios Promptbooks | Microsoft Learn](https://learn.microsoft.com/en-us/security-copilot/build-promptbooks)

**Pré-requisitos**
- Verifique se você tem o acesso e as permissões adequados para criar Promptbooks. [Entender a autenticação no Microsoft Security Copilot | Microsoft Learn](https://learn.microsoft.com/en-us/security-copilot/authentication)
