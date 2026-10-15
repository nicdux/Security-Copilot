![Logotipo do Security Copilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)

# Aceleração da detecção de entradas anômalas com o Microsoft Entra ID e o Security Copilot

No complexo cenário de ameaças atual, a proteção de identidades é essencial para proteger os ativos organizacionais. Um sinal comum de comprometimento é a atividade de um usuário que indica conexões, em um curto período, a partir de vários locais separados por mais de X quilômetros. Esses eventos podem representar entradas arriscadas, exigindo que analistas de segurança determinem se são verdadeiros positivos (indicando atividade mal-intencionada) ou falsos positivos (como configurações incorretas ou anomalias benignas).

Para aumentar a eficiência e acelerar o processo de investigação, as organizações podem usar ferramentas de IA como o Microsoft Security Copilot. Ao integrar o Security Copilot ao Microsoft Entra ID, principalmente ao AADUserRiskEvent, e desenvolver Promptbooks personalizados, as organizações podem investigar entradas arriscadas, reduzir o trabalho manual e viabilizar decisões proativas que aumentam a eficiência do SOC nesses cenários.

Aviso de isenção de responsabilidade: estes prompts são apenas exemplos e estão sujeitos a alterações.




**Plugins necessários**: Microsoft Defender XDR, Public Web

**Entrada necessária**: <TimeIntervalByDays>

**Entrada necessária**: <ConnectionsInterbalByHrs>

**Entrada necessária**: <SepratedDistanceByKM>

**Descrição**: as organizações enfrentam desafios significativos para investigar e fazer a triagem de alertas de proteção de identidade relacionados a anomalias de entrada, especialmente quando os usuários parecem entrar, em um intervalo de poucas horas, a partir de locais geograficamente distantes. Esses desafios incluem:

- Volume de alertas: grandes organizações geram diariamente muitos eventos de entrada arriscada.
- Falsos positivos: atividades legítimas, como conexões VPN ou mudanças de localização de dispositivos, podem ser sinalizadas.
- Restrições de recursos: as equipes de segurança precisam priorizar com eficiência os verdadeiros positivos que serão investigados.

Com o Microsoft Security Copilot e um Promptbook personalizado, analistas de segurança podem automatizar o processo inicial de triagem e se concentrar em insights relevantes. Essa abordagem combina consulta de dados, análise orientada por IA e recomendações práticas para melhorar os fluxos de trabalho de investigação.

1. Primeiro prompt: recuperação de dados do Defender XDR por meio de uma consulta KQL
 ```
 Retrieve Defender XDR information using this KQL query: let riskyusers = AADUserRiskEvents | where TimeGenerated is greater than or equal ago(<TimeIntervalByDays>) | project UserPrincipalName, TimeGenerated, Location, IpAddress, RiskState, Id, RiskEventType; riskyusers | join kind=inner ( riskyusers | extend TimeGenerated1 = TimeGenerated, LocationDetails1 = Location ) on UserPrincipalName | where TimeGenerated is less than TimeGenerated1 and datetime_diff('hour', TimeGenerated1, TimeGenerated) is less than or equal <ConnectionsInterbalByHrs> | extend latyy = Location.geoCoordinates.latitude | extend longy= Location.geoCoordinates.longitude | extend latyy1 = LocationDetails1.geoCoordinates.latitude | extend longy1 = LocationDetails1.geoCoordinates.longitude | extend distance = geo_distance_2points(todouble(Location.geoCoordinates.latitude), todouble(Location.geoCoordinates.longitude), todouble(LocationDetails1.geoCoordinates.latitude), todouble(LocationDetails1.geoCoordinates.longitude)) | where distance is greater than or equal <SepratedDistanceByKM> | summarize arg_max(TimeGenerated, *) by Id | where RiskState is not equal @"dismissed" | project UserPrincipalName, TimeGenerated, IpAddress, Location, TimeGenerated1, IpAddress1, LocationDetails1, RiskEventType, distance
 ```
2. Segundo prompt: análise de padrões e recomendações com IA
 ```
/AnalyzeSecurityData Provide your insights as Security Analyst about what anomalies or similarity patterns can you identify. Provide a list of prompts for Security Copilot to investigate further and a list of recommendations. Use as input security data the information in the table from the previous prompt in this session.
 ```