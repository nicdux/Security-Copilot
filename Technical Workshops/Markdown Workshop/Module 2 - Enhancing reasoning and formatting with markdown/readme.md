<!-- Autor: Rick Kotlarz -->
<!-- Última atualização: 17 de março de 2025 -->

## Módulo 2 - Aprimorando o raciocínio e a formatação com Markdown

![Logotipo do Security Copilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)

#### ⌛ Tempo estimado para concluir este laboratório: 15 minutos
#### 🎓 Nível: 200 (intermediário)

Os prompts de exemplo a seguir demonstram como os usuários podem aprimorar tanto a saída quanto o raciocínio por trás dela usando Markdown. Os LLMs interpretam o contexto e seguem instruções com mais eficiência quando os prompts incluem delimitadores e Markdown. Embora seja possível usar linguagem natural, ela costuma exigir explicações mais detalhadas, que muitos usuários talvez não estejam dispostos a fornecer. Ao oferecer instruções claras e usar Markdown, conforme descrito neste módulo, os usuários podem reduzir a probabilidade de inconsistências na saída.

Muitas vezes, os LLMs não são ajustados para compreender totalmente o contexto específico da consulta de um usuário. Embora plataformas como o Security Copilot ajudem a melhorar os prompts incluindo prompts de sistema que enfatizam a IA Responsável (RAI) e o uso pretendido de plugins ou habilidades, eles nem sempre atendem às expectativas do usuário. Para preencher essa lacuna, os usuários devem fornecer contexto e orientação adicionais, de acordo com as [práticas recomendadas de engenharia de prompts do Security Copilot](https://learn.microsoft.com/en-us/copilot/security/prompting-tips) e as práticas recomendadas gerais de engenharia de prompts para LLMs.

Este módulo mostra como os usuários podem combinar as práticas recomendadas de engenharia de prompts do Security Copilot com as práticas recomendadas gerais de engenharia de prompts para LLMs.

1. [Práticas recomendadas de engenharia de prompts para LLMs](#large-language-model-prompt-engineering-best-practices)
2. [Prompt inicial](#initial-prompt)
3. [Resumos, raciocínio e recomendações](#summarizing-reasoning-and-recommendations)
4. [Criação de links com IDs de alerta](#creating-links-from-alert-ids)
5. [Garantia de formatação consistente](#ensuring-consistent-formatting)
6. [Uso de promptbooks](#leveraging-promptbooks)

### Práticas recomendadas de engenharia de prompts para LLMs

Prompts eficazes são fundamentais para obter respostas precisas, relevantes e úteis dos modelos de linguagem. Ao seguir este conjunto de práticas recomendadas, os usuários podem garantir que as saídas do modelo fiquem mais alinhadas aos resultados desejados.

1. **Atribua uma persona** - Defina uma função específica para adaptar as respostas adequadamente. Por exemplo, instruir o modelo a agir como analista de dados pode gerar insights focados na interpretação dos dados.
2. **Use delimitadores** - Empregue delimitadores, como aspas triplas, para indicar claramente segmentos de texto específicos em tarefas como tradução ou resumo. Isso garante que o modelo processe a parte correta do texto. O Markdown pode simplificar esse processo.
3. **Forneça instruções passo a passo** - Divida tarefas complexas em etapas sequenciais para orientar o modelo durante o processo de raciocínio. Essa abordagem costuma gerar resultados mais precisos.
4. **Inclua exemplos** - Forneça um ou mais exemplos para mostrar o padrão ou o estilo desejado. Isso ajuda o modelo a inferir e reproduzir o formato de resposta esperado.
5. **Seja claro e específico** - Elabore prompts precisos e inequívocos, fornecendo contexto suficiente para que o modelo entenda e atenda à solicitação corretamente.
6. **Especifique o tom** - Se o tom for importante, especifique-o no prompt. Examine as saídas do modelo de maneira iterativa e refine os prompts para melhorar a qualidade das respostas.
7. **Refine iterativamente** - Examine continuamente as saídas do modelo e ajuste os prompts conforme necessário para melhorar a qualidade das respostas.


### Prompt inicial

Executar um prompt sem especificar as expectativas de saída pode gerar formatação inconsistente, como alternância entre tabelas e listas com marcadores. Quando os usuários não fornecem instruções detalhadas sobre o formato desejado, a habilidade retorna todos os dados disponíveis.

Neste exemplo, solicito que o Security Copilot use o plugin do Purview e recupere os dez alertas de DLP com gravidade alta nos últimos 30 dias:

```
Using the Purview plugin, get the last 10 DLP alerts with a severity of high over the past 30 days. Format the output in a table.
```
Posso baixar a saída da resposta selecionando **"Exportar para o Excel"** ou simplesmente exibi-la no navegador selecionando o ícone à direita do botão "Exportar para o Excel".

![Imagem](./images/001_module2_prompt_no_Markdown.png)


### Resumos, raciocínio e recomendações

Ao examinar esses alertas, percebo que alguns envolvem os mesmos usuários. Em vez de exibir cada alerta linha por linha em uma tabela e agrupá-los mentalmente, usarei a habilidade **/AskGPT**, como demonstrado no [Módulo 1 - Formatação com Markdown](https://github.com/Azure/Security-Copilot/tree/main/Technical%20Workshops/Markdown%20Workshop/Module%201%20-%20Formatting%20with%20markdown), para instruir o Security Copilot a:

- Resumir todos os dados, agrupados por usuário.
- Destacar tendências, comportamentos ou problemas significativos observados.
- Identificar padrões, semelhanças ou fatores contribuintes entre os alertas.
- Fornecer um resumo com recomendações acionáveis para mitigar riscos, priorizar incidentes e melhorar a conformidade.

```
/AskGPT For each user, write a concise, actionable summary addressed to their manager. Begin the summary with the user's User Principal Name (UPN). Highlight significant trends, behaviors, or issues observed in their DLP alerts using chain-of-thought reasoning to identify patterns, similarities, or contributing factors across the alerts. Provide clear, actionable recommendations to mitigate risk, prioritize incidents, and improve compliance.
```
![Imagem](./images/002_module2_summarize_reason_and_recommend.png)
### Criação de links com IDs de alerta

Satisfeito com a saída de resumo, raciocínio e recomendações, quero incluir links clicáveis para facilitar a exibição do alerta real. Embora a saída inicial não inclua um link clicável, ela contém a ID do alerta.

Como o Defender XDR, o Sentinel e o Purview usam formatos de URL padronizados, posso usar a ID do alerta para criar um link. O Purview usa especificamente o formato de URL a seguir, no qual `{my-Tenant-ID}` é substituído pela minha Tenant ID e `{Purview-alert-ID}` pela ID do alerta do Purview:
`https://purview.microsoft.com/datalossprevention/alertspage/fullpage?tid={my-Tenant-ID}&alertsviewid=overview&id={Purview-alert-ID}`.

A URL final será semelhante a esta:<br>
`https://purview.microsoft.com/datalossprevention/alertspage/fullpage?tid=0527ecb7-06fb-4769-b324-fd4a3bb865eb&alertsviewid=overview&id=da7618d0-35a6-71b8-3400-08dd5766cd5a`

Para criar um link, basta garantir que os dados necessários ao formato de URL estejam presentes na saída ou sejam fornecidos de outra maneira. Neste caso, a saída contém uma lista de alertas de DLP com suas respectivas IDs. Como minha Tenant ID está ausente, precisarei obtê-la. Há várias maneiras de fazer isso, mas a mais fácil é exibir as [propriedades do locatário no portal do Azure](https://portal.azure.com/#view/Microsoft_AAD_IAM/TenantProperties.ReactView).

Agora que tenho a Tenant ID, posso inserir esse valor diretamente na URL. Com base na minha experiência com o Defender XDR e o Purview, sei que as IDs de alerta associadas ao Purview começam com "dl", que precisarei remover para exibir esses alertas no portal do Purview.

Para gerar essa URL, usarei novamente a habilidade **/AskGPT** e solicitarei ao Security Copilot:
- Criar um link para os alertas.
- Usar a URL raiz que contém minha Tenant ID.
- Remover os dois primeiros caracteres da ID do alerta.

⚠️ Leia o próximo prompt antes de executá-lo e não se esqueça de inserir sua Tenant ID na URL antes de colar.

```
/AskGPT For each user include a direct link to the alert in Microsoft Purview portal using the following URL format:  
Purview: [{Alert Title}](https://purview.microsoft.com/datalossprevention/alertspage/fullpage?tid={Replace-with-your-tenant-ID-and-remove-curly-brackets}&alertsviewid=overview&id={alertId with the first two 'dl' characters of the AlertID removed})
```

⚠️ Se eu preferir trabalhar no Defender XDR em vez do Purview, posso manter os caracteres "dl" no início da ID do alerta e usar a URL do Defender XDR `https://security.microsoft.com/alerts/{alert ID}`, ajustando o prompt adequadamente. Para não confundir o LLM, escolherei o Purview ou o Defender XDR antes de colar o prompt.

```
/AskGPT For each user include a direct link to the alert in Defender XDR portal using the following URL format:  
[{Alert Title}](https://security.microsoft.com/alerts/{alert Id})
```

Se o prompt acima falhar, verifique se você atualizou a Tenant ID.

![Imagem](./images/003_module2_creating_links_from_alert_IDs.png)


### Garantia de formatação consistente

Embora eu valorize a natureza amigável, conversacional e não repetitiva da IA generativa, preciso que a saída tenha formatação consistente em todas as execuções. Para isso, fornecerei instruções claras que integrem meus prompts anteriores, as alterações de URL e diretrizes adicionais de formatação.

Como os LLMs funcionam melhor com delimitadores específicos e o Markdown é uma linguagem consolidada para esse fim, combinarei as [práticas recomendadas de engenharia de prompts do Security Copilot](https://learn.microsoft.com/en-us/copilot/security/prompting-tips) com as [práticas recomendadas gerais para prompts eficazes de LLMs](#general-best-practices-for-effective-prompting-llms) descritas no início desta página. Ao aproveitar esses dois recursos, além de usar o poder do Security Copilot, garantirei que a saída do raciocínio seja formatada de modo consistente sempre que executar este prompt.

```
Using the Purview plugin, get the last 10 DLP alerts with a severity of high. Assume the role of an expert **Data Loss Prevention (DLP) engineer** tasked with generating a **professional, manager-focused summary** of a DLP triage workflow for DLP alerts. 

- For **each user**, write a **concise, actionable summary** addressed to their manager.  
- Begin the summary with the user's **User Principal Name (UPN), Job Title, and Department** to establish context.  
- Highlight **significant trends, behaviors, or issues** observed in their **DLP alerts** using **chain-of-thought reasoning** to identify patterns, similarities, or contributing factors across the alerts.  
- Provide **clear, actionable recommendations** to mitigate risk, prioritize incidents, and improve compliance.
- Include a direct **link to the alert in Microsoft Purview** using the following URL format:   [{Alert Title}](https://purview.microsoft.com/datalossprevention/alertspage/fullpage?tid=0527ecb7-06fb-4769-b324-fd4a3bb865eb&alertsviewid=overview&id={alert Id} 
- Note that if the alert ID begins with 'dl' this portion of the alertId should be removed before creating the URL. Example: https://purview.microsoft.com/datalossprevention/alertspage/fullpage?tid=0527ecb7-06fb-4769-b324-fd4a3bb865eb&alertsviewid=overview&id=dlda7618d0-35a6-71b8-9200-08dd5767802a
...becomes...
https://purview.microsoft.com/datalossprevention/alertspage/fullpage?tid=0527ecb7-06fb-4769-b324-fd4a3bb865eb&alertsviewid=overview&id=da7618d0-35a6-71b8-9200-08dd5767802a

**Tone and Style:** Write in clear, professional, and manager-focused language, emphasizing risk, mitigation strategies, and actionable insights.

## Output format ##
**User**: {User Principal Name (UPN)}

**Summary:**  
{Concise, actionable summary of the DLP alerts for the user, highlighting significant trends, behaviors, or issues observed in their DLP alerts using chain-of-thought reasoning to identify patterns, similarities, or contributing factors across the alerts. Summary should be under 150 words.}

**Recommendations:**  
1. **Recommendation category**: {Any recommendation that supports mitigate risk, prioritize incidents, and improve compliance}
2. **Recommendation category**: {Any additional recommendations that supports mitigate risk, prioritize incidents, and improve compliance}
3. etc...

**Alert Links:**
- [Alert Title](Alert Link)
- [Alert Title](Alert Link)
---
```

![Imagem](./images/004_module2_final_prompt_with_Markdown.png)

---

### Uso de promptbooks

Para facilitar a repetição da execução deste prompt, criarei um promptbook. Os promptbooks podem armazenar vários prompts e oferecer suporte a fluxos de trabalho que permitem executar novamente um ou mais prompts posteriormente. Em prompts avançados como este, que incluem várias linhas de instruções e requisitos de formatação, usar um promptbook reduz a probabilidade de erros de digitação, economiza o tempo de copiar e colar prompts manualmente de uma biblioteca externa e permite compartilhá-los com outras pessoas da organização.

Para criar um promptbook em uma sessão, basta marcar a caixa no canto superior esquerdo do prompt e selecionar o ícone "Criar promptbook" na parte superior. No entanto, é importante observar que os promptbooks usam sinais de menor e maior `< >` para indicar variáveis. Portanto, eles devem ser usados somente em variáveis sem espaços.

![Imagem](./images/005_module2_promptbook_step_1.png)

Em seguida, fornecerei um nome, marcas relevantes (pressionando ENTER após cada marca) e uma descrição. Depois, passarei o mouse sobre a caixa de prompt e clicarei no ícone de lápis para editar o prompt.

![Imagem](./images/005_module2_promptbook_step_2.png)

Como nem sempre quero exatamente "10" alertas, transformarei esse número em uma variável, substituindo "10" por `<Number_of_DLP_alerts>` e colocando-o entre sinais de menor e maior (assim: `<Number_of_DLP_alerts>`). Depois, selecionarei o ícone de marca de seleção localizado onde estava o ícone de lápis.

![Imagem](./images/005_module2_promptbook_step_3.png)

Depois de rolar para baixo, posso ver que a variável foi aceita. Além disso, posso compartilhar o promptbook com outras pessoas nesta tela.

![Imagem](./images/005_module2_promptbook_step_4.png)

Por fim, salvarei o promptbook selecionando "Criar" no canto inferior esquerdo.

![Imagem](./images/005_module2_promptbook_step_5.png)

Agora posso exibir e executar o promptbook na tela inicial, filtrando por "Promptbooks", ou na biblioteca de promptbooks.

![Imagem](./images/005_module2_promptbook_step_6.png)
---

Para consultar a especificação oficial do Markdown, acesse o [CommonMark](https://commonmark.org/help/).