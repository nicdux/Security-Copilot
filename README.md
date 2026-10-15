![Logotipo do Security Copilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)
# Comunidade do Microsoft Security Copilot
Boas-vindas ao repositório do Security Copilot!

O Microsoft Security Copilot é um assistente baseado em IA generativa para operações diárias de segurança e TI, que permite às equipes oferecer proteção na velocidade e na escala da IA.
- https://learn.microsoft.com/pt-br/security-copilot/
- https://learn.microsoft.com/pt-br/security-copilot/get-started-security-copilot
- https://learn.microsoft.com/en-us/security-copilot/plugin_overview
- https://learn.microsoft.com/pt-br/security-copilot/connectors-overview
- https://aka.ms/copilotforsecurity

## Como contribuir
Este projeto aceita contribuições e sugestões. A maioria das contribuições exige que você aceite um Contrato de Licença de Colaborador (Contributor License Agreement — CLA), declarando que tem o direito de nos conceder, e de fato nos concede,
os direitos de uso da sua contribuição. Para obter detalhes, acesse https://cla.opensource.microsoft.com.

Quando você enviar uma pull request (solicitação de pull), um bot de CLA determinará automaticamente se é necessário fornecer um CLA e identificará a PR adequadamente (por exemplo, com uma verificação de status ou um comentário). Basta seguir as instruções
fornecidas pelo bot. Você precisará fazer isso apenas uma vez para todos os repositórios que usam nosso CLA.

Este projeto adotou o [Código de Conduta de Código Aberto da Microsoft](https://opensource.microsoft.com/codeofconduct/).
Para obter mais informações, consulte as [Perguntas frequentes sobre o Código de Conduta](https://opensource.microsoft.com/codeofconduct/faq/) ou entre em contato pelo e-mail [opencode@microsoft.com](mailto:opencode@microsoft.com) caso tenha outras dúvidas ou comentários.

Estas são as etapas para começar a contribuir com o projeto:

**Conta do GitHub**:
- Crie uma conta do GitHub em ([www.github.com](http://www.github.com)) — uma conta gratuita é suficiente.
- Entre com sua nova conta
  
**Crie um fork do repositório**:
- Acesse a página da comunidade: https://github.com/Azure/Copilot-For-Security
- Verifique se você está na branch master
- Clique em "Fork" -> "Create a new fork"
  ![Novo fork no GitHub](https://github.com/Azure/Copilot-For-Security/blob/main/Images/CFSGithubfork.png)
  ![Criar novo fork](https://github.com/Azure/Copilot-For-Security/blob/main/Images/CFSGithubforkCreate.png)
- Isso criará uma cópia do repositório do Security Copilot na sua conta do GitHub:
  ![Ver seu novo fork](https://github.com/Azure/Copilot-For-Security/blob/main/Images/CFSGithubforknew.png)

**Clone o fork em seu computador local**:
- Se ainda não tiver o Git Bash, instale-o por meio de https://git-scm.com/downloads
- Crie um diretório no computador local no qual você baixará o repositório e trabalhará.
    Exemplo: “C:\Users\(username)\Documents\GitForks”
- Abra o Git Bash e acesse o diretório “C:\Users\(username)\Documents\GitForks”
- Execute: Git init
- Execute: Git clone <url of your fork> example: Git clone “https://github.com/(username)/ Copilot-For-Security-Fork”
- Acesse o novo diretório criado, por exemplo: cd Copilot-For-Security-Fork
- Configure como upstream o repositório original do qual o fork foi criado, isto é, o repositório da comunidade do Copilot-For-Security
- Execute: Git remote add upstream https://github.com/Azure/Copilot-For-Security
- Execute: Git remote -v

  ![Clonar em um diretório local](https://github.com/Azure/Copilot-For-Security/blob/main/Images/Clonethefork.png)

Você também pode fazer isso com o GitHub Desktop, disponível em https://desktop.github.com

**Crie uma branch**:
- Você pode trabalhar com a branch main local, mas é recomendável usar uma branch para manter isolados os diferentes projetos em que estiver trabalhando.
- Primeiro, sincronize o repositório local com a branch master do upstream (a própria comunidade do Azure, não o seu fork)
    Execute: git pull upstream main
- Você verá uma lista das atualizações processadas ou uma mensagem informando que tudo está atualizado
- Após a sincronização, crie sua nova branch
    Execute: Git checkout -b <branch name> example Git checkout -b Sojeshs_CFSContributions

![Criar nova branch](https://github.com/Azure/Copilot-For-Security/blob/main/Images/Createnewbranch.png)

**Instale o VS Code:**

[[Baixar o Visual Studio Code — Mac, Linux e Windows](https://code.visualstudio.com/Download)]

**Abra a branch no VS Code:**

Inicie o VS Code, selecione File > Open Folder e abra o diretório do repositório local (exemplo: C:\Users\\(username)\Documents\GitForks\Copilot-For-Security-Fork).

Você verá todos os diretórios e arquivos do repositório. Na parte inferior, é possível conferir em qual branch você está trabalhando. Antes de fazer qualquer alteração, verifique se a branch correta está selecionada.

![Seleção da branch](https://github.com/Azure/Copilot-For-Security/blob/main/Images/VSCodeBranchConfirmation.png)

**Prepare, confirme e publique suas alterações**

Depois de criar o conteúdo desejado no VS Code, será necessário preparar (stage) e confirmar (commit) as alterações. Elas serão confirmadas na branch criada localmente em seu computador. Por exemplo, foi criada uma pasta chamada "SentinelDailyOperations" e um plugin KQL chamado “KQL_SentinelDailyOperationsSample.yml” dentro do diretório "Community Based Plugins". Você também pode adicionar qualquer conteúdo necessário para documentar e implantar esse plugin.

![Seleção da branch](https://github.com/Azure/Copilot-For-Security/blob/main/Images/CFSGithubCreateNewContent.png)

Quando estiver tudo pronto para confirmar as alterações, clique no ícone Source Control à esquerda, insira uma mensagem que resuma as mudanças e clique em “+”. Isso prepara as alterações. Em seguida, clique na marca de seleção para confirmá-las. Nesse momento, elas ainda estão apenas no computador local.
![Seleção da branch](https://github.com/Azure/Copilot-For-Security/blob/main/Images/CFSGithubCreateNewContentStageandCommit.png)

![Seleção da branch](https://github.com/Azure/Copilot-For-Security/blob/main/Images/CFSGithubCreateNewContentCommitChanges.png)

Agora, você pode publicar esse trabalho em seu GitHub pessoal clicando no ícone ao lado do nome da branch. Se aparecer uma lista de repositórios na parte superior, selecione o seu, <youraccount>/Copilot-For-Security, e *NÃO* Azure/Copilot-For-Security. Neste exemplo, selecionamos a própria branch main para publicar as alterações com o novo plugin.

![Seleção da branch](https://github.com/Azure/Copilot-For-Security/blob/main/Images/CFSPushChangestoYourGithub.png)

Agora, você pode revisar as alterações confirmadas no GitHub acessando a branch correspondente:
![Seleção da branch](https://github.com/Azure/Copilot-For-Security/blob/main/Images/CFSSeeYourGithubCommittedChanges.png)

Se o trabalho estiver concluído e pronto para envio ao repositório principal, será necessário abrir uma pull request. Essa solicitação iniciará um conjunto de verificações automatizadas. Se todas forem aprovadas, a solicitação seguirá para um grupo de revisores, e um deles deverá revisar seu trabalho, aceitar a solicitação e mesclá-la à branch master.

![Seleção da branch](https://github.com/Azure/Copilot-For-Security/blob/main/Images/CFSUpdateChangestoMainRepository.png)

A parte superior da página "Open a pull request" é essencial. Ela mostra de qual repositório e branch vêm as alterações e para qual repositório elas serão enviadas. Preencha a seção de comentários com um título significativo e uma lista do que foi feito, pois o revisor lerá essas informações. Em seguida, clique em “Create pull request”.

![Seleção da branch](https://github.com/Azure/Copilot-For-Security/blob/main/Images/CFSSeeChangesandCommitMainRepository.png)

![Seleção da branch](https://github.com/Azure/Copilot-For-Security/blob/main/Images/CFSCreaePullRequestFinal.png)

Depois que as alterações forem mescladas ao GitHub principal, elas ficarão visíveis no repositório principal do GitHub.

![Seleção da branch](https://github.com/Azure/Copilot-For-Security/blob/main/Images/CFSMergePullRequesttoMainGithub.png)

**Confira o status da pull request e sincronize com o repositório principal**

Depois que a pull request for mesclada, confirme se ela foi incorporada ao repositório principal. Recomendamos verificar tanto no site do GitHub quanto por meio de uma sincronização com o repositório local, garantindo que as alterações estejam presentes.


**Boa sorte e boas contribuições para a comunidade do Security Copilot!**
