![Visão geral do Security Copilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)
# Microsoft Security Copilot Logic Apps
Documentação: https://learn.microsoft.com/en-us/copilot/security/connector-logicapp

O conector dos Logic Apps para o Microsoft Security Copilot permite chamar o Microsoft Security Copilot a partir de um fluxo de trabalho dos Logic Apps. Este documento apresenta as novas ações do conector que você pode usar, além de exemplos de casos de uso que podem ser implantados para automatizar investigações, como incidentes do Sentinel, phishing por email e outros.

A primeira versão do conector dos Logic Apps oferece duas ações:

- Evaluate Prompt — dado um prompt em linguagem natural, esta ação inicia uma nova avaliação no Microsoft Security Copilot e retorna a saída ao fluxo de trabalho do Logic App. O usuário pode fornecer um sessionId opcional, que incluirá o contexto relevante da sessão na avaliação realizada. Se sessionId for omitido, a ação criará uma nova sessão.

- Evaluate Direct Skill — dado um prompt em linguagem natural, o nome de uma habilidade e as entradas obrigatórias da habilidade, inicia uma nova avaliação e retorna sua saída. Use esta ação quando souber exatamente qual habilidade do Microsoft Security Copilot é necessária para a tarefa. Esta ação também permite fornecer um sessionId.

As ações "Evaluate Prompt" e "Evaluate Direct Skill" permitem que o usuário defina um sessionId opcional para executar a avaliação no contexto de uma sessão existente. Se ele for omitido, uma nova sessão será criada para a investigação.

# O que você encontrará aqui:
Aqui há diversos playbooks alinhados a cenários de segurança cibernética com os seguintes objetivos:
- Detecção aprimorada de ameaças: a automação pode analisar rapidamente grandes volumes de dados de segurança para detectar ameaças que poderiam passar despercebidas.
- Resposta proativa: playbooks automatizados permitem respostas imediatas a incidentes de segurança, reduzindo a janela de oportunidade dos invasores.
- Monitoramento contínuo: a automação permite monitorar eventos de segurança em tempo real, facilitando a rápida identificação e redução de possíveis riscos.
- Redução de erros humanos: a automação de tarefas repetitivas reduz significativamente o risco de erro humano nas operações de segurança cibernética.
- Resposta aprimorada a incidentes: playbooks automatizados facilitam respostas coordenadas e consistentes a incidentes de segurança, garantindo uma resolução eficiente.
- Escalabilidade: a automação permite ampliar as operações de segurança cibernética com eficiência, acompanhando o crescimento do volume de ameaças e dados.
- Automação da conformidade: processos automatizados ajudam a garantir o cumprimento de normas e padrões de segurança cibernética, reduzindo os riscos de conformidade.
- Otimização de recursos: ao automatizar tarefas rotineiras, os profissionais de segurança cibernética podem se concentrar em iniciativas estratégicas e na busca proativa de ameaças.

**Aviso de isenção de responsabilidade**: os Logic Apps fornecidos são exemplos destinados ao uso com o Security Copilot. Recomendamos que os usuários personalizem essas amostras para atender a seus requisitos específicos. Elas devem servir como orientação e inspiração para criar Logic Apps personalizados para uso próprio.

**Aviso técnico: Logic Apps, uso de SCUs e práticas recomendadas**

**Atenção, clientes!**

Ao usar Logic Apps no Copilot, esteja ciente de que isso pode aumentar o consumo de Secure Compute Units (SCUs). Recomendamos monitorar atentamente o uso de SCUs para otimizar o gerenciamento de recursos.