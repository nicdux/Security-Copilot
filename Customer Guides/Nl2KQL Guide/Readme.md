![Logotipo do Security CoPilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)
# Microsoft Security Copilot
## Recurso em destaque: gerar consultas de busca

### Introdução
**Busca avançada no Security Copilot**<br>
O Security Copilot agora conta com habilidades específicas que aproveitam os recursos de IA generativa do GPT-4 para raciocinar sobre um prompt em linguagem natural e gerar uma consulta KQL capaz de recuperar dados das tabelas de Busca Avançada do Microsoft Defender e das principais tabelas de dados do Microsoft Sentinel. Consulte a lista completa de tabelas compatíveis no [Apêndice](#appendix).<br>
Essa nova funcionalidade substitui uma implementação anterior por um algoritmo muito melhor e pelo acesso aos modelos mais recentes do Azure OpenAI. Estão em andamento pesquisas para estender a funcionalidade a outras tabelas de dados do Sentinel.

### Introdução
**Pré-requisitos**
1. Acesso ao Microsoft Security Copilot.
2. Acesso à Busca Avançada do Defender e ao Microsoft Sentinel com as mesmas credenciais usadas para acessar o Security Copilot.
3. Acesso aos recursos e às licenças necessários no Defender e no Sentinel para ativar todas as tabelas compatíveis.

**Ativação do conjunto de habilidades**
- Habilite “Natural language to Defender 365 KQL” e “Natural language to Sentinel KQL” no console de administração, em “Minhas conexões”.
- As habilidades NL2KQL podem ser selecionadas automaticamente pelo Security Copilot com base no seu prompt.
- Na caixa de prompt, digite “/kql” para selecionar explicitamente a habilidade antes de inserir um prompt.

### Cenários de casos de uso
Você pode iniciar a investigação a partir de um incidente e fazer perguntas complementares:
- Fale sobre o incidente [incidentID].
- Quais são os eventos de logon recentes do usuário presente no alerta?
- Mostre todos os logons recentes do AAD originados do endereço IP.
- O usuário entrou recentemente a partir de fora dos EUA?
- O usuário recebeu algum alerta?
- Quais outras entidades estão associadas a esse usuário?

Você também pode fazer perguntas como:
- Mostre uma lista dos cliques mais recentes em URLs.
- Encontre todos os usuários que clicaram em um link no último dia.
- Mostre os eventos de entrada recentes de [IPaddress].
- Informe o número de logons por usuário nas últimas 12 horas, agrupado por localização e em ordem decrescente.
- Existe um arquivo em minha organização com o nome [nome do arquivo, por exemplo, notepad.exe]?
- Forneça uma lista de dez vulnerabilidades críticas de software.

### Práticas recomendadas para escrever prompts que geram consultas de busca
**Diretrizes gerais** para escrever prompts que geram consultas de busca:
1. Não deixe ambiguidades: tente fazer perguntas com um assunto claro.
2. Faça uma pergunta por vez: sempre que possível, solicite uma única tarefa ou um único tipo de informação por vez.
3. Seja específico: se souber algo sobre os dados que procura, forneça essa informação na pergunta.
4. Use outras habilidades: você pode usar outras habilidades do Security Copilot para coletar informações que forneçam contexto útil ao escrever consultas de busca.

**Exemplos de diretrizes:**
| Ambíguo | Bom | Explicação |
| --- | --- | --- |
| Algum usuário entrou a partir de locais suspeitos na última semana? | Quais contas individuais apresentaram atividades de viagem suspeita ou impossível na última semana? | "Locais suspeitos" é subjetivo e pode gerar resultados menos consistentes. |
| Quais usuários tiveram mais tentativas de logon com falha nas últimas 72 horas? | Mostre os cinco usuários com mais tentativas de logon com falha em dispositivos locais nas últimas 72 horas. | O prompt melhor especifica o escopo (cinco usuários) e esclarece que procuramos logons em dispositivos locais, não na nuvem. |
| Atividade de rede de IPs suspeitos | Atividade de rede de endereços IP associados a proxies ou ao Tor conhecidos | Definir o que você considera suspeito quase sempre é melhor do que deixar o modelo decidir. |

### Comentários
Para nos ajudar a melhorar, é importante que você compartilhe seus comentários. Use os botões de comentários no produto para que possamos entender se o modelo gerou as consultas corretas para você.
- Se a consulta estiver correta e os resultados forem os esperados, selecione “Confirmar”.
- Se a habilidade LookupDataFromDefender365Hunting não estiver sendo usada corretamente, selecione “Fora do esperado”, conforme descrito acima.
- Se a habilidade for executada conforme o esperado, mas a consulta estiver incorreta, selecione “Fora do esperado”. Se possível, explique por que a consulta está incorreta e forneça um exemplo da consulta correta.
  - **Por exemplo:**<br>
    **Prompt em linguagem natural:** obtenha dispositivos com alto nível de exposição.<br>
    **Consulta gerada pelo modelo:**<br>
    ```
    DeviceRegistryEvents
    | where ActionType == "Create"
    | where InitiatingProcessIntegrityLevel == "High"
    | summarize count() by DeviceId, DeviceName
    ```  
    **Ao compartilhar seus comentários, informe que o resultado está fora do esperado e forneça um exemplo da consulta correta, além da categoria da falha.**
    ```
    KQL ground truth:
    DeviceInfo
    | summarize arg_max(Timestamp, *) by DeviceId
    | where ExposureLevel == "High"
    ```  
    **Categoria da falha:** tabela incorreta

### Apêndice
**Lista de tabelas compatíveis do Defender**<br>
Todas as tabelas da Busca Avançada do Defender são compatíveis com NL2KQL. Observe que as colunas AdditionalFields não são compatíveis.

**Lista de tabelas compatíveis do Sentinel**<br>
A habilidade ainda pode gerar consultas KQL para tabelas do Sentinel que não estão incluídas na lista abaixo. As consultas KQL geradas para essas tabelas representam a melhor tentativa possível e podem apresentar um nível de confiança menor.<br>
*Atualizado em 11/10*
- AADManagedIdentitySignInLogs
- AADNonInteractiveUserSignInLogs
- AADProvisioningLogs
- AADRiskyUsers
- AADServicePrincipalSignInLogs
- AADUserRiskEvents
- ABAPAuditLog_CL
- Anomalies
- AppDependencies
- AppTraces
- AuditLogs
- AWSCloudTrail
- AWSGuardDuty
- AzureActivity
- AzureDevOpsAuditing
- AzureDiagnostics
- AzureMetrics
- BehaviorAnalytics
- CommonSecurityLog
- ContainerInventory
- ContainerLog
- DnsEvents
- Dynamics365Activity
- Event
- Heartbeat
- IdentityInfo
- InsightsMetrics
- IntuneAuditLogs
- IntuneDevices
- LAQueryLogs
- MicrosoftAzureBastionAuditLogs
- MicrosoftPurviewInformationProtection
- OfficeActivity
- Perf
- PowerBIActivity
- ProtectionStatus
- SecurityAlert
- SecurityEvent
- SecurityIncident
- SecurityRecommendation
- SigninLogs
- SqlAtpStatus
- StorageBlobLogs
- StorageFileLogs
- Syslog
- ThreatIntelligenceIndicator
- Update
- UrlClickEvents
- Usage
- UserAccessAnalytics
- UserPeerAnalytics
- VMBoundPort
- VMComputer
- VMConnection
- VMProcess
- W3CIISLog
- WindowsEvent
- WindowsFirewall