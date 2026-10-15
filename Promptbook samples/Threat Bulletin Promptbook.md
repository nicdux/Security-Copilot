![Logotipo do Security Copilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)
# Promptbook de boletins de ameaças

**Descrição**: resuma os artigos recentes sobre ameaças em formato de relatório, com recomendações práticas para um determinado período.

**Plugin necessário**: Defender Threat intelligence

**Entrada necessária**: < Lookfarback >

1. Solicite informações sobre os artigos mais recentes a respeito de ameaças
 ```
Share the latest Threat articles published in the last <Lookfarback> in a table format
 ```
2. Verifique se há CVEs mencionadas no artigo e quais tecnologias estão associadas
 ```
If there is any CVEs sighted in these articles , please provide a summary of these CVEs and cite the technologies impacted
```
3. Resuma os artigos em formato de relatório, incluindo itens de ação
 ```
Summarize the following articles and consolidate them in a Threat Bulletin format Named Threat bulletin with the current date . In the bulletin ensure to capture all details including the title summary , link , Created date , also highlight the action items the Team should prioritize in relation to these article
 ```
