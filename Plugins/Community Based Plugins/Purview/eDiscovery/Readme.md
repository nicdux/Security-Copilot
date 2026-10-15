# Plugin do eDiscovery para o Security Copilot
Autor: Amit Singh

Este plugin personalizado do Security Copilot aprimora os recursos de eDiscovery da organização no Microsoft Purview. Ele foi desenvolvido para fluxos de trabalho em que você cria um caso e exporta os artefatos diretamente. É possível iniciar uma exportação em Search após indexar e estimar os artefatos. No entanto, o plugin não oferece suporte a fluxos de trabalho que associam pesquisas a um conjunto de revisão para análise adicional no eDiscovery. A associação de pesquisas a um conjunto de revisão é um processo manual que deve ser concluído no caso, no portal do Purview.

### Pré-requisitos para usar o Security Copilot

- **Verifique se o Security Copilot está habilitado**
  Antes de começar, verifique se o Security Copilot está habilitado em seu ambiente. Siga estas etapas de integração:
  [Introdução ao Security Copilot](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot#onboarding-to-microsoft-security-copilot)

- **Verifique seu acesso para carregar plugins personalizados**
  Para usar plugins personalizados, você precisa ter as permissões adequadas para carregá-los no Security Copilot. Saiba como gerenciar e habilitar esse recurso:
  [Gerenciamento de plugins personalizados](https://learn.microsoft.com/en-us/security-copilot/manage-plugins?tabs=securitycopilotplugin#managing-custom-plugins)

- **Configure as permissões necessárias para seu aplicativo**
  O aplicativo deve ter as seguintes permissões no Microsoft Graph (`https://graph.microsoft.com`):
  - `offline_access`  
  - `user.read`  
  - `eDiscovery.Read.All`  
  - `eDiscovery.ReadWrite.All`  

  Para registrar o aplicativo e configurar essas permissões, siga estas etapas:
  [Registrar um aplicativo no Entra ID](https://learn.microsoft.com/en-us/graph/auth-register-app-v2#register-an-application)

## Configurar o plugin personalizado no Security Copilot

### Carregar o plugin personalizado

1. **Baixar o arquivo necessário**
   - Obtenha o arquivo **[`eDiscovery_OAuth_API_manifest.yaml`](https://github.com/samitks77/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/Purview/eDiscovery/eDiscovery_OAuth_API_manifest.yaml)** no diretório especificado. Esse arquivo YAML será carregado no **Security Copilot** durante a configuração.
   
2. **Adicionar Client ID e Tenant ID**
   - Em **Entra ID App Registration**, adicione o **Client ID** e o **Tenant ID** antes de prosseguir com o carregamento.
   ![Client ID e Tenant ID do Entra ID](EntraID-ClientID-TenantID.png)
   
3. **Gerar e copiar o Secret Value**
   - Durante o carregamento do plugin no **Security Copilot**, você precisará de um **Secret Value** obtido em **Certificates & Secrets** no aplicativo do Entra ID.
   - Esse **Secret Value** funciona como a **chave de API** necessária ao funcionamento correto do plugin.
   - **Importante:** copie o **Secret Value** imediatamente após criá-lo. Se você sair da página, o valor não poderá mais ser lido.
     
     ![Secret Value do Entra ID](EntraID-SecretValue.png)

4. **Criar segredos no Entra ID**

   - Siga estas etapas para criar e gerenciar segredos para o aplicativo:
   **[`Como adicionar credenciais no Entra ID`](https://learn.microsoft.com/en-us/graph/auth-register-app-v2#add-credentials)**

5. **Acessar Custom Plugins**

   - Acesse **Manage Sources** na página inicial do **Security Copilot** e role até a seção **Custom Plugins**.

   ![Carregar plugins personalizados](scp-upload-custom-plugins.png)

   ![Segunda etapa para carregar plugins personalizados](scp-upload-custom-plugins-2.png)
6. **Carregar o arquivo do plugin**

   - Clique em **Security Copilot Plugin** e carregue o arquivo **`eDiscovery_OAuth_API_manifest.yaml`**.

   ![Carregar o manifesto de API do plugin](scp-upload-custom-plugins-api-manifest.png)

7.  **Inserir o Client Secret e conectar**
   
    - Cole o **Client Secret Value** obtido em **Entra ID App Registration**.
    - Clique em **Connect** para continuar.

     ![Segredo do Security Copilot](CfS-Secret.png)

8.  **Entrar**

    Depois de clicar em **Connect**, uma nova janela será aberta para que você entre com suas credenciais.

### Configuração do plugin concluída

Você configurou o **eDiscovery Plugin** no **Security Copilot** com sucesso. Com o plugin carregado, o Client ID, Tenant ID e Secret Value configurados e a autenticação concluída, a integração está pronta para uso. O Security Copilot agora pode usar esse plugin para ampliar os **recursos de eDiscovery**, simplificando as investigações e os processos de obtenção de dados. Se encontrar algum problema, verifique as configurações do Entra ID, confirme se o Client Secret é válido e confira as permissões do Security Copilot.

### Habilidades e prompts

🔹 **Estes são **prompts sugeridos** que você pode usar para interagir com o plugin no **Security Copilot**. Cada prompt ajuda a executar com eficiência determinadas **ações do eDiscovery**. Você pode modificá-los de acordo com seu caso de uso e os requisitos da organização. Abaixo, você encontrará os campos de entrada estruturados necessários para cada ação, garantindo a execução precisa das tarefas do eDiscovery. Para uma visualização mais clara e estruturada dos prompts, consulte a versão HTML:**

👉 **[`Prompts sugeridos em HTML`](https://htmlpreview.github.io/?https://raw.githubusercontent.com/samitks77/Copilot-For-Security/main/Plugins/Community%20Based%20Plugins/Purview/eDiscovery/sampleprompts.html)**





