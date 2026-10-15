# <span class="c12">Integração do Cyware Respond (CFTR) com o Microsoft Security Copilot</span>

## <span class="c3">Introdução</span>

<span class="c2">O Cyware Fusion and Threat Response (Cyware Respond) é uma plataforma de automação de resposta a ameaças que combina fusão cibernética, orquestração avançada e automação. Ela permite que analistas de segurança enfrentem várias ameaças, incluindo malware, vulnerabilidades, incidentes, campanhas e agentes de ameaças. Por meio de bancos de dados de ameaças integrados, oferece recursos para gerenciar e responder a diversas ameaças de segurança.</span>

## <span class="c3">Instruções de configuração</span>

<span class="c2"></span>

1.  <span class="c2">Instalação</span>

*   <span class="c2">Localize o marketplace de plugins no Microsoft Security Copilot.</span>
*   <span class="c2">Pesquise "Cyware Respond" e instale o plugin.</span>

<span style="overflow: hidden; display: inline-block; margin: 0.00px 0.00px; border: 0.00px solid #000000; transform: rotate(0.00rad) translateZ(0px); -webkit-transform: rotate(0.00rad) translateZ(0px); width: 541.86px; height: 202.33px;">![](images/image1.png)</span>

2. <span class="c2">Configuração da instância do Cyware Respond</span>

*   <span class="c2">Entre em sua instância do Cyware Respond.</span>
*   <span class="c2">Acesse o Admin Panel do Cyware Respond.</span>
*   <span class="c2">Acesse Open APIs e crie um novo conjunto de credenciais OpenAPI.</span>
*   <span class="c2">Copie com segurança o token OpenAPI gerado.</span>

<span class="c2"></span>

3. <span class="c2">Configuração do plugin do Copilot</span>

*   <span class="c2">Acesse as configurações do plugin Cyware Respond (CFTR) no Microsoft Security Copilot.</span>
*   <span class="c2">Insira as seguintes informações:</span>

*   <span class="c2">Cyware Respond Instance URL: (por exemplo, [invalid URL removed])</span>
*   <span class="c2">API Token: (cole o token copiado)</span>

<span style="overflow: hidden; display: inline-block; margin: 0.00px 0.00px; border: 0.00px solid #000000; transform: rotate(0.00rad) translateZ(0px); -webkit-transform: rotate(0.00rad) translateZ(0px); width: 504.07px; height: 652.10px;">![](images/image2.png)</span>

4. <span class="c2">Salvar e testar</span>

*   <span class="c2">Clique em "Save" para aplicar sua configuração.</span>

5. <span>Depois de salvar, verifique se o plugin está ativo executando uma invocação ISV com</span> <span class="c8">/Cyware Respond</span><span class="c2"> e realizando uma ação simples de acordo com as diretrizes de uso da organização para confirmar que ele foi habilitado corretamente.</span>

<span class="c2"></span>

<span style="overflow: hidden; display: inline-block; margin: 0.00px 0.00px; border: 0.00px solid #000000; transform: rotate(0.00rad) translateZ(0px); -webkit-transform: rotate(0.00rad) translateZ(0px); width: 470.50px; height: 636.38px;">![](images/image3.png)</span>

## <span class="c3">Exemplos de uso</span>

### <span class="c6">Gerenciamento de incidentes</span>

<span class="c1">Consultar incidentes</span>

*   <span class="c0">"Pesquise incidentes relacionados a 'ransomware' no Cyware Respond."</span>
*   <span class="c0">"Localize incidentes que mencionem 'violação de dados' no Cyware Respond."</span>

<span class="c1">Obter detalhes de incidentes</span>

*   <span class="c0">"Obtenha no Cyware Respond os detalhes do incidente acima."</span>
*   <span class="c0">"Mostre mais informações sobre o incidente no Cyware Respond com o UUID <uuid>."</span>

### <span class="c6">Gerenciamento de ações</span>

<span class="c1">Consultar ações</span>

*   <span class="c0">"Consulte no Cyware Respond as ações desta semana marcadas com 'isolate'."</span>
*   <span class="c0">"Localize no Cyware Respond todas as ações de 'network scan' executadas ontem."</span>

<span class="c1">Detalhes da ação</span>

*   <span class="c0">"Obtenha no Cyware Respond os detalhes da última ação que discutimos."</span>
*   <span class="c0">"Forneça mais informações sobre a ação mencionada anteriormente no Cyware Respond."</span>

### <span class="c6">Gerenciamento de aplicativos</span>

<span class="c1">Consultar aplicativos</span>

*   <span class="c0">"Pesquise no Cyware Respond aplicativos com 'firewall' no nome."</span>
*   <span class="c0">"Localize no Cyware Respond ferramentas de segurança atualizadas recentemente."</span>

<span class="c1">Detalhes do aplicativo</span>

*   <span class="c0">"Obtenha no Cyware Respond os detalhes do aplicativo acima."</span>
*   <span class="c0">"Mostre os detalhes de configuração do aplicativo de segurança discutido anteriormente no Cyware Respond."</span>

### <span class="c6">Gerenciamento de ativos de software</span>

<span class="c1">Consultar ativos de software</span>

*   <span class="c0">"Liste os ativos de software críticos no Cyware Respond."</span>
*   <span class="c0">"Pesquise no Cyware Respond os softwares que precisam de atualização."</span>

<span class="c1">Detalhes do software</span>

*   <span class="c0">"Forneça no Cyware Respond os detalhes do último ativo de software mencionado."</span>
*   <span class="c0">"Obtenha no Cyware Respond as informações de versão do software que mencionamos anteriormente."</span>

### <span class="c6">Gerenciamento de campanhas</span>

<span class="c1">Consultar campanhas</span>

*   <span class="c0">"Localize no Cyware Respond todas as campanhas ativas relacionadas a 'phishing'."</span>
*   <span class="c0">"Pesquise no Cyware Respond campanhas recentes direcionadas a funcionários remotos."</span>

<span class="c1">Detalhes da campanha</span>

*   <span class="c0">"Obtenha no Cyware Respond os detalhes da campanha mencionada anteriormente."</span>
*   <span class="c0">"Mostre mais detalhes sobre essa campanha de ameaça cibernética no Cyware Respond."</span>

### <span class="c6">Gerenciamento de inteligência contra ameaças</span>

<span class="c1">Consultar inteligência contra ameaças</span>

*   <span class="c0">"Pesquise no Cyware Respond inteligência contra ameaças sobre 'ataques DDoS'."</span>
*   <span class="c0">"Obtenha no Cyware Respond as atualizações desta semana sobre 'grupos APT'."</span>

<span class="c1">Detalhes da inteligência contra ameaças</span>

*   <span class="c0">"Mostre os detalhes da última inteligência contra ameaças que discutimos no Cyware Respond."</span>
*   <span class="c0">"Forneça mais informações sobre o agente de ameaça mencionado anteriormente no Cyware Respond."</span>

### <span class="c6">Gerenciamento de malware</span>

<span class="c1">Consultar malware</span>

*   <span class="c0">"Localize no Cyware Respond todas as detecções de malware da última semana."</span>
*   <span class="c0">"Pesquise no Cyware Respond detecções de 'spyware' no departamento de marketing."</span>

<span class="c1">Detalhes do malware</span>

*   <span class="c0">"Forneça no Cyware Respond os detalhes do malware mencionado anteriormente."</span>
*   <span class="c0">"Preciso de mais informações sobre o 'ransomware' que identificamos no Cyware Respond."</span>

### <span class="c6">Gerenciamento de vulnerabilidades</span>

<span class="c1">Consultar vulnerabilidades</span>

*   <span class="c0">"Pesquise no Cyware Respond vulnerabilidades de alta severidade."</span>
*   <span class="c0">"Liste no Cyware Respond todas as vulnerabilidades descobertas na infraestrutura de rede."</span>

<span class="c1">Detalhes da vulnerabilidade</span>

*   <span class="c0">"Obtenha no Cyware Respond os detalhes da vulnerabilidade que discutimos anteriormente."</span>
*   <span class="c0">"Mostre no Cyware Respond as etapas de mitigação da vulnerabilidade mencionada acima.</span>

<span class="c0"></span>