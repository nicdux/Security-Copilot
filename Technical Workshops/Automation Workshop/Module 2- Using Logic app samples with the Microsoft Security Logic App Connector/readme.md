## Aproveitando o conector do aplicativo lógico do Microsoft Security Copilot

![Logotipo do Security CoPilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)

#### ⌛ Tempo estimado para concluir este laboratório: 30 minutos
#### 🎓 Nível: 200 (do proficiente ao especialista)

Documentação do conector do aplicativo lógico: [Link](https://learn.microsoft.com/en-us/security-copilot/connector_logicapp)

#### Objetivos
Ao concluir este guia técnico, você terá as seguintes habilidades:

* Implantar um Azure Logic Apps capaz de processar prompts do Microsoft Security Copilot usando o conector do aplicativo lógico.
* Aproveitar o GitHub do Microsoft Security Copilot para acessar exemplos de aplicativos lógicos para testes.

#### Pré-requisitos
Para concluir esta tarefa com êxito, você precisa atender aos seguintes pré-requisitos:

1. Você precisa ter seu próprio locatário e uma instância do Microsoft Security Copilot.
2. **Assinatura do Azure**: você precisa de uma [assinatura do Azure](https://azure.microsoft.com/en-us/free/) ativa para criar e implantar um Logic App.
3. **Grupo de recursos do Azure**: os Logic Apps são implantados em [grupos de recursos do Azure](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups). Verifique se você já criou um grupo de recursos adequado ou crie um durante o processo de implantação.
4. **Permissões de acesso**: verifique se você tem as [permissões](https://docs.microsoft.com/en-us/azure/role-based-access-control/overview) necessárias para criar recursos na assinatura e no grupo de recursos do Azure em que pretende implantar o Logic App.
5. **ACESSO ao GitHub do Security Copilot:** verifique se você tem acesso ao [repositório público](https://github.com/Azure/Copilot-For-Security/tree/main), no qual encontrará os exemplos de aplicativos lógicos.

#### Etapas a seguir
Agora que iniciamos com êxito um Logic App usando o conector do Security Copilot no módulo anterior, podemos avançar para os exemplos disponíveis em nosso [repositório público](https://github.com/Azure/Copilot-For-Security/tree/main). Esses exemplos abrangem diversos cenários de segurança. Neste módulo, vamos nos concentrar em dois cenários específicos.

---

#### **Cenário 1: boletim de artigos sobre ameaças**

Neste workshop técnico, os participantes aprenderão a implantar um Logic App desenvolvido para produzir boletins de ameaças com informações do Microsoft Defender Threat Intelligence (MDTI) e enviá-los a um endereço de email específico. O workshop abordará o processo de configuração do Logic App para coletar informações de inteligência contra ameaças, criar boletins e automatizar a distribuição por email.

#### Etapas a seguir
- Acesse a pasta do aplicativo lógico no GitHub: [Azure Security Copilot - Logic Apps](https://github.com/Azure/Copilot-For-Security/tree/main/Logic%20Apps)
- Prossiga com a implantação.

## Implantação
[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FAzure%2FCopilot-For-Security%2Fmain%2FLogic%2520Apps%2FThreatBulletinCopilot%2Fazuredeploy.json)
### Instruções pós-implantação

1. Selecione a frequência com que deseja executar o Logic App.
2. Autentique os prompts do Copilot com um usuário que tenha acesso ao Security Copilot.
3. Execute o aplicativo lógico e aguarde os resultados.

#### Exibição do Logic App
![Logic App do boletim de ameaças](https://github.com/KwachSean/SecurityCopilot/raw/main/playbooks/ThreatBulletinCopilot/threatbulletinlogicapp.png)

#### Resultados do Logic App
![Imagem do boletim de ameaças](https://github.com/KwachSean/SecurityCopilot/raw/main/playbooks/ThreatBulletinCopilot/Threatbulletin.png)

---

#### **Cenário 2: Logic App de investigação do Sentinel**

Neste workshop técnico abrangente, os participantes explorarão o processo de implantação de um Logic App especializado. Ativar o botão "Implantar" iniciará a implantação de um Azure Logic App integrado às ações do Security Copilot, que usa um gatilho de incidente do Microsoft Sentinel. Esse Logic App alterará o status do incidente para ativo, gerará marcas dinâmicas (rótulos) e as acrescentará às marcas do incidente do Sentinel. Além disso, a automação determinará e ajustará a gravidade do incidente com base no enriquecimento do MDTI. Ela também documentará de modo abrangente as conclusões da investigação e a lógica por trás da classificação do incidente na seção de comentários do incidente do Microsoft Sentinel.

#### Etapas a seguir
- Acesse a pasta do aplicativo lógico no GitHub: [Azure Security Copilot - Logic Apps](https://github.com/Azure/Copilot-For-Security/tree/main/Logic%20Apps)
- Prossiga com a implantação.

## Implantação

Para implantar o aplicativo lógico acima:

* Selecione a opção Implantar, sua assinatura e o grupo de recursos (selecione o mesmo locatário em que o Security Copilot está habilitado).

[![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FYaniv-Shasha%2FSecurityCopilot%2Fmain%2FPlaybooks%2FCopilot-Sentinel_investigation-DynamicSev%2Fazuredeploy.json)

### Pós-implantação

* Autentique-se com os usuários mencionados acima (você pode usar usuários diferentes para as ações do Copilot e do Sentinel).
* Para executar o aplicativo lógico manualmente, abra a página de incidentes do Microsoft Sentinel, clique com o botão direito do mouse em um incidente específico e selecione Executar guia estratégico. Selecione o aplicativo lógico que acabou de implantar e clique em Executar.
* Para executar a lógica automaticamente, crie uma regra de automação no Sentinel e conecte este guia estratégico como ação da regra.

![Logic App de investigação do Sentinel](https://github.com/Yaniv-Shasha/SecurityCopilot/blob/ccbd305c539800eea2a1f7c1a0905aff954e2e25/Playbooks/Copilot-Sentinel_investigation-DynamicSev/images/full_logic_app.jpg)


---

#### **Módulo bônus: teste os guias estratégicos adicionais no GitHub e crie o seu**

- Acesse a pasta do aplicativo lógico no GitHub: [Azure Security Copilot - Logic Apps](https://github.com/Azure/Copilot-For-Security/tree/main/Logic%20Apps)

![Imagem do Logic App](https://github.com/Azure/Copilot-For-Security/raw/main/Images/Logicapp%20images/logicapp10.png)

- Prossiga com a implantação.