# Consultas de busca dos schemas ASIM essenciais de DNS, rede, proteção contra ameaças e sessões da Web

Este repositório contém uma coleção de consultas de busca de schemas do Advanced Security Information Model (ASIM), desenvolvidas para ajudar a detectar diversas anomalias de rede e possíveis ameaças de segurança.

## Consultas do schema ASIM essencial de DNS

- **As 25 consultas DNS com mais falhas nas últimas 24 horas**
- **Possível atividade de beaconing**
- **Possível atividade de tunelamento DNS ou exfiltração de dados**
- **Solicitações DNS de um cliente acima da média diária**
- **Conexão detectada com site pouco popular**
- **Aumento anômalo da atividade DNS dos clientes**
- **Padrão de exploração da CVE-2020-1350 (SIGRED)**

## Consultas do schema essencial de rede

- **Detectar tráfego LDAP de saída (schema ASIM Network Session)**
- **Detectar uso indevido de porta por anomalia (schema ASIM Network Session)**
- **Detectar uso indevido de porta por limite estático (schema ASIM Network Session)**
- **Detectar vários usuários com o mesmo endereço MAC (schema ASIM Network Session)**
- **Incompatibilidade entre o nome do aplicativo de destino e a porta de destino (schema ASIM Network Session)**
- **Protocolos que transmitem autenticação em texto não criptografado (schema ASIM Network Session)**
- **Tráfego de rede da Área de Trabalho Remota (schema ASIM Network Session)**

## Schema essencial de proteção contra ameaças de rede

- **Tráfego de rede da Área de Trabalho Remota (schema ASIM Network Session)**
- **Comando arriscado codificado em Base64 na URL**
- **User Agent de frameworks de exploração e teste de invasão**

## Elementos essenciais de sessões da Web

- **User Agent vazio detectado (ASIM Web Session)**
- **Número excessivo de solicitações proibidas detectado (ASIM Web Session)**
- **Detectar endereço IP na URL solicitada (ASIM Web Session)**
- **Detectar UserAgent do Kali Linux (ASIM Web Session)**
- **Tráfego de beaconing baseado em User Agents comuns que visitam um número limitado de domínios (ASIM Web Session)**
- **Possível beaconing detectado — quantidade semelhante de bytes enviados (ASIM Web Session)**
- **Possível beaconing detectado (ASIM Web Session)**
- **Solicitação de bots e rastreadores (ASIM Web Session)**
- **Detectar informações de ameaças em solicitações da Web (ASIM Web Session)**

## Uso no plugin do Security Copilot

### Instruções

### Pré-requisitos

-   [Security Copilot habilitado](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)
-   [Acesso para carregar plugins personalizados](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)
-   [Workspace do Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/quickstart-onboard) criado.
-   Parâmetros do plugin KQL: nome do workspace do Microsoft Sentinel, ID da assinatura, nome do grupo de recursos e ID do locatário do Entra.
#### Carregar o plugin personalizado

1. Obtenha o arquivo YAML desejado neste diretório: - [DNSEssentials_HuntingQueries.yaml](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Sentinel%20Custom%20Plugin%20Scenarios/ASIM%Hunting%quries/DNSEssentials_HuntingQueries.yaml).

   [NetworkSessionsEssentials_HuntingQueries.yaml](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Sentinel%20Custom%20Plugin%20Scenarios/ASIM%Hunting%quries/NetworkSessionsEssentials_HuntingQueries.yaml).

    [NetworkThreatProtectionEssentials_HuntingQaueries.yaml](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Sentinel%20Custom%20Plugin%20Scenarios/ASIM%Hunting%quries/NetworkThreatProtectionEssentials_HuntingQaueries.yaml).

     [WebSessionEssentials_HuntingQueries.yaml](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Sentinel%20Custom%20Plugin%20Scenarios/ASIM%Hunting%quries/NetworkThreatProtectionEssentials_HuntingQaueries.yaml).

2. Modifique a consulta KQL conforme necessário para atender aos seus requisitos.


3. [Carregue o plugin personalizado](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#add-custom-plugins) e, na caixa de diálogo exibida, insira o ID do locatário, o ID da assinatura, o nome do workspace e o grupo de recursos que hospeda o workspace do Sentinel. Verifique se o plugin está ativado.

![CopilotForSecurity](https://learn.microsoft.com/en-us/security-copilot/media/add-plugin-button.png)

