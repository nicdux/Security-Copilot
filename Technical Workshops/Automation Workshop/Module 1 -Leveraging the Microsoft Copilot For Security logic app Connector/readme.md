## Aproveitando o conector do aplicativo lógico do Microsoft Security Copilot

![Logotipo do Security CoPilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)

#### ⌛ Tempo estimado para concluir este laboratório: 15 minutos
#### 🎓 Nível: 100 (iniciante)

Documentação do conector do aplicativo lógico: [Link](https://learn.microsoft.com/en-us/security-copilot/connector_logicapp)

#### Objetivos
Ao concluir este guia técnico, você terá as seguintes habilidades:<br>

* Implantar um Azure Logic App capaz de processar prompts do Microsoft Security Copilot usando o conector do aplicativo lógico.<br>

#### Pré-requisitos
Para concluir esta tarefa com êxito, você precisa atender aos seguintes pré-requisitos:<br>

1. Você precisa ter seu próprio locatário e uma instância do Microsoft Security Copilot.<br>
2. **Assinatura do Azure**: você precisa de uma [assinatura do Azure](https://azure.microsoft.com/en-us/free/) ativa para criar e implantar um Logic App.
3. **Grupo de recursos do Azure**: os Logic Apps são implantados em [grupos de recursos do Azure](https://docs.microsoft.com/en-us/azure/azure-resource-manager/management/manage-resource-groups). Verifique se você já criou um grupo de recursos adequado ou crie um durante o processo de implantação.
4. **Permissões de acesso**: verifique se você tem as [permissões](https://docs.microsoft.com/en-us/azure/role-based-access-control/overview) necessárias para criar recursos na assinatura e no grupo de recursos do Azure em que pretende implantar o Logic App.

#### Etapas a seguir

### 1. Criar um recurso de aplicativo lógico de Consumo hospedado nos Azure Logic Apps multilocatário

- Na caixa de pesquisa do portal do Azure, insira Logic Apps e selecione Logic Apps.
![Imagem do Logic App](https://github.com/Azure/Copilot-For-Security/raw/main/Images/Logicapp%20images/logicapp1.png)
- Na barra de ferramentas da página Logic Apps, selecione Adicionar.
- Na página Criar Aplicativo Lógico, primeiro selecione o tipo de Plano para o recurso de aplicativo lógico. Assim, somente as opções desse tipo de plano serão exibidas.
- Quando terminar, suas configurações serão semelhantes ao exemplo a seguir:
![Imagem do Logic App](https://github.com/Azure/Copilot-For-Security/raw/main/Images/Logicapp%20images/logicapp2.png)
- Quando estiver tudo pronto, selecione Examinar + criar.
- Na página de validação exibida, confirme todas as informações fornecidas e selecione Criar.

### 2. Selecionar o modelo de fluxo de trabalho de aplicativo lógico em branco
- Depois que o Azure implantar com êxito o recurso de aplicativo lógico, selecione Ir para o recurso. Como alternativa, localize e selecione o recurso digitando seu nome na caixa de pesquisa do Azure.
![Imagem do Logic App](https://github.com/Azure/Copilot-For-Security/raw/main/Images/Logicapp%20images/logicapp3.png)
- Role para baixo, passe pelo vídeo e pela seção chamada Começar com um gatilho comum.
- Em Modelos, selecione Aplicativo Lógico em Branco.
![Imagem do Logic App](https://github.com/Azure/Copilot-For-Security/raw/main/Images/Logicapp%20images/logicapp4.png)

### 3. Adicionar um gatilho que especifique quando executar o fluxo de trabalho
- No designer de fluxo de trabalho, selecione um gatilho.
![Imagem do Logic App](https://github.com/Azure/Copilot-For-Security/raw/main/Images/Logicapp%20images/logicapp5.png)
- Escolha o gatilho Recorrência e defina que o aplicativo lógico deve ser iniciado uma vez por dia.
![Imagem do Logic App](https://github.com/Azure/Copilot-For-Security/raw/main/Images/Logicapp%20images/logicapp6.png)

### 4. Adicionar o conector do aplicativo lógico do Security Copilot ao fluxo de trabalho
- Selecione o conector do aplicativo lógico do Security Copilot.
![Imagem do Logic App](https://github.com/Azure/Copilot-For-Security/raw/main/Images/Logicapp%20images/logicapp7.png)
- Autentique o conector do aplicativo lógico do Security Copilot.
- Adicione contexto ao prompt.

![Imagem do Logic App](https://github.com/Azure/Copilot-For-Security/raw/main/Images/Logicapp%20images/logicapp9.png)
- Examine os parâmetros no conector do aplicativo lógico do Security Copilot.
![Imagem do Logic App](https://github.com/Azure/Copilot-For-Security/raw/main/Images/Logicapp%20images/logicapp8.png)

Parâmetros e entradas opcionais:

Prompt Content: prompt a ser avaliado
- Session Id: contexto da sessão
- Skill Inputs: corpo JSON opcional que especifica valores para os parâmetros obrigatórios do plugin (habilidade)
- Skill Name: chama diretamente uma habilidade (ignora o planejador)
- Skillsets: chama diretamente um conjunto de habilidades (ignora o planejador)
- Salve o fluxo de trabalho.

### 5. Executar o fluxo de trabalho
- Execute o fluxo de trabalho (êxito).

### 6. Exibir o resultado do fluxo de trabalho no conector do aplicativo lógico e no portal autônomo