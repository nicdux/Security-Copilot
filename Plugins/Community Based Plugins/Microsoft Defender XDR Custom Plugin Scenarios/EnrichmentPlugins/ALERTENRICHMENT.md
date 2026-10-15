# Conjunto de plugins de enriquecimento
**Autor: Craig Freyman**

## Plugin AlertEnrichment
Este conjunto de habilidades de enriquecimento de alertas foi desenvolvido para aprimorar investigações de segurança, fornecendo informações detalhadas sobre dados de alertas. Essas ferramentas permitem que os analistas identifiquem e examinem alertas com base nos títulos e obtenham evidências associadas a alertas específicos para uma investigação eficaz de ameaças.

### AlertTitleSearch
Pesquisa no banco de dados do Defender alertas cujo título contenha uma palavra-chave especificada. Retorna detalhes importantes do alerta, incluindo horário de geração, ID, título, categoria e severidade, para ajudar a identificar rapidamente alertas relevantes.

Prompt de exemplo: pesquise alertas que contenham "DLP policy" nos títulos nos últimos sete dias.

### AlertEvidenceSearch
Obtém evidências detalhadas associadas a um alerta específico usando seu `AlertId`. Fornece informações sobre o tipo de entidade, URLs associadas, informações da conta, metadados de email, detalhes do arquivo e outras informações contextuais para auxiliar nas investigações.

Prompt de exemplo: obtenha evidências do alerta com ID "dl3e6607b8-8ff6-7180-d400-08dcf2ab98ff".
