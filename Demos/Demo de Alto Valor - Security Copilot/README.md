# DEMO DE ALTO VALOR — MICROSOFT SECURITY COPILOT

## Teleprompter completo, prompts e testes — 90 minutos

> Este é o único arquivo que precisa ficar aberto durante a apresentação.
> Cada bloco informa o que dizer, o que fazer, o que copiar e como reagir se
> algo falhar.

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

1. Pulso real do Defender — 7 min.
2. Investigação transversal — 12 min.
3. Hunting e KQL — 7 min.
4. Decisão e revisão humana — 6 min.
5. Da sessão ao fluxo reutilizável — 5 min.

---

## ATO 1 — PULSO REAL DO DEFENDER — 00:28–00:35

### CONFIGURAR FONTES

- Criar sessão separada.
- Habilitar somente Microsoft Defender XDR.
- Desabilitar Public web.
- Não usar o plugin personalizado.

### DIZER

> “Agora saímos da inteligência pública e comprovamos conexão com telemetria
> real, de forma agregada e somente leitura.”

## TESTE A — EVENTOS DE REDE — VALIDADO

### COPIAR E COLAR

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

### DIZER

> “Contagem é sinal, não veredito. Volume não substitui impacto, contexto ou
> validação.”

## TESTE B — VULNERABILIDADES AGREGADAS — TESTAR ANTES

### COPIAR E COLAR

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

## TESTE C — ALERTAS AGREGADOS — ALTERNATIVA

### COPIAR E COLAR

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

### REGRA DE TEMPO

- Executar no máximo dois testes.
- Se um teste falhar, não depurar ao vivo.
- Omitir contagens se não houver aprovação para mostrá-las.

---

## ATO 2 — INVESTIGAÇÃO TRANSVERSAL — 00:35–00:47

### CONFIGURAR FONTES

- Criar sessão nova.
- Habilitar somente Projeto Inicial de Triagem de Incidentes.
- Desabilitar Public web.

### DIZER

> “O cenário combina identidade, dispositivo, e-mail e dados. Nenhum evento
> isolado comprova comprometimento.”

### COPIAR E COLAR

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

### MOSTRAR

- Fatos confirmados.
- Hipóteses e confiança.
- Severidade.
- MITRE ATT&CK.
- Ações condicionadas.
- Lacunas.

### DIZER

> “O valor não é afirmar que houve comprometimento. É organizar o que sabemos,
> o que suspeitamos e o que precisamos validar.”

---

## ATO 3 — HUNTING E KQL — 00:47–00:54

### PROMPT 1 — HIPÓTESES DE HUNTING

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

### DIZER

> “Uma hipótese útil precisa ser verificável. Agora vamos convertê-la em
> telemetria e consulta.”

### PROMPT 2 — KQL

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

### VALIDAR

- Baseline de 14 dias.
- Últimas 24 horas excluídas da baseline.
- `ResultType == 0`.
- `UserPrincipalName + IPAddress`.
- `leftanti join`.
- Limitações e falsos positivos.

### DIZER

> “A consulta é um ponto de partida. Antes de produção, precisamos revisar
> schema, custo, janela temporal e falsos positivos.”

---

## ATO 4 — DECISÃO E REVISÃO HUMANA — 00:54–01:00

### PROMPT 1 — RESUMO EXECUTIVO

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

### SE A PRIMEIRA AÇÃO FOR BLOQUEAR A CONTA

### PROMPT 2 — REVISÃO HUMANA

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

### DIZER

> “A primeira recomendação foi excessivamente disruptiva para confiança
> moderada. Essa correção não diminui a demonstração; ela mostra o modelo
> operacional correto.”

---

## ATO 5 — DA SESSÃO AO FLUXO REUTILIZÁVEL — 01:00–01:05

### MOSTRAR

- Abra **Criar** e mostre que o plugin importado aparece como uma ferramenta GPT.
- Não altere nem publique o agente durante a apresentação.
- Mostre **Sequências de solicitações** para explicar como os prompts podem ser encadeados.

### DIZER

> “Até aqui usamos uma sessão. O próximo nível de valor é empacotar o método:
> entradas padronizadas, fontes definidas, gates de decisão e saídas
> consistentes.”

> “A mesma lógica pode começar como promptbook e evoluir para plugin ou agente,
> sempre com RBAC, testes e auditoria.”

### NÃO FAZER

- Não criar ou publicar um agente ao vivo.
- Não editar o plugin validado.
- Não prometer autonomia sem aprovação.

---

# 7. PLAYBOOK INSTITUCIONAL — 01:05–01:13

## DIZER

> “Uma conversa útil economiza minutos. Um playbook útil muda a operação.”

> “O maior valor não é uma resposta isolada. É transformar a experiência dos
> melhores analistas em um método repetível, revisável e auditável.”

## MOSTRAR A SEQUÊNCIA

1. Validar contexto, fontes e dados permitidos.
2. Separar fatos e hipóteses.
3. Priorizar por impacto e criticidade.
4. Gerar hunting e KQL.
5. Definir resposta, responsáveis e aprovadores.
6. Produzir saída técnica e executiva.
7. Aplicar gates de revisão humana.

## GATES OBRIGATÓRIOS

- Evidências sustentam a conclusão?
- A ação é proporcional?
- Existe impacto operacional?
- Quem aprova?
- Quais dados precisam ser preservados?

---

# 8. SEGURANÇA E USO RESPONSÁVEL — 01:13–01:20

## DIZER

> “IA responsável não é um slide adicional. É parte do desenho do caso de uso,
> das permissões, dos dados e da operação.”

## QUATRO CONTROLES

1. **Menor privilégio:** Copilot não ultrapassa o acesso do usuário.
2. **Dados:** compartilhamento e localização precisam ser revisados.
3. **Rastreabilidade:** fontes, sessões, auditoria e evidências.
4. **Supervisão:** decisões consequentes exigem validação humana.

## NÃO AFIRMAR

- “A IA substitui o analista.”
- “O Copilot vê tudo no tenant.”
- “Os dados ficam no Brasil.”
- “Todo recurso mostrado está em GA.”
- “A consulta gerada está pronta para produção.”
- “O resultado comprova comprometimento.”

---

# 9. PILOTO E MÉTRICAS — 01:20–01:25

## DIZER

> “Não vamos prometer um percentual sem baseline. Vamos medir tempo, esforço,
> qualidade, consistência, retrabalho e segurança da decisão.”

## INDICADORES

- Tempo até a primeira avaliação qualificada.
- Tempo ativo do analista.
- Evidências citadas e lacunas explícitas.
- Consistência entre analistas.
- KQL aprovada sem retrabalho relevante.
- Tempo para informe executivo.
- Recomendações disruptivas corrigidas.
- Reuso do playbook.

## CASO INICIAL RECOMENDADO

> Triagem e comunicação de incidentes de identidade com possível exposição de
> dados.

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
