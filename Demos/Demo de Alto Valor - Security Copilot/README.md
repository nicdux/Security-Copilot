# DEMO DE ALTO VALOR — MICROSOFT SECURITY COPILOT

## Teleprompter completo, prompts e testes — 90 minutos

> Este é o único arquivo que precisa ficar aberto durante a apresentação.
> Cada bloco informa o que dizer, o que fazer, o que copiar e como reagir se
> algo falhar.

## Navegação rápida

- [Abertura e descoberta](#3-abertura-e-descoberta--00000008)
- [Valor e modelo operacional](#4-valor-e-modelo-operacional--00080018)
- [Plataforma e ecossistema](#5-plataforma-e-ecossistema--00180028)
- [Demonstração ao vivo](#6-demonstração-ao-vivo--00280105)
  - [Ato 1 — Pulso real do Defender](#ato-1--pulso-real-do-defender--00280035)
  - [Ato 2 — Investigação transversal](#ato-2--investigação-transversal--00350047)
  - [Ato 3 — Hunting e KQL](#ato-3--hunting-e-kql--00470054)
  - [Ato 4 — Decisão e revisão humana](#ato-4--decisão-e-revisão-humana--00540100)
  - [Ato 5 — Fluxo reutilizável](#ato-5--da-sessão-ao-fluxo-reutilizável--01000105)
- [Playbook institucional](#7-playbook-institucional--01050113)
- [Segurança e uso responsável](#8-segurança-e-uso-responsável--01130120)
- [Piloto e métricas](#9-piloto-e-métricas--01200125)
- [Fechamento e perguntas](#10-fechamento-e-qa--01250130)

## Como ler este roteiro

| Marcador | O que significa |
|---|---|
| 🎯 **Objetivo** | O resultado que este bloco deve produzir |
| 💼 **Valor para o cliente** | Por que o cenário importa para a operação |
| 🧠 **O que significa** | Como interpretar o conceito ou a consulta |
| 🗣️ **Dizer** | Fala sugerida para o cliente |
| ▶️ **Fazer** | Ação na tela |
| 📋 **Copiar e colar** | Prompt completo; use o botão de cópia do GitHub |
| ✅ **Validar** | Pontos que precisam aparecer no resultado |
| ⚠️ **Não concluir** | Limites e interpretações incorretas a evitar |
| ➡️ **Transição** | Frase que conecta este bloco ao próximo |

> **Dica:** no GitHub, cada bloco de código possui um botão de cópia no canto
> superior direito. Copie apenas os blocos sob o título **📋 Copiar e colar**.

---

# 1. REGRAS DE SEGURANÇA E CONTROLE

## Antes de compartilhar a tela

- Use uma janela limpa ou InPrivate.
- Compartilhe somente a janela do navegador.
- Feche abas, favoritos, notificações e informações de conta.
- Não mostre nomes de tenants, workspaces, usuários ou dispositivos.
- Não mostre IPs, URLs, hashes ou incidentes reais.
- Não mostre contagens reais do ambiente de demonstração sem aprovação.
- Não apresente recurso Preview como disponibilidade geral.
- Se uma resposta demorar mais de 45 segundos, use o resultado salvo e avance.
- Se o Embedded Copilot mostrar erro de capacidade, use imediatamente o portal
  standalone já validado. Não depure capacidade durante a apresentação.

## Frase de proteção

> “Os dados do cenário principal são sintéticos. Quando usamos telemetria real,
> as consultas são agregadas, somente leitura e não exibem entidades.”

---

# 2. AGENDA — 90 MINUTOS

| Horário | Bloco | Duração |
|---|---|---:|
| 00:00–00:08 | Missão, prioridades e descoberta | 8 min |
| 00:08–00:18 | Do volume de sinais à decisão | 10 min |
| 00:18–00:28 | Plataforma, integrações, promptbooks e agentes | 10 min |
| 00:28–01:05 | Demonstração ao vivo | 37 min |
| 01:05–01:13 | Playbook institucional | 8 min |
| 01:13–01:20 | Segurança, dados e IA responsável | 7 min |
| 01:20–01:25 | Piloto e métricas | 5 min |
| 01:25–01:30 | Perguntas e próximos passos | 5 min |

**Total: 90 minutos.**

---

# 3. ABERTURA E DESCOBERTA — 00:00–00:08

## DIZER

> “Hoje não vamos avaliar a IA pelo tamanho da resposta. Vamos avaliá-la pela
> capacidade de conectar evidência, decisão e governança em um ambiente de
> missão crítica.”

> “O Security Copilot deve ser visto como uma camada de aceleração do processo,
> não como um chat genérico e não como substituto do profissional.”

## PERGUNTAR

> “Onde o tempo especializado é mais consumido hoje: coletar contexto,
> investigar, decidir, comunicar ou repetir o processo em escala?”

> “Qual decisão de segurança precisa chegar mais rápido à liderança sem perder
> evidência e rastreabilidade?”

## ANOTAR

- Etapa com maior atrito:
- Caso de uso citado:
- Audiência mais importante:

---

# 4. VALOR E MODELO OPERACIONAL — 00:08–00:18

## DIZER

> “O valor aparece quando reduzimos alternância entre portais, padronizamos o
> raciocínio, democratizamos consultas e adaptamos a mesma evidência para
> diferentes audiências.”

> “O ciclo é simples: perguntar, fundamentar, revisar e agir. A ação só acontece
> dentro das permissões e do processo de aprovação da organização.”

## EXPLICAR

- **Prompt:** tarefa em linguagem natural.
- **Plugin:** acesso controlado a uma fonte ou capacidade.
- **Promptbook:** sequência reutilizável de prompts.
- **Agente:** fluxo orientado a objetivo, com ferramentas e permissões.

---

# 5. PLATAFORMA E ECOSSISTEMA — 00:18–00:28

## DIZER

> “Defender, Sentinel, Entra, Intune, Purview e Threat Intelligence continuam
> com seus próprios controles. O Copilot consulta em nome do usuário e não deve
> ultrapassar o RBAC existente.”

> “Promptbooks e agentes são importantes porque transformam uma boa interação
> em um método reutilizável.”

## STATUS DE NOVIDADES

### Disponibilidade geral

- Copilot no Microsoft Entra.
- Copilot no Microsoft Intune.
- Integração do Sentinel data lake.
- Auditoria de administração de agentes no Purview.

### Versão prévia

- Security Analyst Agent.
- Criação de agentes personalizados.
- Microsoft Security Store.
- Sentinel graph e servidor MCP.

## DIZER

> “Preview inspira a visão de futuro. Produção exige validação de
> disponibilidade, risco, suporte e conformidade.”

---

# 6. DEMONSTRAÇÃO AO VIVO — 00:28–01:05

## Estrutura

| Ato | Tempo | Pergunta que respondemos | Prova de valor |
|---|---:|---|---|
| Pulso real do Defender | 7 min | O Copilot acessa e entende o ambiente? | Embedded + telemetria agregada |
| Investigação transversal | 12 min | Ele conecta sinais de domínios diferentes? | Fatos, hipóteses, confiança e lacunas |
| Hunting e KQL | 7 min | Ele transforma suspeita em busca verificável? | Hipótese, telemetria e consulta explicada |
| Decisão e revisão humana | 6 min | Ele comunica sem substituir julgamento? | Resumo executivo + proporcionalidade |
| Fluxo reutilizável | 5 min | Como escalar além de uma conversa? | Promptbook, plugin, agente e gates |

## Resultado narrativo esperado

Ao final da demo ao vivo, o cliente deve conseguir repetir esta frase:

> “O Security Copilot conecta-se ao ambiente, organiza uma investigação,
> transforma hipóteses em consultas, adapta a comunicação e permite padronizar
> o processo sem retirar o controle humano.”

---

## ATO 1 — PULSO REAL DO DEFENDER — 00:28–00:35

### 🎯 Objetivo

Provar, logo no início da parte prática, que o Security Copilot:

1. está conectado ao ambiente;
2. respeita o contexto e as permissões do analista;
3. consegue resumir um incidente no fluxo de trabalho;
4. consulta telemetria real sem precisar expor entidades sensíveis.

### 💼 Valor para o cliente

Este ato responde à pergunta:

> **“O produto consegue trabalhar com o meu ambiente real e reduzir o tempo
> gasto para entender o que está acontecendo?”**

O valor não está em mostrar uma grande quantidade de eventos. Está em:

- reduzir a troca entre telas;
- produzir uma primeira leitura consistente;
- acelerar a passagem de dado técnico para contexto;
- manter o analista responsável pela conclusão e pelas ações.

### 🧭 Escolha do caminho

| Se... | Use... | Por quê |
|---|---|---|
| O Incident assistant está funcionando | **Embedded no Defender** | É a prova de valor mais direta |
| Você pode mostrar somente agregados | **Teste A — eventos de rede** | Prova conexão sem expor entidades |
| A audiência quer postura e exposição | **Teste B — vulnerabilidades** | Mostra priorização baseada em exposição |
| A audiência quer operação do SOC | **Teste C — alertas** | Mostra concentração de alertas |

Execute o Embedded e, no máximo, **uma** consulta agregada. Não transforme o
bloco em uma exploração de tabelas.

### ▶️ Configurar fontes

- Criar sessão separada.
- Habilitar somente Microsoft Defender XDR.
- Desabilitar Public web.
- Não usar o plugin personalizado.

### 🗣️ Dizer

> “Começamos com uma prova concreta: conexão com telemetria real do ambiente,
> usando uma experiência incorporada e consultas agregadas somente leitura.”

## OPÇÃO RECOMENDADA — COPILOT EMBEDDED NO DEFENDER

Use somente um incidente previamente autorizado para demonstração.

### 🧠 O que significa

O Security Copilot Embedded recebe automaticamente o contexto do incidente
aberto no Defender. O analista não precisa copiar o ID, reconstruir a linha do
tempo ou alternar para outro portal antes de pedir uma síntese.

O resumo:

- organiza alertas, entidades e evidências;
- reduz o tempo para a primeira avaliação;
- não substitui a leitura das fontes;
- não muda o incidente até que alguém execute uma ação autorizada.

### ▶️ Mostrar

- O incidente no Microsoft Defender.
- O painel **Incident assistant**.
- O **Incident summary** gerado.
- A seção de triagem e recomendações, sem executar ações.

### 🗣️ Dizer

> “Aqui o Copilot está incorporado ao fluxo de trabalho do analista. Ele recebe
> o contexto do incidente sem exigir troca de portal e produz um resumo
> fundamentado para acelerar a primeira avaliação.”

> “Continuamos dentro das permissões do usuário e da capacidade associada ao
> workspace. O resumo apoia a decisão; ele não executa remediação por conta
> própria.”

### ✅ Validar com o cliente

- O resumo identifica o evento principal?
- Ele separa evidência de recomendação?
- A linha do tempo está coerente?
- As lacunas ou limitações estão visíveis?
- Um analista conseguiria decidir o próximo passo mais rapidamente?

### ⚠️ Não clicar

- **Remediate**.
- **Contact user in Teams**.
- **Resolve and export incident**.
- Qualquer ação que altere status, atribuição ou classificação.

### ⚠️ Não concluir

- O resumo não comprova comprometimento.
- Uma recomendação não equivale a uma ação aprovada.
- Ausência de alerta adicional não significa ausência de atividade maliciosa.

### Plano B

Se o Embedded apresentar erro ou demorar mais de 45 segundos, feche o painel e
continue com o teste agregado abaixo ou com o portal standalone.

## TESTE A — EVENTOS DE REDE — VALIDADO

### 🎯 Objetivo

Confirmar que existe telemetria recente do Defender for Endpoint e mostrar,
sem revelar dispositivos ou endereços, quais **tipos de eventos de rede**
aparecem com maior frequência.

### 💼 Por que fazemos esta consulta

Antes de investigar um caso específico, o analista precisa saber se a fonte
está ativa e produzindo dados. Esta consulta funciona como um “pulso”:

- comprova ingestão recente;
- demonstra Advanced Hunting;
- preserva privacidade por usar somente agregações;
- cria uma ponte entre linguagem natural e KQL.

### 🧠 O que a consulta faz

| Linha | Significado |
|---|---|
| `DeviceNetworkEvents` | Usa a tabela de conexões e eventos de rede dos endpoints |
| `where Timestamp >= ago(7d)` | Limita a análise aos últimos sete dias |
| `summarize ... by ActionType` | Conta eventos por tipo de ação, sem retornar entidades |
| `top 5` | Mantém somente os cinco tipos mais frequentes |
| `order by` | Organiza o maior volume primeiro |

### ⚠️ O que o resultado não significa

- Mais eventos não significam mais risco.
- `ConnectionSuccess` não significa atividade maliciosa.
- Uma contagem não informa impacto, intenção ou criticidade.
- Eventos agregados não substituem investigação.

### 📋 Copiar e colar

````text
Use exclusivamente o plug-in Microsoft Defender XDR para executar exatamente a consulta KQL somente leitura abaixo.

Não modifique a consulta, não acrescente outras tabelas, não use a web pública e não exiba registros individuais.

```kusto
DeviceNetworkEvents
| where Timestamp >= ago(7d)
| summarize QuantidadeEventos = count() by ActionType
| top 5 by QuantidadeEventos desc
| order by QuantidadeEventos desc
```

Apresente somente uma tabela com:
- tipo de ação;
- quantidade agregada de eventos;
- período analisado.

Depois da tabela, explique em no máximo três frases:
- que o resultado confirma telemetria recente do Defender for Endpoint;
- que as contagens representam eventos, não incidentes confirmados;
- que uma investigação precisa de contexto e validação adicional.

Não use placeholders. Não execute ações de escrita ou remediação. Responda em português do Brasil.
````

### ✅ Validar

- A tabela retornou até cinco tipos de ação.
- O período analisado é de sete dias.
- Nenhum dispositivo, usuário, IP ou URL foi exibido.
- O texto final esclarece que eventos não são incidentes.

### 🗣️ Dizer

> “Contagem é sinal, não veredito. Volume não substitui impacto, contexto ou
> validação.”

> “Esta consulta não procura um ataque. Ela confirma que a fonte está viva e
> nos mostra onde existe volume para uma investigação posterior.”

### ➡️ Transição

> “Já comprovamos acesso à telemetria. Agora vamos mudar de volume para
> exposição: onde existem vulnerabilidades associadas aos ativos?”

## TESTE B — VULNERABILIDADES AGREGADAS — TESTAR ANTES

### 🎯 Objetivo

Mostrar a postura de vulnerabilidades por severidade, sem revelar dispositivo,
software, versão ou CVE.

### 💼 Por que fazemos esta consulta

Para uma liderança, uma lista extensa de CVEs não ajuda a decidir. A primeira
pergunta é: **qual é a distribuição da exposição e quantos ativos estão
envolvidos?**

Esta consulta demonstra como o Copilot pode ajudar a:

- resumir postura;
- preparar priorização;
- separar exposição de exploração;
- orientar uma conversa entre segurança, infraestrutura e negócio.

### 🧠 O que a consulta faz

| Trecho | Significado |
|---|---|
| `DeviceTvmSoftwareVulnerabilities` | Usa vulnerabilidades realmente associadas a dispositivos do tenant |
| `dcount(DeviceId)` | Conta dispositivos distintos afetados |
| `dcount(CveId)` | Conta vulnerabilidades distintas |
| `by VulnerabilitySeverityLevel` | Agrupa por criticidade |
| `case(...)` | Cria uma ordem numérica para severidade |
| `project-away` | Remove a coluna auxiliar antes de apresentar |

> **Importante:** não usar `DeviceTvmSoftwareVulnerabilitiesKB` para afirmar
> exposição do tenant. A tabela `KB` é uma base de conhecimento de referência.

### ⚠️ O que o resultado não significa

- Vulnerabilidade observada não significa exploração.
- Severidade alta não define sozinha a prioridade.
- Um ativo crítico pode exigir prioridade mesmo com menor volume.
- Exploitabilidade, exposição externa e controles compensatórios importam.

### 📋 Copiar e colar

````text
Use exclusivamente o plug-in Microsoft Defender XDR para executar exatamente a consulta KQL somente leitura abaixo.

Não modifique a consulta, não use a web pública e não exiba dispositivos, nomes de software, versões, CVEs ou outros registros individuais.

```kusto
DeviceTvmSoftwareVulnerabilities
| summarize
    DispositivosAfetados = dcount(DeviceId),
    VulnerabilidadesDistintas = dcount(CveId)
    by VulnerabilitySeverityLevel
| extend OrdemSeveridade = case(
    VulnerabilitySeverityLevel == "Critical", 4,
    VulnerabilitySeverityLevel == "High", 3,
    VulnerabilitySeverityLevel == "Medium", 2,
    VulnerabilitySeverityLevel == "Low", 1,
    0)
| order by OrdemSeveridade desc
| project-away OrdemSeveridade
```

Apresente somente uma tabela agregada por severidade.

Depois da tabela, explique em no máximo três frases:
- que os resultados representam exposição observada, não exploração confirmada;
- que priorização deve considerar criticidade do ativo, exploitabilidade e controles compensatórios;
- que nenhuma ação deve ser tomada sem validação.

Não use placeholders. Não execute ações de escrita ou remediação. Responda em português do Brasil.
````

### ✅ Validar

- O resultado está agregado por severidade.
- Não aparecem nomes de dispositivos, software ou CVEs.
- A resposta diferencia exposição de exploração.
- A recomendação exige validação antes de ação.

### 🗣️ Dizer

> “Estamos reduzindo milhares de relações técnicas a uma visão de exposição.
> O próximo passo não é corrigir tudo; é combinar severidade com criticidade do
> ativo, exploitabilidade e impacto.”

### ➡️ Transição

> “Postura mostra onde podemos estar expostos. Alertas mostram onde os controles
> já observaram comportamento que merece análise.”

## TESTE C — ALERTAS AGREGADOS — ALTERNATIVA

### 🎯 Objetivo

Mostrar onde o volume de alertas se concentra por severidade e categoria, sem
abrir qualquer alerta individual.

### 💼 Por que fazemos esta consulta

Um SOC não prioriza apenas pelo total de alertas. A combinação entre categoria
e severidade ajuda a entender:

- quais famílias de detecção geram mais trabalho;
- onde pode existir ruído;
- quais áreas merecem tuning ou investigação;
- como orientar capacidade operacional.

### 🧠 O que a consulta faz

| Linha | Significado |
|---|---|
| `AlertInfo` | Usa metadados de alertas do Defender XDR |
| `where Timestamp >= ago(7d)` | Analisa uma janela recente e comparável |
| `summarize ... by Severity, Category` | Conta alertas por severidade e categoria |
| `top 8` | Exibe somente as maiores concentrações |
| `order by` | Ordena pelo maior volume |

### ⚠️ O que o resultado não significa

- Maior volume não equivale ao maior risco.
- Alertas podem ser duplicados, correlacionados ou falsos positivos.
- Prioridade exige ativos, usuários, evidências e impacto.
- Esta visão mede carga; não encerra a triagem.

### 📋 Copiar e colar

````text
Use exclusivamente o plug-in Microsoft Defender XDR para executar exatamente a consulta KQL somente leitura abaixo.

Não modifique a consulta, não use a web pública e não exiba incidentes, dispositivos, usuários, endereços IP, URLs, hashes ou outros registros individuais.

```kusto
AlertInfo
| where Timestamp >= ago(7d)
| summarize QuantidadeAlertas = count() by Severity, Category
| top 8 by QuantidadeAlertas desc
| order by QuantidadeAlertas desc
```

Apresente somente uma tabela com:
- severidade;
- categoria;
- quantidade agregada de alertas;
- período analisado.

Depois da tabela, explique em no máximo três frases:
- quais combinações concentram maior volume;
- que volume não equivale automaticamente a risco ou prioridade;
- que priorização exige impacto, entidades, contexto e validação humana.

Não use placeholders. Não execute ações de escrita ou remediação. Responda em português do Brasil.
````

### ✅ Validar

- A tabela apresenta severidade, categoria, quantidade e período.
- Nenhuma entidade de alerta foi exibida.
- A explicação afirma que volume não é prioridade.

### 🗣️ Dizer

> “Esta visão mostra carga operacional. Para transformar carga em prioridade,
> precisamos adicionar impacto, criticidade e contexto — exatamente o que
> faremos no próximo ato.”

### Regra de tempo

- Mostrar o Embedded e executar no máximo **uma** consulta agregada.
- Se um teste falhar, não depurar ao vivo.
- Omitir contagens se não houver aprovação para mostrá-las.

### ➡️ Transição para o Ato 2

> “Até aqui observamos o ambiente de forma agregada. Agora vamos acompanhar um
> cenário transversal e mostrar como o Copilot organiza uma decisão.”

---

## ATO 2 — INVESTIGAÇÃO TRANSVERSAL — 00:35–00:47

### 🎯 Objetivo

Demonstrar como o Security Copilot organiza sinais de **identidade, e-mail,
dados e endpoint** em uma triagem coerente, sem transformar indícios em
certezas.

### 💼 Valor para o cliente

Incidentes relevantes raramente ficam dentro de um único produto. O cenário
mostra um problema comum:

1. uma identidade acessa de um contexto incomum;
2. surge um mecanismo de persistência ou coleta em e-mail;
3. ocorre movimentação incomum de arquivos;
4. a ausência de malware pode criar falsa sensação de segurança.

O valor é reduzir o trabalho manual de:

- reconstruir a linha do tempo;
- distinguir fato de hipótese;
- definir o que falta investigar;
- priorizar uma resposta proporcional.

### 🧠 Como explicar os sinais

| Sinal | Por que importa | O que ainda não sabemos |
|---|---|---|
| IP/localização não usuais | Pode indicar sessão anômala | Viagem, VPN ou acesso legítimo |
| MFA aprovado | A autenticação passou | Se o usuário aprovou conscientemente |
| Dispositivo não gerenciado | Menor visibilidade e controle | Se o uso era autorizado |
| Regra de encaminhamento externa | Pode criar persistência ou coleta | Se existe justificativa de negócio |
| 186 downloads em 12 minutos | Volume acima da linha de base | Conteúdo, sensibilidade e propósito |
| Nenhum alerta de malware | Não houve aquela detecção | Não exclui abuso de identidade ou dados |

### ▶️ Configurar fontes

- Criar sessão nova.
- Habilitar somente Projeto Inicial de Triagem de Incidentes.
- Desabilitar Public web.

### 🗣️ Dizer

> “O cenário combina identidade, dispositivo, e-mail e dados. Nenhum evento
> isolado comprova comprometimento.”

> “Nosso objetivo não é pedir que a IA declare um ataque. É pedir que organize
> fatos, hipóteses, confiança e lacunas para orientar o analista.”

### 📋 Copiar e colar

````text
Use exclusivamente a ferramenta "Realizar a triagem de um incidente de segurança" do plugin "Projeto Inicial de Triagem de Incidentes" para analisar os dados sintéticos abaixo.

Entregue:
- fatos confirmados;
- hipóteses com nível de confiança;
- severidade inicial justificada;
- possível mapeamento MITRE ATT&CK;
- ações priorizadas de contenção, investigação e recuperação;
- ações que exigem aprovação humana;
- lacunas de evidência.

Não invente indicadores nem capacidades de produto. Responda em português do Brasil.

Dados sintéticos do incidente:

```json
{
  "classificacao": "SINTETICO - USO EXCLUSIVO EM DEMONSTRACAO",
  "idIncidente": "DEMO-2026-001",
  "titulo": "Entrada incomum seguida de encaminhamento e download de arquivos",
  "periodoUtc": {
    "inicio": "2026-10-14T09:12:00Z",
    "fim": "2026-10-14T09:41:00Z"
  },
  "entidades": {
    "usuario": "analista.financeiro@contoso.example",
    "dispositivo": "FIN-WKS-042",
    "ipNovo": "203.0.113.42",
    "ipHistorico": "198.51.100.27",
    "destinoEncaminhamento": "auditoria@external.example"
  },
  "contextoAmbiente": {
    "criticidadeUsuario": "Alta",
    "justificativa": "Acesso a relatorios consolidados e sistemas de conciliacao; sem funcao administrativa privilegiada",
    "localHabitual": "Brasilia",
    "autenticacao": "MFA por notificacao no aplicativo"
  },
  "eventos": [
    {
      "timestampUtc": "2026-10-14T09:12:00Z",
      "fonte": "Entra ID",
      "evento": "Entrada bem-sucedida a partir de endereco IP nao observado para o usuario nos 30 dias anteriores",
      "detalhes": "MFA aprovado; dispositivo nao gerenciado; localizacao divergente do padrao historico"
    },
    {
      "timestampUtc": "2026-10-14T09:18:00Z",
      "fonte": "Exchange Online",
      "evento": "Criacao de regra de encaminhamento para endereco externo",
      "detalhes": "Regra criada seis minutos apos a entrada"
    },
    {
      "timestampUtc": "2026-10-14T09:26:00Z",
      "fonte": "SharePoint Online",
      "evento": "Download de 186 arquivos em 12 minutos",
      "detalhes": "Volume acima da linha de base informada para o usuario"
    },
    {
      "timestampUtc": "2026-10-14T09:41:00Z",
      "fonte": "Microsoft Defender XDR",
      "evento": "Nenhum alerta de malware associado ao dispositivo no periodo",
      "detalhes": "Ausencia de alerta nao confirma ausencia de comprometimento"
    }
  ],
  "dadosAusentes": [
    "Reputacao atual do endereco IP",
    "Resultado da verificacao de risco do usuario",
    "Confirmacao do usuario sobre a aprovacao de MFA",
    "Conteudo e sensibilidade dos arquivos baixados",
    "Eventos anteriores e posteriores ao periodo analisado"
  ]
}
```
````

### ✅ Validar

- Fatos confirmados.
- Hipóteses e confiança.
- Severidade.
- MITRE ATT&CK.
- Ações condicionadas.
- Lacunas.

### ⚠️ Não concluir

- MFA aprovado não prova legitimidade.
- Download em massa não prova exfiltração.
- Regra externa não prova persistência maliciosa.
- Ausência de malware não reduz automaticamente o risco de identidade.
- O mapeamento MITRE pode ser tentativo.

### 🗣️ Dizer

> “O valor não é afirmar que houve comprometimento. É organizar o que sabemos,
> o que suspeitamos e o que precisamos validar.”

> “Reparem que o Copilot não precisa esconder incerteza para ser útil. A lacuna
> de evidência é parte do resultado.”

### ➡️ Transição

> “A triagem produziu hipóteses. Agora precisamos transformar cada hipótese em
> algo verificável por telemetria.”

---

## ATO 3 — HUNTING E KQL — 00:47–00:54

### 🎯 Objetivo

Converter uma suspeita em um plano verificável:

> **hipótese → telemetria necessária → consulta → critérios que aumentam ou
> reduzem a confiança.**

### 💼 Valor para o cliente

O Copilot reduz a barreira entre a pergunta do analista e a linguagem KQL. Isso
ajuda a:

- acelerar a formulação da busca;
- documentar por que a busca existe;
- explicar KQL para profissionais menos experientes;
- padronizar a revisão por especialistas.

Ele não elimina a validação de schema, desempenho e falsos positivos.

### PROMPT 1 — HIPÓTESES DE HUNTING

### 🧠 Por que começar pela hipótese

Escrever KQL antes de definir a pergunta tende a produzir consultas corretas do
ponto de vista sintático, mas pouco úteis. A hipótese define:

- comportamento procurado;
- fonte de dados;
- evidência esperada;
- condição que muda a confiança;
- falsos positivos plausíveis.

### 📋 Copiar e colar

```text
Com base somente no incidente sintético e na triagem desta sessão, proponha três hipóteses de threat hunting.

Para cada hipótese, informe:
- o comportamento que deve ser validado;
- por que ele é relevante para este incidente;
- a telemetria necessária;
- a fonte de dados Microsoft mais adequada;
- o resultado que aumentaria ou reduziria a confiança;
- possíveis falsos positivos.

Separe claramente fatos confirmados de hipóteses. Não execute ações e não trate hipóteses como evidências.
```

### ✅ Validar

Cada hipótese deve informar:

- comportamento;
- relevância para o incidente;
- telemetria;
- fonte Microsoft;
- evidência favorável e contrária;
- falsos positivos.

### 🗣️ Dizer

> “Uma hipótese útil precisa ser verificável. Agora vamos convertê-la em
> telemetria e consulta.”

### PROMPT 2 — KQL

### 🎯 Objetivo da consulta

Encontrar autenticações bem-sucedidas recentes em que o mesmo usuário aparece
com um IP que não estava presente na sua própria linha de base histórica.

Essa pergunta é útil porque reduz o universo de busca:

- não procura qualquer IP novo no tenant;
- compara cada usuário com seu próprio histórico;
- retorna somente eventos recentes;
- cria uma fila de investigação, não um veredito.

### 🧠 Lógica esperada

1. Criar uma baseline dos 14 dias anteriores.
2. Excluir as últimas 24 horas da baseline.
3. Selecionar logins recentes bem-sucedidos.
4. Comparar `UserPrincipalName + IPAddress`.
5. Usar `leftanti join` para manter pares ainda não observados.
6. Projetar somente os campos úteis ao analista.

### Por que `leftanti join`

O `leftanti` retorna linhas do conjunto recente que **não possuem
correspondência** na baseline. Em linguagem simples:

> “Mostre logins recentes cujo par usuário + IP ainda não havia aparecido no
> histórico comparado.”

### 📋 Copiar e colar

```text
Vamos aprofundar a hipótese 1: possível comprometimento de credenciais ou sessão.

Crie uma consulta KQL para Microsoft Sentinel que identifique entradas bem-sucedidas, nas últimas 24 horas, realizadas a partir de um endereço IP que não tenha sido observado para o mesmo usuário nos 14 dias anteriores.

Requisitos:
- use a tabela SigninLogs;
- considere sucesso de autenticação usando ResultType igual a 0;
- compare o mesmo UserPrincipalName e IPAddress;
- use uma janela histórica que não inclua as últimas 24 horas;
- apresente TimeGenerated, UserPrincipalName, IPAddress, Location, AppDisplayName, DeviceDetail e ConditionalAccessStatus;
- ordene pelos eventos mais recentes;
- adicione comentários em português do Brasil;
- explique a consulta linha por linha;
- informe limitações, campos que podem variar e possíveis falsos positivos;
- não execute a consulta e não invente resultados.
```

### ✅ Validar

- Baseline de 14 dias.
- Últimas 24 horas excluídas da baseline.
- `ResultType == 0`.
- `UserPrincipalName + IPAddress`.
- `leftanti join`.
- Limitações e falsos positivos.

### ⚠️ Falsos positivos esperados

- viagem legítima;
- VPN ou proxy com novo endereço;
- troca de operadora;
- dispositivo pessoal autorizado;
- infraestrutura de autenticação distribuída;
- endereço IPv6 temporário.

### ⚠️ Limitações técnicas

- `Location` e `DeviceDetail` podem ser campos dinâmicos.
- A retenção disponível pode ser menor que a janela solicitada.
- Resultado vazio pode indicar ausência de dados, não ausência de risco.
- A consulta precisa ser revisada no schema real antes de produção.

### 🗣️ Dizer

> “A consulta é um ponto de partida. Antes de produção, precisamos revisar
> schema, custo, janela temporal e falsos positivos.”

> “O ganho não é apenas gerar código. É manter a ligação entre hipótese,
> evidência e decisão.”

### ➡️ Transição

> “Agora temos uma investigação técnica. O próximo desafio é comunicar risco e
> ação para uma liderança sem perder as incertezas.”

---

## ATO 4 — DECISÃO E REVISÃO HUMANA — 00:54–01:00

### 🎯 Objetivo

Mostrar duas capacidades diferentes:

1. adaptar uma investigação técnica para uma audiência executiva;
2. revisar criticamente a recomendação da IA antes de qualquer decisão.

### 💼 Valor para o cliente

O SOC não termina quando a consulta retorna. É necessário comunicar:

- qual é o risco;
- qual pode ser o impacto;
- qual é o nível de confiança;
- quais ações são proporcionais;
- quais decisões exigem aprovação.

Esse ato mostra redução de tempo de redação **sem terceirizar a
responsabilidade**.

### PROMPT 1 — RESUMO EXECUTIVO

### 🧠 Por que limitar a 120 palavras

A restrição força priorização. Um resumo executivo não deve reproduzir logs ou
o relatório técnico; deve sustentar uma decisão.

### 📋 Copiar e colar

```text
Com base somente nos fatos, hipóteses, lacunas e consulta KQL produzidos nesta sessão, gere um resumo executivo de no máximo 120 palavras para uma liderança de segurança.

O resumo deve conter:
- o risco principal;
- o impacto potencial para a organização;
- o nível de confiança atual;
- três ações recomendadas em ordem de prioridade;
- os dados que ainda precisam ser confirmados.

Regras:
- diferencie fatos confirmados de hipóteses;
- não afirme que houve comprometimento ou exfiltração sem evidência suficiente;
- não inclua endereços de e-mail, IPs, nomes de dispositivos ou outros detalhes técnicos desnecessários;
- indique quais ações exigem aprovação humana;
- use linguagem executiva, objetiva e em português do Brasil;
- não ultrapasse 120 palavras.
```

### ✅ Validar

- Risco principal em linguagem de negócio.
- Impacto apresentado como potencial, não como fato.
- Confiança explícita.
- Três ações priorizadas.
- Dados ainda não confirmados.
- Ausência de detalhes técnicos desnecessários.

### ⚠️ Momento didático esperado

Se a resposta recomendar **bloqueio imediato** com confiança apenas moderada,
não esconda o resultado. Use-o para demonstrar supervisão humana.

### PROMPT 2 — REVISÃO HUMANA

### 🎯 Por que executar esta revisão

Ações como bloquear conta, revogar sessões ou remover regras podem interromper
operações. Com evidência incompleta, a resposta deve privilegiar:

1. preservação de evidências;
2. validação urgente;
3. contenção condicional;
4. aprovação humana.

### 📋 Copiar e colar

```text
Revise o resumo executivo anterior aplicando os princípios de supervisão humana, proporcionalidade e menor impacto operacional.

Como o nível de confiança é apenas moderado e ainda não existe confirmação de comprometimento ou exfiltração:

- não recomende o bloqueio imediato da conta como primeira ação;
- priorize preservação de evidências, validação urgente com o usuário e investigação dos eventos;
- apresente bloqueio de conta, revogação de sessões, redefinição de credenciais ou remoção de regras somente como contenções condicionais;
- informe claramente quais evidências aumentariam a confiança e justificariam essas contenções;
- identifique as ações que exigem aprovação humana;
- mantenha fatos e hipóteses separados;
- preserve linguagem executiva e objetiva;
- limite a resposta a 120 palavras;
- responda em português do Brasil.
```

### ✅ Validar

- O bloqueio deixou de ser ação automática.
- A recomendação explica quando conter.
- As evidências que aumentam confiança estão explícitas.
- As ações disruptivas exigem aprovação.

### 🗣️ Dizer

> “A primeira recomendação foi excessivamente disruptiva para confiança
> moderada. Essa correção não diminui a demonstração; ela mostra o modelo
> operacional correto.”

> “O Copilot acelera análise e comunicação. A organização continua responsável
> pelo apetite de risco, pelos gates e pela decisão.”

### ➡️ Transição

> “Até aqui produzimos valor em uma sessão. Agora vamos mostrar como transformar
> esse conhecimento em uma capacidade repetível.”

---

## ATO 5 — DA SESSÃO AO FLUXO REUTILIZÁVEL — 01:00–01:05

### 🎯 Objetivo

Demonstrar que o valor não precisa ficar preso a uma conversa individual. O
mesmo método pode ser reutilizado com entradas, fontes e critérios definidos.

### 💼 Valor para o cliente

- reduz dependência do conhecimento de uma pessoa;
- aumenta consistência entre turnos e equipes;
- facilita revisão e auditoria;
- permite evolução gradual, sem começar por automação autônoma.

### 🧠 Evolução recomendada

| Nível | Forma | Quando usar |
|---|---|---|
| 1 | Prompt guiado | Explorar e validar o caso |
| 2 | Promptbook | Repetir uma sequência conhecida |
| 3 | Plugin | Encapsular habilidade e entradas |
| 4 | Agente | Orquestrar ferramentas com identidade, RBAC e gates |

### ▶️ Mostrar

- Abra **Criar** e mostre que o plugin importado aparece como uma ferramenta GPT.
- Não altere nem publique o agente durante a apresentação.
- Mostre **Sequências de solicitações** para explicar como os prompts podem ser encadeados.

### 🗣️ Dizer

> “Até aqui usamos uma sessão. O próximo nível de valor é empacotar o método:
> entradas padronizadas, fontes definidas, gates de decisão e saídas
> consistentes.”

> “A mesma lógica pode começar como promptbook e evoluir para plugin ou agente,
> sempre com RBAC, testes e auditoria.”

### ⚠️ Não fazer

- Não criar ou publicar um agente ao vivo.
- Não editar o plugin validado.
- Não prometer autonomia sem aprovação.

### ➡️ Transição

> “A tecnologia permite reuso. O playbook define como esse reuso será
> governado.”

---

# 7. PLAYBOOK INSTITUCIONAL — 01:05–01:13

## 🎯 Objetivo

Converter o fluxo demonstrado em um padrão operacional com:

- entradas conhecidas;
- fontes autorizadas;
- etapas consistentes;
- responsáveis;
- aprovadores;
- evidências e saídas registradas.

## 💼 Valor para o cliente

O playbook é o ponto em que o Security Copilot deixa de ser uma ferramenta de
produtividade individual e passa a apoiar uma capacidade institucional.

## 🗣️ Dizer

> “Uma conversa útil economiza minutos. Um playbook útil muda a operação.”

> “O maior valor não é uma resposta isolada. É transformar a experiência dos
> melhores analistas em um método repetível, revisável e auditável.”

## ▶️ Mostrar a sequência

1. Validar contexto, fontes e dados permitidos.
2. Separar fatos e hipóteses.
3. Priorizar por impacto e criticidade.
4. Gerar hunting e KQL.
5. Definir resposta, responsáveis e aprovadores.
6. Produzir saída técnica e executiva.
7. Aplicar gates de revisão humana.

## 🧠 O que cada etapa resolve

| Etapa | Problema resolvido |
|---|---|
| Validar contexto | Evita analisar dados errados ou não autorizados |
| Fatos e hipóteses | Evita transformar inferência em evidência |
| Priorizar | Conecta tecnologia, criticidade e impacto |
| Hunting/KQL | Torna a hipótese verificável |
| Resposta | Define ação, responsável e aprovação |
| Comunicação | Adapta a mesma evidência à audiência |
| Revisão | Evita decisão automática desproporcional |

## ✅ Gates obrigatórios

- Evidências sustentam a conclusão?
- A ação é proporcional?
- Existe impacto operacional?
- Quem aprova?
- Quais dados precisam ser preservados?

## ➡️ Transição

> “Um playbook sem controles apenas repete risco em escala. Por isso, o próximo
> bloco trata de dados, identidade, rastreabilidade e supervisão.”

---

# 8. SEGURANÇA E USO RESPONSÁVEL — 01:13–01:20

## 🎯 Objetivo

Mostrar que segurança da IA não depende apenas do modelo. Depende da combinação
entre identidade, acesso, dados, auditoria, testes e supervisão.

## 🗣️ Dizer

> “IA responsável não é um slide adicional. É parte do desenho do caso de uso,
> das permissões, dos dados e da operação.”

## 🧠 Quatro controles

1. **Menor privilégio:** Copilot não ultrapassa o acesso do usuário.
2. **Dados:** compartilhamento e localização precisam ser revisados.
3. **Rastreabilidade:** fontes, sessões, auditoria e evidências.
4. **Supervisão:** decisões consequentes exigem validação humana.

## 💼 Por que isso importa

- reduz risco de acesso excessivo;
- permite investigar quem usou qual fonte;
- evita automação de decisões não aprovadas;
- cria evidência para segurança, privacidade e conformidade.

## ⚠️ Não afirmar

- “A IA substitui o analista.”
- “O Copilot vê tudo no tenant.”
- “Os dados ficam no Brasil.”
- “Todo recurso mostrado está em GA.”
- “A consulta gerada está pronta para produção.”
- “O resultado comprova comprometimento.”

---

# 9. PILOTO E MÉTRICAS — 01:20–01:25

## 🎯 Objetivo

Sair da reunião com um caso de uso mensurável, um dono e critérios claros para
continuar ou interromper.

## 🗣️ Dizer

> “Não vamos prometer um percentual sem baseline. Vamos medir tempo, esforço,
> qualidade, consistência, retrabalho e segurança da decisão.”

## 🧠 Indicadores e significado

| Indicador | O que revela |
|---|---|
| Tempo até a primeira avaliação | Velocidade para produzir contexto útil |
| Tempo ativo do analista | Esforço humano realmente economizado |
| Evidências e lacunas | Qualidade e transparência |
| Consistência entre analistas | Padronização do processo |
| KQL aprovada | Utilidade técnica da assistência |
| Tempo para informe executivo | Redução de retrabalho de comunicação |
| Recomendações corrigidas | Efetividade da supervisão humana |
| Reuso do playbook | Adoção e capacidade institucional |

## 💼 Caso inicial recomendado

> Triagem e comunicação de incidentes de identidade com possível exposição de
> dados.

## ✅ Critério de saída

Antes de encerrar, obtenha uma resposta para:

- qual fluxo será pilotado;
- quem é o responsável;
- qual dado pode ser usado;
- qual baseline será medida;
- quando será feita a revisão de resultado.

---

# 10. FECHAMENTO E Q&A — 01:25–01:30

## DIZER

> “Hoje mostramos três coisas: conexão com o ambiente, melhoria da decisão e
> capacidade de institucionalizar o processo.”

> “Passamos do contexto externo ao sinal, do sinal à investigação e da
> investigação à decisão, mantendo evidência, governança e supervisão humana.”

## PERGUNTA DE COMPROMISSO

> “Qual fluxo deve ser o primeiro piloto: identidade, hunting,
> vulnerabilidades ou proteção de dados?”

---

# 11. RESPOSTAS CURTAS PARA PERGUNTAS

## “Ele substitui o analista?”

> Não. O produto amplia a expertise humana. Investigação e decisão continuam
> exigindo validação.

## “Ele vê todo o tenant?”

> Não. O acesso depende da função no Security Copilot e do RBAC dos produtos.

## “Os dados treinam a OpenAI?”

> Segundo a documentação Microsoft, os dados não são compartilhados com a
> OpenAI nem usados para treinar o modelo fundamental do Azure OpenAI.

## “Os dados ficam no Brasil?”

> A localização é definida na criação do workspace. Precisamos validar a
> configuração e os requisitos com arquitetura, privacidade e o time de conta.

## “Ele toma ações automaticamente?”

> Alguns agentes podem executar ações delimitadas dentro das permissões e
> aprovações configuradas. Nesta demonstração usamos somente leitura, análise e
> recomendações.

## “Qual ganho percentual?”

> Não prometemos percentual sem baseline. O piloto mede tempo, esforço,
> qualidade, retrabalho, consistência e segurança da decisão.

---

# 12. PLANO DE CORTE

## Se perder 5 minutos

- Execute apenas um agregado do Defender.

## Se perder 10 minutos

- Remova o pulso real do Defender.

## Nunca cortar

- Revisão humana.
- Governança.
- Próximos passos.
- Pergunta de compromisso.

---

# 13. CHECKLIST FINAL

- [ ] Apresentação aberta.
- [ ] PDF de contingência aberto.
- [ ] Este teleprompter aberto.
- [ ] Sessão salva de Threat Intelligence.
- [ ] Sessão salva da triagem sintética.
- [ ] Sessão salva do KQL.
- [ ] Sessão salva do resumo revisado.
- [ ] Plugin personalizado habilitado.
- [ ] Microsoft Threat Intelligence habilitado.
- [ ] Microsoft Defender XDR habilitado.
- [ ] Embedded Copilot testado duas vezes ou removido do fluxo principal.
- [ ] Portal standalone preparado como fallback do Embedded.
- [ ] Public web desabilitado durante os testes controlados.
- [ ] Janela limpa e notificações desabilitadas.
- [ ] Cronômetro pronto.
- [ ] Plano de corte conhecido.

---

# 14. APÊNDICE OPCIONAL — THREAT INTELLIGENCE

> Não iniciar a demonstração por este cenário. Use somente se houver cobertura
> previamente validada para um ator ou campanha específica.

## Abordagem recomendada

Em vez de buscar genericamente por setor e região, use um ator conhecido e um
promptbook de perfil de ator. Exemplo:

```text
Usando somente o Microsoft Threat Intelligence, produza um perfil executivo do ator Midnight Blizzard.

Inclua:
- objetivos e motivações conhecidas;
- setores historicamente visados;
- táticas e técnicas MITRE ATT&CK;
- ferramentas e padrões de acesso conhecidos;
- artigos e fontes disponíveis com suas datas;
- perguntas defensivas que uma organização deve investigar em seu ambiente.

Diferencie informações históricas de atividade recente. Não afirme que o ator está direcionando a organização ou o Brasil sem evidência explícita. Responda em português do Brasil.
```

Se não houver resultado, não depure ao vivo. Volte para o pulso real do Defender.
