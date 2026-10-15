# Obter as vulnerabilidades mais recentes da CISA e verificar os dispositivos da minha organização
Autor: Jamil Mirza
Esta solução verifica o feed mais recente da CISA a cada 24 horas e consulta a ocorrência da CVE nos dispositivos do Microsoft Defender for Endpoint. O Security Copilot verifica as ações de correção e enriquece a descrição. Ele também informa quantos dispositivos da sua organização, caso existam, estão vulneráveis à CVE relatada. Por fim, um email com as descobertas é enviado para uma caixa de correio que pode ser alterada após a instalação do Logic App.

## Implantar a solução

### Etapa 1: implantar o Logic App

Clique no botão abaixo para implantar o Logic App. Selecione o grupo de recursos e altere o nome do Playbook, se necessário. Essas informações serão inseridas na tela de implantação.

[![Implantar no Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FSecurity-Copilot%2Fmain%2FLogic%2520Apps%2FLatestCISAVulnerabilities%2FCISALogicApp.json)

### Etapa 2: inicializar as conexões de API do O365 e do Security Copilot

Abra o novo Logic App.

Clique em "API Connections".

![Conexões de API](image-2.png)

Autorize as duas conexões de API.
![Autorização das conexões de API](image-1.png)

### Etapa 3: alterar o endereço de email

Abra o novo Logic App.

1. Clique em "Logic App Designer" (localizado em "Development Tools").

2. Clique em "Parameters".

3. Altere o valor padrão para um endereço de email de sua escolha.

![Configuração do endereço de email](image-3.png)

### Etapa 4: notificação por email

Abaixo está um exemplo do email recebido para cada descoberta.

![Exemplo de notificação por email](image-5.png)
