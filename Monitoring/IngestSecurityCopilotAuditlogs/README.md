# Ingerir logs de auditoria do Microsoft Security Copilot e implantar a pasta de trabalho de auditoria
Blog da comunidade técnica: [Monitorar atividades de usuários e eventos do sistema com o Security Copilot](https://techcommunity.microsoft.com/blog/securitycopilotblog/monitor-user-activities-and-system-events-with-security-copilot-and-microsoft-se/4303368)

A auditoria é um recurso essencial em qualquer solução de segurança, pois oferece visibilidade das atividades dos usuários e dos eventos do sistema, permite detectar anomalias de uso e atividade e ajuda a garantir a conformidade com requisitos regulatórios. Ao enviar os logs de auditoria do Copilot for Security para seu SIEM nativo de nuvem, o Microsoft Sentinel, os usuários podem obter informações mais detalhadas sobre o uso do Security Copilot e tomar medidas proativas para reduzir os riscos.

# Pré-requisitos
### Habilitar o recurso de log de auditoria no Security Copilot
Durante a experiência da primeira execução, um Security Administrator pode optar por permitir que o Microsoft Purview acesse, processe, copie e armazene ações de administradores, ações de usuários e respostas do Copilot. Para obter mais informações, consulte a introdução ao Security Copilot.

Os Security Administrators também podem acessar essa opção na página de configurações de Owner.

Siga estas etapas para atualizar as configurações do log de auditoria:

1. Entre no Microsoft Security Copilot (https://securitycopilot.microsoft.com).
2. Selecione o ícone do menu inicial.
3. Acesse Owner settings > Logging audit data in Microsoft Purview.
![Security Copilot](./images/cfs_setting_1.png)<br>  

### Habilitar os logs do Microsoft Defender for Cloud Apps pelo conector de dados do Microsoft Defender XDR
Para integrar ao Microsoft Defender XDR, verifique se você tem:
1. Workspace do Sentinel Log Analytics: permissões de leitura e gravação.
2. Controle de acesso ao conector: o usuário que aplicar alterações ao conector deve ser membro do Microsoft Entra ID associado ao locatário ao qual o workspace pertence.
3. Permissões do locatário: 'Global Administrator' ou 'Security Administrator' no locatário do workspace.
4. Licença: M365 E5, M365 A5 ou qualquer outra licença qualificada para o Microsoft Defender XDR.

![Microsoft Defender XDR](./images/sentinel_XDR.png)<br>  


### Implantar regras analíticas
[![Implantar no Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FSecurity-Copilot%2Fmain%2FMonitoring%2FIngestSecurityCopilotAuditlogs%2Fazuredeploy_analytics.json)
![Regras analíticas](https://github.com/user-attachments/assets/c0def0de-9fe0-41e8-9ec4-69866094fa55)


### Implantar a pasta de trabalho
[![Implantar no Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FSecurity-Copilot%2Fmain%2FMonitoring%2FIngestSecurityCopilotAuditlogs%2Fazuredeploy_workbook.json)
![Pasta de trabalho de auditoria](https://github.com/user-attachments/assets/ea8f42f4-afb2-4bb2-9f9f-d9c4b44d0a31)
