![Visão geral do Copilot for Security](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)

# Conjunto de plugins de enriquecimento do Copilot for Security

**Autor: Craig Freyman**

## Visão geral
Este conjunto de plugins permite enriquecer várias entidades em operações e investigações de segurança. Há um README detalhado para cada tipo de enriquecimento.

### Enriquecimento de alertas
Aprimora investigações de segurança obtendo e correlacionando dados relacionados a alertas. Permite pesquisar alertas por título, obter evidências associadas e avaliar incidentes de segurança com eficiência.

### Enriquecimento de usuários
Conjunto de ferramentas desenvolvido para aprimorar investigações de segurança por meio da análise das atividades dos usuários, da detecção de anomalias no comportamento de entrada, do acompanhamento de alterações de senha, do monitoramento de modificações de MFA e da verificação de informações de localização. Ajuda as equipes de segurança a identificar ameaças e garantir a conformidade com as políticas de segurança.

### Enriquecimento de URLs
Aprimora investigações de segurança fornecendo informações detalhadas sobre as interações dos usuários com URLs. Permite acompanhar cliques em URLs, analisar padrões de cliques e correlacionar atividades de URL com outros eventos de segurança para realizar avaliações abrangentes de risco.

### Enriquecimento de incidentes
Fornece informações sobre alertas relacionados a incidentes para melhorar as investigações de segurança. Permite correlacionar, obter e analisar com eficiência os alertas vinculados a incidentes específicos para realizar investigações direcionadas.

### Enriquecimento de arquivos
Aprimora investigações de segurança fornecendo informações detalhadas sobre a atividade de arquivos nos dispositivos. Ajuda a identificar arquivos potencialmente mal-intencionados, avaliar ameaças de segurança e recomendar etapas de correção.

### Enriquecimento de emails
Aprimora investigações de segurança fornecendo informações sobre a atividade de email. Permite identificar interações de email com base em domínios, destinatários, remetentes e solicitações de quarentena, apoiando uma análise abrangente de ameaças.

### Enriquecimento de dispositivos
Fornece informações sobre o comportamento dos dispositivos, vulnerabilidades e padrões de atividade. Ajuda as equipes de segurança a monitorar a exposição dos dispositivos, analisar eventos de entrada e identificar vulnerabilidades para correção direcionada.

### Enriquecimento de IP
Aprimora investigações de segurança analisando atividades relacionadas a IP, como tentativas de entrada com falha, ataques de força bruta e anomalias de entrada. Apoia a detecção de comportamentos suspeitos de entrada e possíveis ameaças.

### Enriquecimento do Purview
Desenvolvido para aprimorar investigações de segurança por meio da consulta de eventos de DLP e atividades de arquivos de usuários e dispositivos. Ajuda os analistas de segurança a correlacionar alertas de prevenção contra perda de dados (DLP) com outros tipos de evento para auxiliar nos esforços de investigação e resposta.

**Observação**
Antes de invocar qualquer habilidade, verifique se você tem permissões suficientes e acesso aos conjuntos de dados necessários no Microsoft Defender ou no Sentinel.

## **Pré-requisitos**
1. Acesso aos ambientes do Microsoft Defender e do Sentinel.

2. Verifique se foram atribuídas as permissões adequadas para consultar as tabelas relevantes (por exemplo, `SigninLogs`, `EmailEvents` e `DeviceFileEvents`).

## Selecionar ou carregar o arquivo de manifesto anexado no console do Copilot for Security
1. Clique no botão `Sources` e acesse `Custom Plugins`.
2. Clique em `Security Copilot plugin Custom .yaml or .json`.
3. Alguns plugins usam o Sentinel; nesse caso, insira as informações do Azure quando solicitado.
