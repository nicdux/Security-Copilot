![Logotipo do Security Copilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)
# Investigação de usuário de risco do Entra

**Plugins necessários**: Microsoft Entra, Natural Language to KQL to Microsoft Defender XDR, Microsoft Defender XDR e Microsoft Defender Threat intelligence

**Entrada necessária**: UPN do usuário: <userupn> e nome de usuário: <Username>


**Descrição**: investigação de usuário de risco do Entra.

1. Gere um relatório usando o plugin do Entra para determinar se o usuário identificado por <userupn> é considerado de risco. Se o usuário for considerado de risco, forneça uma lista detalhada dos motivos dessa avaliação.
 ```
Generate a report based on Entra plugin, Is the user <userupn> considered risky? If yes, list the reasons.
 ```
2. Determine e liste os métodos de autenticação habilitados no momento para o usuário identificado por <userupn>.
 ```
What authentication methods are enabled for the user <userupn>?
 ```
3. Recupere e liste todas as tentativas de entrada realizadas pelo usuário identificado por <userupn> nos últimos 30 dias. Inclua os endereços IP correspondentes usados em cada tentativa.
 ```
Retrieve and list all login attempts made by the user within the past 30 days, along with the corresponding IP addresses used for each login attempt.
 ```
4. Use o MDTI para fornecer a reputação dos endereços IP ou nomes de host identificados nas tentativas de entrada do usuário <userupn>.
```
Provide the reputation of any IPs or hostnames found
```
5. Se algum endereço IP for encontrado nas tentativas de entrada do usuário <userupn>, use o Microsoft Defender Threat intelligence para validar a associação dele a agentes de ameaça conhecidos.
```
If any IP address is found, validate its association with any known Threat actor?
```
6. Liste todos os grupos dos quais o usuário identificado por <username> é membro.
```
List the groups user <username> is part of
```
7. Recomende etapas de correção para mitigar o risco associado ao usuário identificado por <userupn>.
```
Recommend remediation steps to mitigate the user risk
```
8. Gere um relatório executivo que resuma os insights sobre um usuário potencialmente de risco.
```
Generate an executive report summarizing insights on a potentially risky user. Commence with metadata details for the user, encompassing their User Principal Name (UPN), suspected country of origin, configured authentication method, and any recorded failed login attempts. Follow this with a bullet-point list outlining key areas requiring remediation to address the identified risks. Subsequently, craft a coherent paragraph elucidating mitigation strategies aimed at ameliorating the highlighted concerns
```
