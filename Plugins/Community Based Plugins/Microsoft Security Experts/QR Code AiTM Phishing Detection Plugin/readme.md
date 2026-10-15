# Plugin de detecção de phishing AiTM por código QR

## Introdução
Boas-vindas ao QR Code AiTM Phishing Detection Plugin! Este plugin aprimora seus esforços de segurança cibernética detectando e mitigando ataques de phishing por código QR. Com as informações do Defender Experts da Microsoft, o plugin oferece uma proteção robusta contra essas campanhas sofisticadas de phishing.

## Visão geral
O phishing AiTM (Adversary-in-the-Middle) por código QR é uma técnica em que os invasores exploram códigos QR para redirecionar os usuários a sites fraudulentos. Quando os usuários leem o código QR e se autenticam, os invasores podem roubar tokens de sessão e realizar atividades mal-intencionadas. Este plugin ajuda a identificar e evitar esses ataques monitorando padrões suspeitos de email, atributos de remetentes e o comportamento dos usuários para manter a organização segura.

Para obter informações mais detalhadas, consulte o artigo completo [aqui](https://techcommunity.microsoft.com/t5/microsoft-security-experts-blog/hunting-for-qr-code-aitm-phishing-and-user-compromise/ba-p/4053324).

## Pré-requisitos
- <span style="color:blue">**Instância do Copilot for Security**</span>
- <span style="color:blue">**Microsoft Defender for Endpoint**</span>

<span style="color:green">**Observação:** este plugin é baseado em KQL e usa consultas de busca nas tabelas do Defender para identificar comportamentos de risco e atividades suspeitas. As tabelas incluem CloudAppEvents, EmailEvents, EmailAttachmentInfo, AADSignIn etc.</span>

## Passo a passo orientado
Este guia apresenta as principais etapas para começar a usar a nova ferramenta. Primeiro, adicionaremos o plugin personalizado.
1. Acesse o [Security Copilot](https://securitycopilot.microsoft.com).
2. Baixe o arquivo YAML do QR Code AiTM Phishing Detection Plugin.
3. Selecione o ícone de plugins no canto inferior esquerdo.

![Plugin de detecção de phishing AiTM por código QR](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Security%20Experts/QR%20Code%20AiTM%20Phishing%20Detection%20Plugin/images/Picture1.png)

4. Em Custom upload, selecione **Upload plugin**.

![Plugin de detecção de phishing AiTM por código QR](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Security%20Experts/QR%20Code%20AiTM%20Phishing%20Detection%20Plugin/images/Picture2.png)

5. Selecione o plugin do Copilot for Security e carregue o QR Code AiTM Phishing Detection Plugin.

![Plugin de detecção de phishing AiTM por código QR](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Security%20Experts/QR%20Code%20AiTM%20Phishing%20Detection%20Plugin/images/Picture3.png)

6. Clique em **Add**.
7. O plugin será exibido em Custom.
![Plugin de detecção de phishing AiTM por código QR](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Security%20Experts/QR%20Code%20AiTM%20Phishing%20Detection%20Plugin/images/Picture4.png)



O pacote personalizado contém os seguintes prompts:


Em **QRCODE**, você encontrará:
![Plugin de detecção de phishing AiTM por código QR](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Security%20Experts/QR%20Code%20AiTM%20Phishing%20Detection%20Plugin/images/Picture5.png)



**Vamos começar a usá-lo em conjunto com os recursos do Copilot for Security**
