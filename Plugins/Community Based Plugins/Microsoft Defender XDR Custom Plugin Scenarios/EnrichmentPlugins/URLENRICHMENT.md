# Conjunto de plugins de enriquecimento
**Autor: Craig Freyman**

## Plugin URLEnrichment
Este conjunto de habilidades de enriquecimento de URL foi desenvolvido para aprimorar investigações de segurança, fornecendo informações detalhadas sobre as interações dos usuários com URLs. Ele permite acompanhar cliques em URLs, analisar padrões de cliques e correlacionar atividades de URL com outros eventos de segurança para realizar avaliações abrangentes de risco.

### WhoClickedUrl
Identifica os usuários que clicaram em uma URL específica de um email em determinada data. Fornece detalhes como horário do clique, tipo de ação, informações do usuário e dados relacionados de rede ou ameaça para auxiliar na investigação de possíveis violações de segurança.

Prompt de exemplo: identifique os usuários que clicaram em https://example.com nos últimos 30 dias.

### UrlClickCount
Analisa a frequência e a atualidade dos cliques em uma URL específica nos últimos 30 dias. Fornece o número total de cliques e os carimbos de data/hora do primeiro e do último clique para apoiar a avaliação e a investigação de ameaças.

Prompt de exemplo: analise a frequência de cliques em https://example.com nos últimos 30 dias.

### UrlCorrelation
Correlaciona os cliques em uma URL específica com alertas de segurança, eventos de email e eventos de rede nos últimos 30 dias. Fornece uma visão geral abrangente do risco, incluindo horários dos eventos, usuários, alertas relacionados e IDs de incidentes associados.

Prompt de exemplo: correlacione a atividade da URL https://example.com com eventos de segurança relacionados nos últimos 30 dias.
