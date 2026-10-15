# Conjunto de plugins de enriquecimento
**Autor: Craig Freyman**

## Plugin de enriquecimento de usuários
Este conjunto de habilidades de enriquecimento foi desenvolvido para aprimorar investigações de segurança, fornecendo informações detalhadas sobre as atividades dos usuários, como comportamento de entrada, alterações de senha, modificações de MFA, análise de localização, atividades de caixa de correio e acompanhamento de entradas por IP. Com essas ferramentas, as equipes de segurança podem identificar possíveis ameaças, monitorar riscos dos usuários e responder com eficácia a comportamentos suspeitos.

---

### UnusualSigninActivity
Identifica padrões incomuns de entrada de um usuário específico com base em anomalias, como locais de alto risco, falhas de entrada e mudanças repentinas no uso de dispositivos, aplicativos ou endereços IP. Destaca desvios do comportamento normal e fornece recomendações de ações de segurança.

**Prompt de exemplo**: identifique padrões incomuns de entrada de mscott@paper.com.

---

### PasswordChangeCount
Analisa o número de alterações de senha de um usuário específico nos últimos sete dias. Identifica possíveis ameaças de segurança, como comprometimento de conta ou ataques de phishing, detectando anomalias nos padrões de alteração de senha.

**Prompt de exemplo**: detecte alterações recentes de senha de mscott@paper.com nos últimos sete dias.

---

### RecentMFAChanges
Acompanha alterações recentes de MFA de um usuário, identificando métodos de autenticação adicionados, removidos ou modificados. Fornece informações detalhadas sobre as alterações e destaca anomalias.

**Prompt de exemplo**: acompanhe as alterações de MFA de mscott@paper.com nos últimos sete dias.

---

### UserHomeOfficeLocation
Obtém e compara a localização do escritório de origem de um usuário (cidade, país e estado) com locais recentes de entrada para detectar atividades incomuns. Destaca desvios que podem indicar acesso não autorizado.

**Prompt de exemplo**: compare a localização do escritório de origem com os padrões de entrada de mscott@paper.com.

---

### UserSigninBaseline
Estabelece uma linha de base da atividade de entrada habitual de um usuário nos últimos 30 dias, incluindo o endereço IP, o local, o dispositivo, o aplicativo e o aplicativo cliente usados com mais frequência. Detecta desvios para identificar possíveis riscos de segurança.

**Prompt de exemplo**: estabeleça uma linha de base de entradas de mscott@paper.com nos últimos 30 dias.

---

### FailedUserSignInSpecificDay
Identifica tentativas de entrada com falha de um usuário específico em um período retrospectivo definido. Fornece informações sobre as tentativas com falha, incluindo carimbos de data/hora, endereços IP, locais e motivos da falha.

**Prompt de exemplo**: identifique tentativas de entrada com falha de mscott@paper.com nos últimos sete dias.

---

### EnhancedUserRiskAssessment
Combina eventos de risco do usuário, entradas recentes, indicadores de usuário de alto risco e alertas de segurança para fornecer um contexto detalhado sobre atividades de risco de um usuário específico. Apoia a detecção de ameaças, a priorização de incidentes e o planejamento de correções.

**Prompt de exemplo**: obtenha detalhes avançados de risco do usuário mscott@paper.com.

---

### ImpossibleTravel
Detecta deslocamentos impossíveis analisando padrões de entrada e identificando entradas em locais geograficamente distantes em um intervalo de tempo curto e irrealista. Apoia a detecção de possível uso indevido de credenciais.

**Prompt de exemplo**: detecte eventos de deslocamento impossível de mscott@paper.com nos últimos sete dias.

---

### SuspiciousMailboxActivities
Investiga atividades recentes da caixa de correio para detectar possíveis ameaças de segurança, como:
- Regras da caixa de entrada recém-criadas ou modificadas que redirecionem ou filtrem emails de maneira suspeita.
- Alterações nas permissões da caixa de correio que possam indicar acesso não autorizado.
Concentra-se na identificação de anomalias que possam levar à exfiltração ou a tentativas de comprometimento de email corporativo (BEC).

**Prompt de exemplo**: investigue atividades suspeitas na caixa de correio de mscott@test.com nos últimos 30 dias.

---

### DailyEntraIDRiskDetectionReview
Resume e prioriza as detecções de risco do Entra ID do último dia, destacando alertas relevantes ou críticos que possam exigir a revisão de um analista do SOC.

**Prompt de exemplo**: resuma as detecções de risco do Entra ID das últimas 24 horas.

---

### SuccessfulLoginsFromIP
Encontra todas as entradas bem-sucedidas de usuários provenientes de um endereço IP especificado. Retorna informações detalhadas do evento, incluindo carimbo de data/hora, usuário, local, dispositivo e aplicativo.

**Prompt de exemplo**: liste todas as entradas bem-sucedidas provenientes de 1.2.3.4.

---

### SuccessfulLoginCountFromIP
Retorna o número total de tentativas de entrada bem-sucedidas provenientes de um determinado endereço IP. É útil para determinar rapidamente se um IP específico já foi usado com sucesso.

**Prompt de exemplo**: conte as entradas bem-sucedidas provenientes de 1.2.3.4.

---
