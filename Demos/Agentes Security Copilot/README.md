# Demo de Agentes do Microsoft Security Copilot

## Objetivo

Este pacote demonstra três camadas de extensibilidade:

1. **Agente nativo Microsoft:** Vulnerability Remediation Agent no Intune.
2. **Artefato oficial:** tool KQL do repositório `Azure/Security-Copilot` e agente interativo da documentação Microsoft.
3. **Agente personalizado:** priorização de exposição usando KQL do Defender.

> O framework de desenvolvimento de agentes customizados e o Vulnerability
> Remediation Agent estão documentados como recursos de pré-lançamento/preview.
> Valide disponibilidade antes de produção.

## Transparência sobre GitHub

O repositório oficial público
[`Azure/Security-Copilot`](https://github.com/Azure/Security-Copilot) contém
plugins e tools KQL, GPT e API. Em 20/10/2026, ele não contém um manifesto
completo com `AgentDefinitions` pronto para upload.

Por isso, a demonstração usa:

- uma **tool oficial do GitHub**;
- um **agente oficial de exemplo do Microsoft Learn**;
- um **agente customizado** que utiliza tools KQL.

Não apresente um plugin como se fosse um agente completo.

## Arquivos

- `security-copilot-docs-agent-oficial.yaml`: reprodução do exemplo oficial de
  agente interativo.
- `tool-oficial-github-kql-defender.yaml`: tool KQL do GitHub oficial.
- `agente-priorizacao-exposicao-ptbr.yaml`: agente personalizado somente leitura.

## Cenário 1 — agente nativo do Intune

### Vulnerability Remediation Agent

O agente:

- usa dados do Defender Vulnerability Management;
- prioriza CVEs por severidade, impacto e alcance;
- oferece orientação de remediação no Intune;
- registra sugestões que o administrador marca como aplicadas;
- não executa remediação automaticamente.

### Pré-requisitos

- Intune Plan 1;
- Security Copilot com SCUs;
- Defender for Endpoint P2 ou Defender Vulnerability Management;
- plugins Intune e Defender;
- identidade agêntica;
- Intune read-only;
- Defender Security Reader ou Unified RBAC equivalente.

### Limitações

- public preview;
- nuvem pública;
- Windows cliente e apps Intune;
- não cobre Windows Server;
- sem scope tags no preview;
- execução manual e sem pause;
- Mark as Applied é atestação humana.

## Cenário 2 — amostra oficial e tool do GitHub

### Tool oficial

Fonte:

[`KQL_DefenderExample.yaml`](https://github.com/Azure/Security-Copilot/blob/main/Plugins/MSFT_Plugin_Samples/KQL/KQL_DefenderExample.yaml)

A tool `GetLatestEmailsByRecipient` consulta `EmailEvents` por destinatário.

Teste seguro:

```text
Use exclusivamente a habilidade GetLatestEmailsByRecipient do plugin My Sample Defender KQL Plugin para procurar os e-mails mais recentes do destinatário sintético analista@example.com. Não use outras fontes. Se não houver resultados, informe isso sem inferir atividade.
```

### Agente oficial de documentação

Fonte:

[Build Security Copilot Interactive Agents](https://learn.microsoft.com/copilot/security/developer/build-interactive-agents)

O agente usa Microsoft Learn MCP e demonstra:

- `AgentDefinitions`;
- `PromptSkill`;
- `InteractiveAgent`;
- `ChildSkills`;
- teste;
- Activity map;
- publicação pessoal.

## Cenário 3 — agente customizado

### Agente de Priorização de Exposição

O agente chama três tools KQL:

- `GetExposureSummary`;
- `GetTopExposedSoftware`;
- `GetTopCveReach`.

### Guardrails

- somente leitura;
- dados agregados;
- sem DeviceId ou DeviceName;
- exposição não tratada como exploração;
- menor número de tools;
- limitações explícitas;
- aprovação humana para remediação.

### Prompts

```text
Resuma nossa exposição atual por severidade e explique como priorizar.
```

```text
Quais softwares concentram mais dispositivos expostos a vulnerabilidades críticas ou altas?
```

```text
Quais CVEs críticas ou altas afetam mais dispositivos e quais evidências ainda precisamos validar?
```

## Ordem de implantação

1. Publicar os agentes customizados como **Myself only**.
2. Habilitar plugins obrigatórios.
3. Testar cada tool separadamente.
4. Testar a orquestração do agente.
5. Configurar a identidade usada pelo chat publicado.
6. Verificar Activity map.
7. Revisar dados e respostas.
8. Medir SCU.
9. Publicar no workspace somente após aprovação.

## Solução de problemas

### Builder funciona, mas o chat publicado falha

O teste no builder e o chat publicado são experiências distintas. Se as tools
funcionarem no builder, mas o chat não iniciar:

1. confirme que `Descriptor.Name`, `AgentDefinitions.Name`,
   `RequiredSkillsets`, `ProcessSkill`, `PromptSkill` e o nome da skill de
   agente usam o mesmo namespace técnico ASCII;
2. publique novamente como **Myself only**;
3. em **Agents**, selecione **Set up**;
4. vincule somente uma conta autorizada e com o menor privilégio necessário;
5. confirme que todos os plugins obrigatórios aparecem como disponíveis;
6. execute **Chat with agent** e valide o Activity map.

Não reutilize uma instância antiga com namespace divergente. Remova-a apenas
depois que a nova versão passar no teste do chat publicado.

### A captura da identidade não conclui

- permita a janela de autenticação solicitada pelo navegador;
- confirme que a sessão do Security Copilot continua válida;
- repita o setup em uma janela sem bloqueio de pop-ups;
- não publique no workspace enquanto a identidade não estiver validada;
- não aumente privilégios apenas para contornar o setup.

## Critérios de qualidade

- duas execuções consecutivas;
- tools esperadas;
- sem identificadores indevidos;
- fatos e interpretação separados;
- limitações explícitas;
- nenhuma ação de escrita;
- revisão humana obrigatória.

## Fontes oficiais

- [Vulnerability Remediation Agent](https://learn.microsoft.com/intune/copilot/agents/vulnerability-remediation-agent)
- [Gerenciar o agente](https://learn.microsoft.com/intune/copilot/agents/manage-vulnerability-remediation-agent)
- [Agent manifest](https://learn.microsoft.com/copilot/security/developer/agent-manifest)
- [Interactive agents](https://learn.microsoft.com/copilot/security/developer/build-interactive-agents)
- [Test agent](https://learn.microsoft.com/copilot/security/developer/test-agent-dev)
- [Publish agent](https://learn.microsoft.com/copilot/security/developer/publish-agent-dev)
