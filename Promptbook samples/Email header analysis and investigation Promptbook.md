![Logotipo do Security Copilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)
# Análise de cabeçalho de e-mail

**Plugins necessários**: Microsoft Defender Threat intelligence, Natural Language to KQL to Microsoft Defender XDR, Microsoft Defender XDR

**Entrada necessária**: < Emailheaders >


**Descrição**: investigue um e-mail suspeito examinando os cabeçalhos, filtrando as entidades e concluindo com um resumo do e-mail.

1. Faça a triagem do e-mail
 ```
Can you triage the email header below and point out what you find suspicious? <emailheaders>
 ```
2. Identifique indicadores técnicos no cabeçalho do e-mail
 ```
Can you list all the Technical indicators in the above prompt that we can use for an investigation process
 ```
3. Identifique os domínios associados ao e-mail e a inteligência contra ameaças relacionada a eles
 ```
Return the reputation for all the domains in the list
 ```
4. Identifique os IPs associados ao e-mail e a inteligência contra ameaças relacionada a eles
```
Return the reputation for all the IP addresses in the list
```
5. Identifique se as entidades associadas aparecem em artigos sobre ameaças
```
Can you check if there any threat articles associated with any of the Domains or IPS from the list above
```
6. Identifique se as entidades associadas ao remetente e ao caminho de retorno aparecem em artigos sobre ameaças
```
What about the sender and return path emails are they associated with any intelligence articles
```
7. Use a busca do Defender para verificar se outras pessoas na organização receberam o e-mail
```
/LookupDataFromDefender365Hunting Based on the email title check if this email sent to other users?
```
8. Use a busca do Defender para verificar se alguém na organização clicou em alguma URL associada ao e-mail
```
Hunt my environment and determine if any of the users clicked any URL in the email above
```
9. Resuma a investigação e indique o grau de certeza quanto aos elementos suspeitos
```
Based on the above email investigation, summarize this investigation with all the investigation steps taken during this session. Also share supported evidence and let me know if this is a phishing email with certainty percentage: if the email is not suspicious give it 0-30% if it medium suspicious for phishing give it 30%-74% and if its high suspicious as phishing give it 75%-100%. Always include suspicious certainty percentage.
