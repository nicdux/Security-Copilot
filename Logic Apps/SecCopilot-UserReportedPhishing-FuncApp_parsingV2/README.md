# Análise de phishing com o Security Copilot
**Autor:** Craig Freyman

Uma solução automatizada de análise de emails de phishing que usa Azure Logic Apps, Function Apps e Security Copilot. Com as permissões adequadas, ela pode ser implantada em cinco minutos. O Logic App monitora uma caixa de correio compartilhada do Office 365 e aciona a análise quando um email chega. O Security Copilot avalia se a mensagem tem intenção maliciosa e gera relatórios HTML detalhados, enviados por email. A integração opcional com o Microsoft Sentinel permite acompanhar e gerenciar incidentes. Este projeto demonstra as possibilidades do Security Copilot e do Azure. Ele pode funcionar imediatamente ou exigir ajustes; a boa notícia é que usa apenas um prompt do Security Copilot, o que facilita a personalização para sua organização.

## Visão geral

Esta solução oferece um fluxo de trabalho completo para analisar emails suspeitos de phishing. A funcionalidade principal é executada por uma série de Azure Functions que analisam emails, extraem dados importantes, limpam a entrada JSON e geram relatórios HTML. Combinada ao Security Copilot e aos Logic Apps, ela cria um sistema eficiente para distinguir emails legítimos, spam, suspeitos e de phishing.

### Componentes principais

1. **Função de análise de email** — extrai e processa o conteúdo do email, incluindo:
   - Desempacotamento recursivo para localizar os emails originais (trata mensagens encaminhadas, inseridas e encapsuladas em TNEF)
   - **Compatibilidade aprimorada com o Proofpoint** para analisar emails encaminhados pelo Proofpoint
   - Tratamento inteligente da proteção de URL do Proofpoint e do Microsoft SafeLinks
   - Compatibilidade com anexos EML e MSG
   - Análise completa de cabeçalhos, corpo e anexos

2. **Gerador de relatórios HTML** — cria relatórios HTML formatados com base nos resultados da análise de phishing:
   - Categorização por cores (phishing, spam, legítimo, suspeito)
   - Detalhamento das descobertas da análise
   - Organização por categorias de avaliação

### Finalidade e escopo

Esta solução não foi projetada para substituir os filtros tradicionais de spam ou os gateways de segurança de email. Em vez disso, demonstra as possibilidades da combinação do Security Copilot com Azure Functions e Logic Apps para aprimorar sua infraestrutura de segurança de email existente. A solução pressupõe que você já tenha um filtro padrão no gateway de email.

O foco principal é oferecer uma análise mais detalhada dos emails suspeitos encaminhados para investigação, especialmente aqueles provenientes de ambientes protegidos pelo Proofpoint.

## Pré-requisitos

1. **Recursos do Azure:**
   - Assinatura do Azure
   - Direitos de Contributor no grupo de recursos de destino da implantação
   - [Security Copilot Security Compute Units](https://learn.microsoft.com/en-us/copilot/security/get-started-security-copilot)
   - Workspace do Microsoft Sentinel (opcional)

2. **Configuração de email:**
   - [Caixa de correio compartilhada do Office 365 para monitoramento](https://learn.microsoft.com/en-us/microsoft-365/admin/email/create-a-shared-mailbox?view=o365-worldwide)
   - Permissões para gerenciar configurações de email

## Etapas de implantação

### 1. Implantar o Function App

[![Implantar no Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FCopilot-For-Security%2Fmain%2FLogic%20Apps%2FSecCopilot-UserReportedPhishing-FuncApp_parsingV2%2Ffunctionapp_azuredeploy.json)

Parâmetros obrigatórios:
- FunctionAppName (o prefixo "phish" e caracteres aleatórios são adicionados ao nome)
- FunctionAppResourceGroup

Aguarde a implantação completa do Function App antes de prosseguir para a etapa 2.

### 2. Implantar o Logic App

[![Implantar no Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FCopilot-For-Security%2Fmain%2FLogic%20Apps%2FSecCopilot-UserReportedPhishing-FuncApp_parsingV2%2Flogicapp_azuredeploy.json)

Parâmetros obrigatórios:
- SubscriptionId
- LogicAppName
- FunctionAppName (etapa 1)
- FunctionAppResourceGroup (etapa 1)
- SharedMailboxAddress
- HTMLReportRecipient

Parâmetros opcionais do Sentinel (use "none" se não estiver usando o Sentinel):
- LogAnalyticsWorkspaceName
- LogAnalyticsWorkspaceId
- LogAnalyticsResourceGroup

### 3. Configurar conexões de API

1. Abra o Logic App no portal do Azure.
2. Autorize estas conexões:
   - Office 365 (acesso à caixa de correio compartilhada)
   - Security Copilot
   - Azure Monitor Logs (se estiver usando o Sentinel)
   - Sentinel (se estiver usando o Sentinel)

### 3. Configurar permissões do Logic App

Se usar a integração com o Sentinel, atribua estas funções à identidade gerenciada do Logic App:

1. Função "Log Analytics Reader" (fornece Microsoft.OperationalInsights/workspaces/read)
2. Função "Microsoft Sentinel Responder" (fornece Microsoft.SecurityInsights/incidents/comments/write)

Atribua as permissões passo a passo:

1. Abra o workspace do Log Analytics e acesse "Access control (IAM)".
![Controle de acesso do Log Analytics](image.png)
2. Selecione "Log Analytics Reader".
![Seleção da função Log Analytics Reader](image-1.png)
3. Selecione "Managed Identity" e escolha o nome do Logic App.
![Seleção da identidade gerenciada](image-2.png)
4. Clique em Next e atribua as permissões.
5. Repita as etapas 1 a 4 para a função "Microsoft Sentinel Responder".

### 5. Habilitar o Logic App

O Logic App é implantado em estado desabilitado. Habilite-o na visão geral do Logic App para iniciar a operação.

## Funções e pontos de extremidade

O Function App expõe os seguintes pontos de extremidade HTTP:

1. **Analisador de email** (`/parse_email_functionapp`)
   - Método: POST
   - Corpo: conteúdo bruto do email ou JSON com email codificado em Base64
   - Parâmetros opcionais: `max_depth` (default=10)
   - Retorno: dados analisados do email em formato JSON

2. **Limpador de JSON** (`/clean_json_functionapp`)
   - Método: POST
   - Corpo: conteúdo JSON (pode incluir notação Markdown)
   - Retorno: JSON limpo, com a notação Markdown removida e os valores nulos substituídos

3. **Gerador de relatórios HTML** (`/generate_html_report_functionapp`)
   - Método: POST
   - Corpo: JSON da análise de phishing
   - Retorno: relatório HTML formatado

4. **Extrator de expressão regular** (`/extract_regex_functionapp`)
   - Método: POST
   - Corpo: JSON com os campos `pattern` e `subject`
   - Retorno: resultados correspondentes em formato JSON

## Recursos de análise de email

### Compatibilidade com formatos de email
- Emails MIME comuns (text/plain, text/html)
- Emails inseridos (message/rfc822)
- Anexos TNEF (winmail.dat)
- Anexos de arquivo EML e MSG
- Emails encaminhados por vários clientes de email (Gmail, Outlook, Apple Mail)
- Emails de phishing relatados pelo Proofpoint

### Extração de conteúdo
- Análise completa de cabeçalhos
- Conteúdo do corpo em texto sem formatação e HTML
- Extração e normalização de URLs
- Extração de domínios
- Extração de endereços IP
- Processamento de anexos

### Tratamento de anexos
- Extração de texto de PDF
- Extração de conteúdo do Excel (com vários métodos alternativos)
- Anexos de email (análise recursiva)
- Hash SHA256 para verificação de anexos

### Processamento de URLs
- Decodificação de URLs do Microsoft SafeLinks
- Decodificação de URLs do Proofpoint URLDefense
- Expansão de encurtadores de URL
- Remoção de URLs base duplicadas em casos de grande volume

## Recursos

- Monitoramento e análise automatizados de emails
- Avaliação detalhada de segurança usando o Security Copilot
- Classificação de emails (phishing, spam, legítimo, suspeito)
- Geração de relatórios HTML
- Integração opcional com incidentes do Sentinel
- Compatibilidade com emails inseridos e cadeias complexas de encaminhamento
- Extração e análise abrangentes de URLs e domínios

## Observações de segurança

- A solução usa identidades gerenciadas pelo sistema para acesso seguro
- Revise e configure as opções de segurança da conta de armazenamento de acordo com a política da sua empresa
- Garanta as permissões mínimas necessárias para todas as conexões
- Atualize regularmente as dependências do Function App
- O analisador de email usa `CustomEmailPolicy` para tratar problemas comuns de análise, como cabeçalhos Message-ID malformados

## Depuração e registro em log

O aplicativo usa o módulo `logging` do Python com o nível DEBUG habilitado e fornece logs abrangentes para solução de problemas. Cada função principal inclui registros detalhados para ajudar a diagnosticar problemas durante a implantação e a operação.

## Limitações

- A extração de PDF requer a biblioteca pdfminer.six
- O processamento do Excel pode exigir várias bibliotecas (pandas, openpyxl, xlrd)
- A expansão de URLs tem limites de taxa para evitar bloqueios
- Casos com grande volume de URLs removem automaticamente as duplicatas, mantendo as URLs base
- Endereços IP privados/locais são excluídos da extração de IPs
