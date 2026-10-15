**Plugins personalizados do GitHub Advanced Security (GhAS)**

O GitHub Advanced Security (GhAS) executa verificação de código (teste estático de segurança de aplicações, ou SAST, por meio do CodeQL), análise do Dependabot (análise de composição de software, ou SCA) e verificação de segredos nos arquivos dos repositórios de usuários e organizações do GitHub.
Esta pasta contém dois plugins para o Security Copilot:
- O plugin "GitHub Advanced Security for GitHub Organizations" possui habilidades para listar todos os alertas resultantes da análise do GhAS em todos os repositórios de uma organização. Ele chama a API https://api.github.com/orgs/Org-Name no GitHub.
- O plugin "GitHub Advanced Security for GitHub Repositories" possui habilidades para listar todos os alertas resultantes da análise do GhAS em um repositório específico de uma organização. Ele também pode obter os detalhes de cada alerta e ler a configuração do CodeQL em um repositório específico. Ele chama a API https://api.github.com/repos/Org-Name no GitHub.

Instruções
- No GitHub, crie um Personal access token do tipo "classic". Atribua a ele pelo menos o escopo "repo" / "security_events".
- Baixe os dois arquivos *Manifest.yaml desta pasta.
- Crie os dois plugins personalizados no Security Copilot, um após o outro, carregando os dois arquivos de manifesto.
- Após cada carregamento, configure cada plugin personalizado definindo os dois parâmetros solicitados: o nome da organização no GitHub (escreva-o no final da URL proposta) e o Personal access token (chave) criado no GitHub.
- Agora você pode usar as habilidades disponíveis nesses dois plugins.

Para obter orientações detalhadas, passo a passo, e demonstrações, consulte https://www.linkedin.com/pulse/copilot-security-custom-plugin-github-advanced-stefano-pescosolido-vrcpf/?trackingId=asq05nvu75FGTlUOJYBw6w%3D%3D

Observação:
- Nesta versão prévia inicial, todas as habilidades exigem que um parâmetro "User-Agent" seja especificado na entrada. Essa é uma solução temporária para garantir que o Security Copilot grave esse parâmetro no cabeçalho das chamadas às APIs do GitHub (sem esse cabeçalho, as APIs retornam acesso negado). **Você pode definir qualquer valor nesse parâmetro** (o valor não é relevante). Em geral, basta defini-lo uma vez por sessão; nos prompts seguintes, o Copilot pressupõe que o valor permanece o mesmo.

Autor da versão inicial:
Stefano Pescosolido
https://linkedin.com/in/stefanopescosolido
