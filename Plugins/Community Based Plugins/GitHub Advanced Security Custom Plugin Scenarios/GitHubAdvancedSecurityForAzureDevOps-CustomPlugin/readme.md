**Plugin personalizado do GitHub Advanced Security for Azure DevOps (GAzDO)**

O GitHub Advanced Security for Azure DevOps (GAzDO) executa verificação de código (teste estático de segurança de aplicações, ou SAST, por meio do CodeQL), análise do Dependabot (análise de composição de software, ou SCA) e verificação de segredos nos arquivos dos repositórios de organizações do Azure DevOps.
Esta pasta contém um plugin para o Security Copilot que consulta as APIs "List" e "Get" expostas pelo Azure DevOps e relacionadas ao Advanced Security (GAzDO).

Instruções
- No Azure DevOps, crie um Personal Access Token (PAT). Atribua a ele pelo menos o escopo "Read" em "Advanced Security".
- Gere a versão em Base64 da cadeia de caracteres "Basic:<your-personal-access-token>". Por exemplo, use este comando do PowerShell:
  [System.Convert]::ToBase64String([System.Text.Encoding]::UTF8.GetBytes("Basic:<your-personal-access-token>"))
- Baixe o arquivo *Manifest.yaml desta pasta.
- Crie o plugin personalizado no Security Copilot carregando esse arquivo de manifesto.
- Após o carregamento, configure o plugin personalizado definindo os dois parâmetros solicitados: o nome da organização no Azure DevOps (escreva-o no final da URL proposta) e a versão em Base64 do Personal Access Token criado conforme descrito acima.
- Agora você pode usar as habilidades disponíveis neste plugin.

Autor da versão inicial:
Stefano Pescosolido
https://linkedin.com/in/stefanopescosolido
