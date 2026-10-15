# Conjunto de plugins de enriquecimento
**Autor: Craig Freyman**

## Plugin IncidentEnrichment
Este conjunto de plugins de enriquecimento de incidentes foi desenvolvido para aprimorar investigações de segurança, fornecendo informações sobre alertas relacionados a incidentes. Essas ferramentas permitem correlacionar, obter e analisar com eficiência os alertas vinculados a incidentes específicos para realizar investigações direcionadas.

### AlertTitleToIncidentCorrelation
Obtém os alertas associados a um ID de incidente especificado e fornece uma visão geral dos títulos. Se mais de dez alertas forem encontrados, sugere refinar a pesquisa pelo nome do alerta, permitindo correlação eficiente e investigação direcionada.

Prompt de exemplo: correlacione os títulos dos alertas com o ID de incidente "1337" para refinar os resultados da pesquisa.

### IncidentAlertRetrieval
Obtém todos os alertas associados a um ID de incidente específico. Fornece detalhes abrangentes, incluindo carimbo de data/hora, ID exclusivo do alerta, nome e nível de severidade, para apoiar investigações aprofundadas de incidentes.

Prompt de exemplo: obtenha todos os alertas do incidente com ID "2807" para revisar a atividade relacionada.
