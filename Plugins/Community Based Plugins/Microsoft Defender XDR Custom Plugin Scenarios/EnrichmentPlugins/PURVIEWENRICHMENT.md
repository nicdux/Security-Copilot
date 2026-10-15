# Conjunto de plugins de enriquecimento
**Autor: Craig Freyman**

## Plugin PurviewEnrichment
Este conjunto de habilidades de enriquecimento do Purview foi desenvolvido para aprimorar investigações de segurança por meio da consulta de eventos de DLP e atividades de arquivos de usuários e dispositivos. Essas ferramentas ajudam os analistas de segurança a correlacionar alertas de prevenção contra perda de dados (DLP) com outros tipos de evento, auxiliando nos esforços de investigação e resposta.

### DLPGetlatestDlpalertperuser
Obtém os alertas de DLP mais recentes gerados por um usuário específico. Fornece informações sobre violações de política, tipos de informações confidenciais e ações de correção.

Prompt de exemplo: obtenha os alertas de DLP mais recentes do usuário "john.doe@example.com".

### DLPgetAllDlpalerts
Obtém todos os alertas de DLP para análise entre cargas de trabalho. Isso permite que as equipes de segurança identifiquem tendências, detectem possíveis ameaças e avaliem a eficácia das políticas.

Prompt de exemplo: obtenha todos os alertas de DLP dos últimos 30 dias.

### DLPgetalertbyPolicy
Obtém todos os alertas de DLP associados a uma política especificada. Ajuda os analistas de segurança a avaliar o impacto da política e ajustar as configurações.

Prompt de exemplo: obtenha os alertas de DLP da política "Confidential Data Policy".

### DLPgetFileactivity
Obtém detalhes da atividade de arquivos relacionada a violações de DLP, incluindo rótulos, informações confidenciais e ações de usuários associadas.

Prompt de exemplo: obtenha a atividade do arquivo "Confidential_Report.docx".

### DLPgetEndpointactivity
Obtém a atividade de arquivos confidenciais ocorrida em um dispositivo especificado. É útil para identificar acessos não autorizados a dados ou tentativas de exfiltração.

Prompt de exemplo: obtenha a atividade do ponto de extremidade do dispositivo "workstation-01".

### DLPgetSiteCollectionActivity
Obtém a atividade de coleções de sites ou bibliotecas do SharePoint relacionada a alertas de DLP. Ajuda a monitorar a movimentação de arquivos confidenciais e as tentativas de acesso não autorizado.

Prompt de exemplo: obtenha a atividade do SharePoint para a coleção de sites "HR-Confidential".
