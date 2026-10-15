
### Plugin personalizado de detecção de atividades anômalas de rede (CEF)

Boas-vindas ao plugin personalizado de detecção de atividades anômalas de rede (CEF)! Aqui você encontrará habilidades que pesquisam eventos de atividades anômalas nos dados CEF de rede da tabela CommonSecurityLog do Sentinel.

#### Recursos:

- StartTime:
            Description: define em startTime a quantidade de dias do período retrospectivo para a detecção de atividades anômalas de rede (CEF) no Microsoft Sentinel
            Required: true
            DefaultValue: 21d
- EndTime:
            Description: define em endTime a quantidade de dias do período retrospectivo para a detecção de atividades anômalas de rede (CEF) no Microsoft Sentinel
            Required: true
            DefaultValue: 0d
