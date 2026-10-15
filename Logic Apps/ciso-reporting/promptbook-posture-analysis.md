# Prompts no Promptbook de análise de postura

Este Promptbook contém uma série de prompts de exemplo para relatar o status geral da postura de segurança da organização atual. Ele foi projetado para ser chamado pelo Logic App [CfS-SendPromptbookResultsByEmail](https://github.com/Azure/Security-Copilot/tree/main/Logic%20Apps/CfS-SendPromptbookResultsByEmail) e requer o plugin personalizado [CISO Posture Summary](https://github.com/Azure/Security-Copilot/blob/main/Logic%20Apps/ciso-reporting/ciso-posture-summary-man.yaml) como pré-requisito.

OBSERVAÇÃO: este Promptbook está em uma versão preliminar. Além de os prompts não estarem otimizados quanto ao consumo de capacidade computacional, o conteúdo ainda está bastante incompleto. Consulte [este artigo](https://www.linkedin.com/pulse/periodic-reporting-security-managers-cisos-using-stefano-pescosolido-fm80f/) para obter mais detalhes sobre como este Promptbook deve ser aprimorado.

## Prompt 1
```
Which threats should I focus on based on their exposure scores? For each returned threat, include a brief summary (no more that <WORDS_NUMBER> words), the Exposure Score, the Last Updated date, the number of related Alerts, the number of Misconfigured Devices and the number of Vulnerable Devices.
```

## Prompt 2
```
/GetSentinelSOCOptimizationRecommendations Is my Sentinel environment configured appropriately with reference to threat coverage and data utilization? Summarize the results in 3 paragraphs: Threat Coverage Recommendations (for each threat, show a bulleted list of: Threat Name, Recommended Action, Number of Active Detections, Number of Recommended Detections), Data Utilization Recommendations (for each table, show a bulleted list of: Table Name, Recommendations, Number of Suggested Rules) and Detection Tuning Recommendations (for each detection, show a bulleted list of: Detection ID, Recommended Action, Recommended Entities). For Data Utilization, show only the recommendations with 1 or more Suggested Rules
```

## Prompt 3
```
/CisoRecommendationsBySeverity List the top <NUMBER_OF_RECOMMENDATIONS> active Recommendations created in the last <NUMBER_OF_DAYS> days. For the input parameter named "csv_of_severities" specify the following word or words, each surrounded by double quotes, with only the first letter in uppercase and, if more than one, separated by commas: <SEVERITIES>
```


---

# Parâmetros do Logic App que chama o Promptbook de análise de postura e envia os resultados por email
(Modelo do Logic App: https://github.com/Azure/Security-Copilot/tree/main/Logic%20Apps/CfS-SendPromptbookResultsByEmail)


## Parâmetros relacionados às respostas do Promptbook


### Valor do parâmetro 'SkipPromptsInOutput' do Logic App
Índices dos prompts cujas respostas não devem ser incluídas no email enviado.
(Deixe vazio)
```
[]
```

### Valor do parâmetro 'ReplacePromptsInOutput' do Logic App
Texto a ser usado para substituir os prompts no email enviado.
OBSERVAÇÃO: ele pode incluir palavras e números que devem ser consistentes com os valores especificados nos parâmetros de entrada do Promptbook.<br>
```
["List the global threats that should be prioritized based on their exposure score and the vulnerabilities present in my environment.","List the recommendations for better coverage in our SIEM (Microsoft Sentinel) against the most impactful threats. Also, show the recommendations for better utilization of our collected logs.","List the top 10 high and medium severity recommendations based on the number of impacted resources in my cloud PaaS environments in Azure, AWS, and GCP."]
```


## Parâmetros relacionados à formatação HTML do email enviado


### Valor do parâmetro 'HtmlBodyHeader' do Logic App
(Tons de **verde**)
```
<!DOCTYPE html><html><style>.notification-table-header {padding: 10px;width: auto;border-top: none;background: #3B7D23;font-size: 11.0pt;color: white;font-weight: bold;margin-left: 10px;text-align: left;border: none;border-bottom: solid white 1.5pt;} .notification-table-text {padding: 10px;margin-left: 5px;width: 70%;text-align: left;border: none;border-bottom: solid white 1.5pt;background: #FAFAFA;font-size: 12.0pt;height: 20.05pt;} .notification-card-footer span {font-size: 12.0pt;color: #000000;} .notification-card-footer p {vertical-align: baseline;} .notification-body {margin: 0 auto;text-align: center;width: 650px;border: 1px black;border-collapse: collapse;background-color: #B4E5A3;} </style> <body style="background-color: #dfdfdf;"><table style="width:100%;"><tr><td style="padding:0;"><div align="center"><table class="notification-body"><tr style="border: 1px grey; border-top:none;"><td><p style='font-size:5.0pt;'><span>&nbsp;</span></p><table style='width:590px;margin:0 auto;border-collapse:collapse;
```

### Valor do parâmetro 'HtmlBodyRow' do Logic App
(Igual ao modelo do Logic App)
```
<tr><td class="notification-table-header"><span>***CONTENT1***</span></td></tr><tr><td class="notification-table-text"><span>***CONTENT2***</span></td></tr><tr class="notification-card-footer"><td><p style='text-indent:36.0pt;'><span style='font-size:10.0pt;'>&nbsp;</span></p></td></tr>
```


### Valor do parâmetro 'HtmlBodyRow' do Logic App
(Igual ao modelo do Logic App)
```
<tr class="notification-card-footer"><td><p style='text-align:center;'><span style='font-size:12.0pt; color:yellow;'>The content of this email was generated by Artificial Intelligence and may not be accurate. Please verify its accuracy..</span><br/><span style='font-size:12.0pt;'>To access Security Copilot, click <a href="https://security.microsoft.com/">HERE</a>.</span><br></p></td></tr></table></td></tr></table></div></td></tr></table></body></html>
```
