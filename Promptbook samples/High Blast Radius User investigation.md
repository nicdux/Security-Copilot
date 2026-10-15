![Logotipo do Security Copilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)
# Investigação de usuário com alto raio de impacto

**Plugins necessários**: Investigate anomalous activities by high blast radius user (KQL personalizado), AbuseIPDB, Microsoft Intune, Cybersixgill Threat Intelligence e Rare Processes Launched as a Service (KQL personalizado)

**Entrada necessária**: nenhuma.


**Descrição**: este Promptbook investiga ou busca evidências de um possível comprometimento da identidade de usuários com alto raio de impacto.


1. Use a UEBA para recuperar uma lista de usuários com alto raio de impacto que realizaram atividades anômalas recentemente
 ```
show me users who have a high blast radius and have recently performed anomalous activities
 ```
2. Identifique o usuário com maior prioridade para uma investigação adicional e explique essa conclusão.
 ```
 Using Hunt for anomalous activities by high blast radius accounts plugin, which specific user from the above prompt should I focus on and why?

 ```
3. Obtenha dados de reputação do endereço IP público usado para realizar as atividades anômalas
 ```
Using AbuseIPDB, tell me about the IP address used by the user
 ```
4. Identifique os dispositivos gerenciados atribuídos ao usuário para aprofundar a investigação de atividades suspeitas que possam ter sido realizadas nesses dispositivos
```
what device is assigned to this user
```
5. Use o Cybersixgill Threat Intelligence para descobrir se a ID do usuário foi comprometida e está à venda na dark web ou na deep web.
```
According to Cybersixgill, tell whether this user's credentials have been compromised.
```
6. Determine o estado de conformidade com as políticas do dispositivo usado pelo usuário.
```
tell me about the compliance state of the managed device.
```
7. Verifique se algum processo suspeito foi executado recentemente no computador
```
have there been any rare processes executed on this device over the past 7 days ?
```
8. Obtenha um resumo final da investigação, reunindo os insights extraídos de todos os prompts anteriores e das diversas soluções de segurança
```
/AskGPT Summarize this investigation. Include a verdict whether threat hunting is required and why. If yes suggest specific, follow up actions.
```
