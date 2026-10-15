# Conjunto de plugins de enriquecimento
**Autor: Craig Freyman**

## Plugin DeviceEnrichment
Este conjunto de habilidades de enriquecimento de dispositivos foi desenvolvido para aprimorar investigações de segurança, fornecendo informações sobre o comportamento dos dispositivos, vulnerabilidades e padrões de atividade. Com essas ferramentas, as equipes de segurança podem monitorar a exposição dos dispositivos, analisar eventos de entrada e identificar vulnerabilidades para correção direcionada.

### DeviceExposureLevel
Resume os níveis de exposição dos dispositivos no ambiente, identificando o número total de dispositivos de alto risco e de dispositivos de alto risco voltados para a Internet. Ajuda a priorizar os esforços de correção dos ativos críticos.

Prompt de exemplo: resuma os níveis de exposição de todos os dispositivos da rede.

### DeviceLogonSearch
Obtém um log detalhado dos eventos de entrada interativa e remota em dispositivos para uma conta e uma data específicas. Inclui ID e nome do dispositivo, carimbos de data/hora de entrada e nome da conta, auxiliando no acompanhamento da atividade do usuário e na identificação de dispositivos associados.

Prompt de exemplo: obtenha os eventos de entrada de jsmith em 2024-09-13.

### DeviceTimeline
Obtém e analisa uma linha do tempo detalhada de eventos do dispositivo e alertas de segurança próximos a um carimbo de data/hora específico. Inclui ações em arquivos, conexões de rede, atividades de processos e alertas relacionados para investigar comportamentos suspeitos e anomalias.

Prompt de exemplo: crie uma linha do tempo dos eventos do dispositivo laptop-win10v próximos a 2024-08-30T01:10:39.501000.

### DeviceCVESearch
Obtém uma lista de vulnerabilidades de software (CVEs) que afetam um dispositivo especificado, filtradas por nível de severidade (Critical, High, Medium ou Low). Fornece informações sobre fornecedores de software, impactos das vulnerabilidades e postura geral de segurança do dispositivo para ajudar a priorizar os esforços de correção.

Prompt de exemplo: liste as CVEs de some-host-name com nível de severidade High.

### CVEHostSearch
Obtém uma lista de dispositivos afetados por um identificador de CVE especificado. Fornece informações sobre o impacto da vulnerabilidade em cada dispositivo, destaca riscos críticos e avalia a postura geral de segurança para apoiar os esforços de correção em toda a rede.

Prompt de exemplo: encontre todos os dispositivos afetados pela CVE-2023-12345.

### DeviceDefenderSensorHealthReport
Analisa a integridade e o estado de configuração do sensor do Microsoft Defender em dispositivos Windows, macOS e Linux. Avalia recursos críticos de segurança, incluindo proteção contra adulteração, proteção em tempo real, proteção na nuvem e monitoramento de comportamento. Avalia os estados operacionais do Defender (Active, Passive e EDR Blocked) e o estado de conformidade.

Prompt de exemplo: obtenha o estado de integridade do sensor do Defender para device01.

### DefenderAvSignatureHealthReport
Avalia a atualidade das assinaturas de antivírus do Microsoft Defender e o estado da proteção em tempo real em dispositivos Windows, macOS e Linux. Identifica versões de assinatura desatualizadas, monitora as assinaturas mais recentes disponíveis e detecta dispositivos com proteção em tempo real inativa.

Prompt de exemplo: obtenha o relatório de integridade das assinaturas do Defender AV para todos os dispositivos.

### WindowsCriticalVulnerabilitiesReport
Avalia vulnerabilidades críticas em dispositivos Windows 10 e 11. Identifica os dispositivos de alto risco com as vulnerabilidades mais críticas, acompanha CVEs exploráveis e avalia vulnerabilidades de dia zero. Ajuda a priorizar os esforços de correção com base na severidade e na possibilidade de exploração.

Prompt de exemplo: liste os dez principais dispositivos Windows com vulnerabilidades críticas.

### ASRRuleTriggerCount
Analisa a frequência de acionamento das regras de redução da superfície de ataque (ASR) nos dispositivos. Identifica regras de alta frequência e ajuda as equipes de segurança a avaliar possíveis interrupções antes de habilitar as regras de ASR no modo de imposição.

Prompt de exemplo: mostre as regras de ASR acionadas com mais frequência em nosso ambiente.

### ASRBusinessHoursImpact
Analisa quando as regras de ASR são acionadas para avaliar o impacto operacional nos negócios. Compara os padrões de acionamento durante e fora do horário comercial e identifica as regras com maior impacto no horário comercial.

Prompt de exemplo: analise o impacto das regras de ASR durante o horário comercial.

### ASRImplementationPlan
Cria um plano de implementação em fases para as regras de ASR com base na avaliação de impacto. Calcula pontuações de impacto combinadas e classifica as regras em fases de impacto baixo, médio e alto para uma abordagem gradual de imposição.

Prompt de exemplo: crie um plano de implementação em fases para as regras de ASR.

### ASRPlatformCompatibility
Analisa a compatibilidade das regras de ASR com diferentes plataformas Windows. Cria uma matriz de compatibilidade que mostra quais regras são compatíveis com cada plataforma, evitando tentativas de imposição de regras sem suporte.

Prompt de exemplo: mostre a compatibilidade das regras de ASR em nossas plataformas Windows.

### ASRImpactByDevice
Analisa o acionamento das regras de ASR por dispositivo para determinar o impacto operacional. Identifica pontos de extremidade com risco de perder funcionalidades quando as regras de ASR forem impostas.

Prompt de exemplo: identifique os dispositivos mais afetados pelas regras de ASR.

### ASRRuleTrends
Acompanha como as regras de ASR são acionadas ao longo do tempo. Monitora a contagem diária de acionamentos e ajuda a avaliar se as regras estão se tornando mais ou menos impactantes.

Prompt de exemplo: mostre as tendências de acionamento das regras de ASR no último mês.

### ASRRuleApplicationMapping
Mapeia as regras de ASR para aplicativos específicos a fim de compreender o impacto nos negócios. Identifica quais aplicativos acionam regras específicas e ajuda a desenvolver estratégias de exclusão direcionadas para aplicativos essenciais aos negócios.

Prompt de exemplo: mapeie as regras de ASR para os aplicativos afetados por elas.

### ASRUserImpactAnalysis
Analisa o acionamento das regras de ASR por usuário para determinar o impacto operacional. Identifica departamentos com risco de interrupção do fluxo de trabalho e ajuda a planejar uma comunicação direcionada aos usuários antes da imposição.

Prompt de exemplo: analise quais usuários são mais afetados pelas regras de ASR.

### ASRExclusionCandidates
Identifica possíveis candidatos à exclusão de regras de ASR com base na frequência de acionamento. Cria formatos de caminho de exclusão prontos para uso a fim de minimizar interrupções durante a transição para o modo de imposição.

Prompt de exemplo: encontre candidatos à exclusão de regras de ASR.

### ASRProcessAnalysis
Analisa quais processos específicos estão acionando as regras de ASR. Fornece informações detalhadas sobre caminhos de processos, nomes de arquivos e linhas de comando para diferenciar softwares legítimos que precisam de exclusões de atividades potencialmente mal-intencionadas.

Prompt de exemplo: analise quais processos estão acionando as regras de ASR.