# Conjunto de plugins de enriquecimento
**Autor: Craig Freyman**

## Plugin EmailEnrichment
Este conjunto de habilidades de enriquecimento de email foi desenvolvido para aprimorar investigações de segurança, fornecendo informações detalhadas sobre atividades de email. Essas ferramentas permitem identificar interações de email com base em domínios, destinatários ou remetentes e investigar atividades relacionadas para uma análise abrangente de ameaças.

### DomainEmailSearch
Pesquisa na tabela `EmailEvents` emails que contenham um nome de domínio especificado. Fornece detalhes importantes, incluindo horário, remetente, destinatário, assunto, corpo e quantidade de anexos, para apoiar análises e investigações de ameaças.

Prompt de exemplo: identifique emails que contenham o domínio "example.com" nos últimos sete dias.

### RecipientEmailSearch
Pesquisa na tabela `EmailEvents` emails enviados a um destinatário específico. Fornece detalhes importantes, incluindo horário, remetente, destinatário, assunto, corpo e quantidade de anexos, para apoiar investigações de ameaças.

Prompt de exemplo: encontre todos os emails enviados para user@example.com nos últimos sete dias.

### SenderEmailSearch
Pesquisa na tabela `EmailEvents` emails enviados por um remetente específico. Fornece detalhes importantes, incluindo horário, remetente, destinatário, assunto, corpo e quantidade de anexos, para auxiliar na análise da atividade do remetente.

Prompt de exemplo: obtenha todos os emails enviados por admin@example.com na última semana.

### NetworkMessageIdEmailSearch
Pesquisa na tabela `EmailEvents` emails por um `NetworkMessageId` especificado. Fornece detalhes importantes do email, incluindo horário, remetente, destinatário e assunto. Essa habilidade ajuda os analistas de segurança a localizar mensagens específicas nas investigações, permitindo análises de ameaças e correções direcionadas.

Prompt de exemplo: obtenha os detalhes do email com NetworkMessageId "1d6ce5463-10b7-4c1e-e0a9-08dd529394bc".

### QuarantineRequestInsights
Analisa solicitações de quarentena de email e suas aprovações para compreender as ações dos usuários e os padrões de segurança de email. Obtém detalhes importantes para uma investigação completa.

Prompt de exemplo: analise solicitações e aprovações de quarentena para obter informações de segurança de email.
