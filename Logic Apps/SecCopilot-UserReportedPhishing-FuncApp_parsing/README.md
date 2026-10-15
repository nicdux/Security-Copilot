# Análise de phishing relatado por usuários com o Security Copilot
Autores: Yaniv Shasha e Craig Freyman
Esta solução automatiza a análise de emails de phishing relatados por usuários usando o Security Copilot. Ela monitora uma caixa de entrada compartilhada e aciona um Logic App quando um novo email chega. O Logic App processa o email usando um Function App, que extrai os detalhes relevantes, usa as habilidades MDTI do Security Copilot para obter informações de reputação e envia os resultados a um destinatário por email.

## Implantar a solução

### Etapa 1: implantar o Function App

Clique no botão abaixo para implantar o Function App. Você deverá selecionar ou criar um grupo de recursos e fornecer um nome exclusivo para o Function App. Verifique se o Function App foi totalmente implantado antes de iniciar a implantação do Logic App.

[![Implantar no Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FCopilot-For-Security%2Fmain%2FLogic%2520Apps%2FSecCopilot-UserReportedPhishing-FuncApp_parsing%2Ffunctionapp_azuredeploy.json)

Se tiver problemas, você pode criar um Function App vazio/básico e implantá-lo pela linha de comando:
`az functionapp deployment source config-zip --resource-group yourresourcegroup --name youremptyfunctionapp --src .\FunctionApp.zip` <- arquivo ZIP baixado no diretório local.

### Etapa 2: implantar o Logic App

Clique no botão abaixo para implantar o Logic App. Anote o nome e o grupo de recursos do Function App da etapa anterior. Essas informações serão inseridas na tela de implantação.

[![Implantar no Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FCopilot-For-Security%2Fmain%2FLogic%2520Apps%2FSecCopilot-UserReportedPhishing-FuncApp_parsing%2Flogicapp_azuredeploy.json)


### Etapa 3: inicializar as conexões de API do O365 e do Security Copilot

Abra o novo Logic App.

Clique em "API Connections".

![Conexões de API](image.png)

Autorize as duas conexões de API.
![Autorização das conexões de API](image-1.png)

### Etapa 4: habilitar o Logic App
![Habilitação do Logic App](image-3.png)

### Observações sobre a implantação
Se quiser alterar o código do Function App, você pode clonar o repositório com o Git. Sempre que alterar o código do FunctionApp, reempacote o arquivo FunctionApp.zip. O arquivo ZIP é a referência usada na implantação da solução. A pasta .python_packages é necessária neste cenário de implantação. Não foi possível determinar como fazer com que os Azure Function Apps instalem as bibliotecas Python automaticamente.

## Detalhes das funções
Há cinco funções no Function App:

### 1. parse_email
Este Azure Function App em Python foi projetado para tratar solicitações HTTP que contenham dados brutos de email. Seus principais recursos incluem:

**Análise de email**:
    - Extrai os principais metadados (por exemplo, remetente, destinatário, caminho de retorno, assunto e data).
    - Obtém o conteúdo principal do corpo, trata emails multiparte e limpa mensagens encaminhadas.
    - Identifica os resultados de autenticação DKIM, SPF e DMARC nos cabeçalhos do email.
    - Processa anexos, calcula hashes SHA-256 e captura o conteúdo Base64 e o tipo MIME.

**Extração e processamento de URLs**:
   - Extrai URLs do corpo dos emails em HTML e texto sem formatação.
   - Decodifica Microsoft SafeLinks e expande URLs encurtadas seguindo os redirecionamentos.
   - Se a contagem for superior a 20, remove as duplicatas e mantém URLs base exclusivas, além de remover todas as marcas HTML.
   - Filtra URLs de imagens e verifica a validade das URLs.

**Extração de domínios e filtragem de IPs**:
   - Identifica e filtra os domínios para garantir a validade.
   - Distingue IPs públicos e não públicos usando padrões de expressão regular e a biblioteca `ipaddress`.
   - Retorna os IPs públicos e as URLs extraídos para fins de segurança e análise.

**Análise recursiva**:
   - Analisa recursivamente o conteúdo, inclusive JSON aninhado, para extrair domínios, IPs e URLs, facilitando a análise estruturada do conteúdo do email.
   
**Limpeza de HTML e conteúdo**:
   - Remove quebras de linha em excesso e marcas HTML para produzir um conteúdo de texto mais limpo na resposta.

**Tratamento de erros**:
   - Fornece tratamento e registro abrangentes de erros em vários pontos de falha, inclusive dados malformados ou erros de análise.

A função retorna uma resposta JSON que contém os dados de email analisados, as URLs extraídas, os IPs públicos e os domínios limpos, tornando-a adequada para integração com fluxos de trabalho de segurança e análise.

### 2. parse_virustotal_json
Este Azure Function App em Python foi projetado para tratar solicitações HTTP que contenham um objeto JSON do VT, facilitando a filtragem. A API do VT retorna dados em excesso para a IA generativa.

**Análise da solicitação**:
   - Aceita e analisa um objeto JSON da solicitação HTTP, esperando especificamente um objeto `data` que contenha `attributes` com `last_analysis_results`.

**Detecção de conteúdo malicioso ou suspeito**:
   - Extrai os resultados da análise de `last_analysis_results` e filtra as entradas em que `category` esteja rotulada como "malicious" ou "suspicious".
   - Para cada entrada sinalizada, coleta detalhes como `engine_name`, `method` e `result` usados pelos mecanismos de análise do VirusTotal.

**Geração de resposta**:
   - Retorna uma resposta JSON que lista todas as descobertas maliciosas ou suspeitas, inclusive os detalhes relevantes do mecanismo de detecção, facilitando o processamento posterior da inteligência contra ameaças ou a geração de alertas.

**Tratamento de erros**:
   - Registra os erros se a análise falhar ou se a estrutura JSON for inesperada, retornando o erro 500 com uma mensagem.

### 3. normalize_json
Este Azure Function App é uma função acionada por HTTP, projetada para limpar e validar entradas JSON removendo notações Markdown e tratando valores `null`. Sua principal finalidade é aceitar a notação JSON em Markdown gerada pelo Security Copilot e convertê-la em um objeto JSON limpo.

**Remoção da notação Markdown**:
   - Remove da entrada JSON as anotações Markdown, inclusive três acentos graves (```json) e notações alternativas como `~~~json`, limpando o texto para uma análise JSON válida.

**Substituição de valores nulos**:
   - Substitui recursivamente todos os valores `null` do objeto JSON pela cadeia de caracteres `"None"`, atendendo aos casos em que `null` precisa ser preservado como texto para saída ou processamento posterior.

**Geração de resposta**:
   - Retorna como resposta uma cadeia de caracteres JSON limpa e formatada, pronta para uso posterior e fácil de ler.

**Tratamento de erros**:
   - Captura erros de decodificação de JSON quando a entrada está formatada incorretamente e retorna o erro 400 com uma mensagem útil.
   - Registra todos os erros inesperados e retorna o erro 500, garantindo robustez.

### 4. json_to_html
Este Azure Function App é uma função acionada por HTTP, projetada para gerar um relatório HTML de análise de phishing com base em dados JSON.

**Geração de relatório HTML**:
   - Usa modelos Jinja2 para criar, a partir da entrada JSON, um relatório HTML detalhado e estilizado, com seções para "Final Evaluation", "Email Body Analysis", "Attachment Review", "Domain Evaluation" e "URL Evaluation".
   - Destaca as principais descobertas com cores personalizadas baseadas em valores como `Classification`, `Confidence Level` e `Phishing Likelihood`.
   - Formata listas, tabelas e indicadores, criando um layout claro e estruturado que facilita a análise.

**Análise e validação de JSON**:
   - Analisa os dados JSON do corpo da solicitação HTTP e valida se eles formam uma lista de objetos JSON; caso não estejam no formato esperado, emite o erro 400.
   
**Ordem de seções personalizável**:
   - Processa as seções em uma ordem predefinida, garantindo uma estrutura HTML consistente mesmo que as seções apareçam em outra ordem no JSON de entrada.

**Tratamento de erros**:
   - Captura erros de análise de JSON e outras exceções inesperadas, retornando respostas HTTP informativas (400 para formato JSON inválido e 500 para outros problemas).

### 5. parse_pdf
Este Azure Function App é uma função acionada por HTTP que processa um arquivo PDF codificado em Base64 no corpo da solicitação, extrai o texto e o retorna em um formato limpo. Em seguida, o texto é acrescentado à variável 'email_body' no Logic App.

**Decodificação de PDF em Base64**:
   - Aceita o PDF como uma cadeia de caracteres codificada em Base64 no corpo da solicitação HTTP, diretamente ou em um conteúdo JSON (campo `body`).
   - Permite prefixos opcionais de URI de dados, que são removidos antes da decodificação.

**Extração de texto de PDF**:
   - Usa `pdfminer` para extrair o texto bruto do arquivo PDF, tratando os dados binários da cadeia de caracteres Base64 decodificada.

**Limpeza de texto**:
   - Realiza o pós-processamento do texto extraído para remover caracteres não imprimíveis e reduzir o excesso de espaços em branco, retornando uma saída de texto limpa e compacta.

**Tratamento de erros**:
   - Registra erros de decodificação, problemas de análise de JSON e exceções inesperadas, fornecendo respostas informativas:
     - Status 400 para Base64 inválido ou formatação JSON inválida.
     - Status 500 para erros de processamento inesperados, com registro detalhado para depuração.
