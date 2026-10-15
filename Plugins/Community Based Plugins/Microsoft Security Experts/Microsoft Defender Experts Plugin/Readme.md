![Logotipo do Defender Experts](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Security%20Experts/Microsoft%20Defender%20Experts%20Plugin/Images/LogoDex.png)

# Introdução

Boas-vindas ao **Defender Experts for Hunting Plugin**! Este plugin eleva sua postura de segurança cibernética ao fornecer busca proativa de ameaças em todo o ambiente da organização, incluindo o Office 365, aplicativos de nuvem e plataformas de identidade. Com as informações de especialistas experientes em segurança da Microsoft, o plugin permite que sua equipe detecte e responda rapidamente a ameaças avançadas.

# Visão geral

O Defender Experts for Hunting é um serviço proativo de busca de ameaças que vai além dos pontos de extremidade tradicionais e abrange o Office 365, aplicativos de nuvem e plataformas de identidade. Nossos especialistas experientes em segurança procuram ativamente ameaças no ambiente da organização, investigam anomalias e fornecem alertas contextuais detalhados com instruções claras de correção, permitindo respostas rápidas e eficazes.

Realizamos análises aprofundadas para descobrir ameaças avançadas e avaliar o alcance e o impacto de atividades mal-intencionadas, especialmente aquelas que envolvem adversários humanos ou ataques hands-on-keyboard. Um importante resultado do serviço é o compartilhamento das consultas de busca avançada desenvolvidas durante as análises, permitindo que sua equipe procure proativamente ameaças semelhantes e aprimore a mitigação de riscos.

Além disso, por meio do Copilot for Security, integramos nossas descobertas às ferramentas automatizadas para melhorar sua capacidade de descoberta e priorização, garantindo que suas defesas evoluam continuamente diante dos novos desafios de segurança.

# Pré-requisitos

- **Capacidade do Copilot for Security**
- **Microsoft Defender for Endpoint**

> **Observação:** este plugin é baseado em KQL e usa consultas de busca avançada para verificar comportamentos de risco e atividades suspeitas nas tabelas do Defender. As tabelas incluem `CloudAppEvents`, `EmailEvents`, `EmailAttachmentInfo`, `AADSignIn`, entre outras.

# Passo a passo orientado

Este guia apresenta as principais etapas para começar a usar a nova ferramenta. Primeiro, adicionaremos o plugin personalizado.

1. **Acesse o Security Copilot**

    ![Página principal do DEX](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Security%20Experts/Microsoft%20Defender%20Experts%20Plugin/Images/mainpageDex.png)


2. **Baixe o plugin Defender Experts do GitHub**

3. **Selecione o ícone de plugins no canto inferior esquerdo**

4. **Em Custom upload, selecione _Upload plugin_**

    ![Carregar o plugin DEX](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Security%20Experts/Microsoft%20Defender%20Experts%20Plugin/Images/uploadpluginDex.png)


5. **Selecione o plugin do Copilot for Security e carregue o plugin DEX**

    ![Carregar o plugin DEX](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Security%20Experts/Microsoft%20Defender%20Experts%20Plugin/Images/uploadpluginDex.png)


6. **Clique em _Add_**

7. **O plugin será exibido em Custom**

    ![Visualizar o plugin DEX](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Security%20Experts/Microsoft%20Defender%20Experts%20Plugin/Images/ViewPluginDex.png)


8. **O pacote personalizado contém os seguintes prompts:** **em DEX, você encontrará:**

    ![Habilidades do DEX](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Microsoft%20Security%20Experts/Microsoft%20Defender%20Experts%20Plugin/Images/SkillsDex.png)


Vamos começar a usá-lo em conjunto com os recursos do Copilot for Security.
