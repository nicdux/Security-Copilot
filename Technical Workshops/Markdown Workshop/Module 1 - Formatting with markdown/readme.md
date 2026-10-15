## Módulo 1 - Formatação com Markdown no Microsoft Security Copilot

![Logotipo do Security CoPilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)

#### ⌛ Tempo estimado para concluir este laboratório: 15 minutos
#### 🎓 Nível: 100 (iniciante)

Os prompts de exemplo a seguir demonstram como os usuários podem modificar a saída de uma habilidade de plugin usando Markdown. Os LLMs interpretam o contexto e seguem instruções com mais eficiência quando delimitadores e Markdown são incluídos nos prompts. Embora seja possível usar linguagem natural, ela costuma exigir explicações mais detalhadas do que a maioria dos usuários está disposta a fornecer. Ao oferecer instruções claras e usar Markdown, conforme abordado neste módulo, você pode reduzir a probabilidade de variações na saída.

1. [Prompt inicial](#initial-prompt)
2. [Formatação como tabela com AskGPT](#formatting-as-a-table-with-askgpt)
3. [Formatação como lista com AskGPT](#formatting-as-a-list-with-askgpt)
4. [Combinação de um prompt com instruções de formatação Markdown](#combining-a-prompt-with-Markdown-formatting-instructions)
5. [Markdown disponível](#available-markdown)
6. [Aumento da eficiência](#increasing-efficiency)


### Prompt inicial

Executar um prompt sem especificar as expectativas de saída pode gerar formatação inconsistente, como alternância entre tabelas e listas com marcadores. Quando os usuários não fornecem instruções detalhadas sobre o formato desejado, a habilidade retorna todos os dados disponíveis. Neste exemplo, a saída começa com "Incident ID", seguida por "Display Name", "Severity" e assim por diante.

```
List the last 3 incidents from Defender.
```
![Imagem](./images/001_prompt_no_Markdown.png)

### Formatação como tabela com AskGPT

Para modificar a saída padrão, podemos usar a habilidade /AskGPT e instruir o modelo a não realizar nenhuma ação além de ler as instruções. Em seguida, especifique que as saídas posteriores devem seguir o formato Markdown fornecido. Lembre-se de que isso não reformatará resultados existentes; a instrução precisa ser definida **antes** do prompt cuja saída você deseja alterar.
```
/AskGPT No action is needed at this time, simply review the following instructions and respond with 'Ready!'. Instructions: All additional responses will be formatted to conform to the following Markdown example.
## Markdown example
|  **Created Date**       | **Incident ID** | **Status** | **Incident URL**  | **Title**            | **Severity** | **Assigned To** | **Classification** | **Determination** | **Last Updated**             | 
|-------------------------|-----------------|------------|-------------------|----------------------|--------------|-----------------|--------------------|-------------------|------------------------------| 
| 2025-01-08T12:09:40.47Z |     1234        |   Active   | https://12.aka.ms | Multi-stage incident | High         | John.Doe        | Malware            | True Positive     | 2025-01-22T23:33:21.1733333Z |
```
![Imagem](./images/002_AskGPT_Markdown_formatting.png)

Observe que executar novamente o [prompt inicial](#initial-prompt) agora gera "Created Date" como primeira coluna, seguida por "Incident ID" e "Status", em vez de "Incident ID", "Display Name" e "Severity". **Aplique essas instruções antes de formatar outros prompts.** Para melhorar a organização e facilitar o acesso, considere salvar este prompt em um promptbook.

![Imagem](./images/003_AskGPT_formatting_as_a_table_prompt.png)

### Formatação como lista com AskGPT

Outro exemplo de formatação Markdown é mostrado abaixo, usando marcadores, recuos e uma linha horizontal após cada incidente. Neste exemplo, os campos "Assigned To", "Classification" e "Determination" foram excluídos da saída formatada ao serem removidos do exemplo de Markdown.
```
/AskGPT No action is needed at this time, simply review the following instructions and respond with 'Ready!'. Instructions: All additional responses will be formatted to conform to the following Markdown example.
- **Created Date**: `2025-01-08T12:09:40.47Z`
  - **Incident ID**: `1234`
  - **Status**: `Active`
  - **Title**: `Multi-stage incident`
    - **Severity**: `High`
  - **Last Updated**: `2025-01-22T23:33:21.1733333Z`
    -  **Incident URL**: [Incident Details](https://12.aka.ms)
---
```


![Imagem](./images/004_AskGPT_formatting_as_a_list_prompt.png)


![Imagem](./images/005_AskGPT_formatting_as_a_list_result.png)

---


### Combinação de um prompt com instruções de formatação Markdown

Em vez de separar a solicitação, você pode incluir a formatação no próprio prompt. Combinar o prompt e as instruções de formatação pode ser útil ao trabalhar com Logic Apps e ajuda a reduzir o uso de SCUs.

 ```
List the last 3 incidents from Defender. Ensure the output is formatted to conform to the following Markdown example.
## Markdown example
| **Incident ID** | **Status** | **Incident URL**  | **Title**            | **Severity** | **Assigned To** | **Classification** | **Determination** | **Created Date**         | **Last Updated**            | 
|-----------------|------------|-------------------|----------------------|--------------|-----------------|--------------------|-------------------|--------------------------|-----------------------------| 
|     1234        |   Active   | https://12.aka.ms | Multi-stage incident | High         | John.Doe        | Malware            | True Positive     | 2025-01-08T12:09:40.47Z | 2025-01-22T23:33:21.1733333Z |
```
![Imagem](./images/006_prompt_that_includes_AskGPT_formatting.png)


---
### Markdown disponível

Devido à rapidez das mudanças no Security Copilot, a melhor maneira de visualizar quais elementos de sintaxe Markdown estão disponíveis é usar o prompt a seguir.

Atualmente, a instância autônoma do Security Copilot não oferece suporte à renderização de todos os elementos de sintaxe Markdown (por exemplo, determinados títulos e imagens). Embora você ainda possa incluir esses elementos nos prompts, a saída precisará ser processada e renderizada por outro serviço.

```
/AskGPT Assume the role of a Markdown syntax expert. Provide a comprehensive list of Markdown syntax elements, including tables, numbered lists, task lists, and horizontal rules. For each element, provide instructions on how I can replicate them myself and what it would look like when rendered.
```
Para consultar a especificação oficial do Markdown, acesse o [CommonMark](https://commonmark.org/help/).

### Aumento da eficiência

Todos os métodos de formatação Markdown acima incluem caracteres adicionais para ajudar os usuários a visualizar o formato. Para aumentar a eficiência, você pode remover espaços duplos e hifens extras. Veja um exemplo:

```
| **Incident ID** | **Status** | **Incident URL** |
| --- | --- | --- |
| 1234 | Active | https://12.aka.ms |
```