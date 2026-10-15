# Enviar por email os resultados do Promptbook do Security Copilot

Este Logic App executa o Promptbook especificado no Security Copilot (Copilot for Security). Em seguida, converte para HTML a resposta de cada prompt, escrita na linguagem Markdown simplificada do Security Copilot. Usando esses trechos HTML ou respostas em texto sem formatação e partindo de um modelo HTML personalizável, ele monta o corpo HTML de um email e, por fim, envia esse email aos destinatários especificados. É possível excluir do email uma ou mais respostas do Promptbook pelo índice de posição (1, 2, 3 etc.); também é possível substituir o texto de um ou mais prompts no email para facilitar a leitura.

Consulte este artigo para obter mais detalhes e assistir a um vídeo sobre como implantar e usar a solução: https://www.linkedin.com/pulse/sending-security-copilot-promptbook-responses-via-stefano-pescosolido-wcalf.

### Pré-requisitos:
* Este Logic App é útil quando há Security Compute Units (SCUs) ativas para o Security Copilot


### Ações pós-implantação:
1. Defina as credenciais da conexão de API OAuth com o Security Copilot e o Office 365 (a conexão com o O365 é usada para enviar o email).
2. Edite o fluxo de trabalho e defina o nome do Promptbook e os parâmetros relacionados na ação run-prompt (após a implantação, eles ficam vazios).
3. No editor do fluxo de trabalho, se necessário, modifique o tipo e/ou os parâmetros do gatilho (por exemplo, altere a data e a hora da recorrência ou substitua o gatilho pelo gatilho de incidente do Microsoft Sentinel).
4. No editor do fluxo de trabalho, abra os parâmetros e defina o título, o assunto e os destinatários desejados para o email.
5. No editor do fluxo de trabalho, na lista de parâmetros, se necessário, especifique os índices dos prompts que não devem ser incluídos no email (use o parâmetro SkipPromptsInOutput).
6. No editor do fluxo de trabalho, se necessário, personalize ainda mais o assunto do email (por exemplo, se você alterou o gatilho para MS Sentinel Incident, talvez queira incluir a ID do incidente no final do assunto).
7. Habilite o Logic App (o modelo o implanta no estado desabilitado).

## Botão de implantação
[![Implantar no Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FSecurity-Copilot%2Frefs%2Fheads%2Fmain%2FLogic%2520Apps%2FCfS-SendPromptbookResultsByEmail%2FCfS-SendPromptbookResultsByEmail.json)

## Exemplo de personalização do email:
A imagem a seguir mostra:
1. O Promptbook padrão "Vulnerability impact assessment" usado como exemplo
2. O email enviado com o modelo HTML padrão
3. A personalização de três parâmetros: HtmlBodyHeader (para alterar as cores), SkipPromptsInOutput (para ocultar o segundo prompt e a respectiva resposta no email) e ReplacePromptsInOutput (para substituir, no email, o texto do primeiro e do terceiro prompt. Observação: o segundo prompt da matriz é mantido como uma cadeia de caracteres vazia "", o que significa que não deve haver substituição; o último prompt nem sequer é incluído, o que também significa que não haverá substituição)<br>
4. O email enviado com essa personalização
   
![Exemplo de personalização do email](./Example%20of%20email%20customization.png)
