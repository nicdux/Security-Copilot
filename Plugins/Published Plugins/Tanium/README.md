## Configurar a integração da Tanium com o Security Copilot

Estabeleça a comunicação entre uma instância da Tanium e o Security Copilot usando:

- uma URL do manifesto do plugin da Tanium para carregar o plugin personalizado Tanium Skills no Security Copilot

- uma URL da instância da Tanium para conectar o Security Copilot à instância da Tanium

- um token de API da Tanium para conceder ao Security Copilot permissão para consultar sua rede usando a Tanium e coletar dados de endpoints

1. Em uma janela do navegador, acesse a página inicial do Microsoft Security Copilot.

2. Clique no plugin Security Copilot. A janela modal Manage plugins será exibida.
![Janela Manage plugins](https://github.com/shuhblam/copilot-for-security/assets/745064/ec05f712-7489-46a5-a2be-7576bca0b2f1)

3. Na seção Custom, clique em Add plugin. A janela modal Add a plugin será exibida.
![Janela Add a plugin](https://github.com/shuhblam/copilot-for-security/assets/745064/5254358d-8e71-4a9d-ab11-3d39e4a88fb6)

4. Selecione Who can use this plugin?.

5. Clique em Security Copilot plugin.

6. Selecione o tipo de arquivo .json.

7. Em outra janela do navegador, acesse o Tanium Console.

8. Selecione Modules > Connect > Overview. A página Connect Overview será exibida.

9. Clique em Settings. Em seguida, clique em Microsoft Security Copilot.
![Configurações do Microsoft Security Copilot](https://github.com/shuhblam/copilot-for-security/assets/745064/4c7c8e0d-6efc-48e2-874a-b6e6e022cde2)

10. Clique em Tanium Plugin Manifest URL Copy para copiar a URL do manifesto do plugin para a área de transferência.

11. No Security Copilot, selecione Upload as a link. Em seguida, cole a Tanium Plugin Manifest URL.

12. Clique em Add. A janela modal Set up Tanium Skills será exibida.
![Janela Set up Tanium Skills](https://github.com/shuhblam/copilot-for-security/assets/745064/82e9ad22-5031-4494-98dc-bafb4dc8971b)

13. No Tanium Console, clique em Tanium Instance URL Copy para copiar a URL da instância da Tanium para a área de transferência.

14. No Security Copilot, cole a Tanium Instance URL na janela modal Set up Tanium Skills.

15. No Tanium Console, clique em Generate para gerar um token de API válido por 365 dias e copie o valor do token para a área de transferência.

> Não é possível visualizar o valor do token no Tanium Console. Se quiser registrá-lo para referência futura, cole o valor em um editor de texto sem formatação e salve o arquivo em um local seguro.


16. No Security Copilot, cole o valor do token de API no campo Value da janela modal Set up Tanium Skills.

17. Clique em Set up.


## Habilidades e prompts
| Soluções Tanium necessárias | Sugestão de prompt da habilidade Tanium | Descrição | Exemplos de prompts em linguagem natural |
| ------------- | ------------- | ------------- | ------------- |
| Tanium Core Platform | Get Logged In User | Recupera o usuário que está conectado no momento a um endpoint | Usando a Tanium, retorne o usuário conectado no momento ao endpoint com o hostname _hostname_ para que eu possa investigar um possível uso não autorizado do endpoint. Retorne uma URL de Tanium Console Question Results para que eu possa consultar mais informações em tempo real sobre esse endpoint. |
| Tanium Core Platform, sensor-dependent | Get Real-time Data from Endpoints | Recupera dados em tempo real de endpoints com base em um sensor da Tanium. Para obter mais informações sobre os sensores compatíveis | Usando a Tanium, retorne o nome do computador e o endereço IP dos endpoints. Exiba os resultados em uma tabela, em ordem alfabética pelo nome do computador, e retorne uma URL de Tanium Console Question Results para que eu possa consultar a lista de endpoints em tempo real. |
| Asset, SBOM | Count Endpoints Having Package Version | Recupera a quantidade total de endpoints que têm o pacote de software informado | Usando a Tanium, retorne o número total de endpoints com um pacote de software para _software-name_, para que eu possa começar a catalogar quais computadores têm o software instalado. Exiba os resultados em uma tabela, em ordem alfabética pelo nome do host, e retorne uma URL de Tanium Console Question Results para que eu possa consultar a lista de endpoints em tempo real. |
| Asset, SBOM | List Endpoints Having Package | Recupera até 10 endpoints que têm o pacote de software informado | Usando a Tanium, retorne os endpoints com um pacote de software para _software-name_, para que eu possa começar a catalogar quais computadores podem estar com uma versão desatualizada. Exiba os resultados em uma tabela, em ordem alfabética pelo nome do host, e retorne uma URL de Tanium Console Question Results para que eu possa consultar a lista de endpoints em tempo real. |
| Asset, SBOM, Threat Response | List Process SHA-256 Hashes and Versions | Recupera o hash SHA-256 do arquivo e a versão de um processo informado | Usando a Tanium, retorne o valor de hash SHA-256 e a versão do processo em execução _process-name_, para que eu possa localizar outras instâncias desse processo com base no valor de hash. |
| Comply | Get Vulnerability Test Results | Informa se um endpoint está vulnerável a uma CVE e o motivo da vulnerabilidade | Usando a Tanium, verifique se o endpoint _hostname_ está vulnerável a _cve-id_ e retorne os motivos pelos quais esse endpoint está vulnerável, com uma sugestão de plano de ação para corrigir a intrusão. |
| Comply | List Endpoints Vulnerable To CVE | Recupera até 10 endpoints vulneráveis a um ID de CVE informado | Usando a Tanium, retorne os endpoints vulneráveis a _cve-id_, para que eu possa corrigir a vulnerabilidade nesses endpoints. Exiba os resultados em uma tabela, em ordem alfabética pelo nome do host, e retorne uma URL de Tanium Console Question Results para que eu possa consultar a lista de endpoints em tempo real. |
| Direct Connect, Threat Response | View Endpoint Processes | Recupera uma URL para a página Threat Response Live Connection do endpoint solicitado, que contém uma lista dos processos em execução | Usando a Tanium, retorne uma URL de Threat Response Live Connection para o endpoint com o hostname _hostname_, para que eu possa analisar os processos em execução e identificar possíveis vulnerabilidades. |
| Incident Response | List Service Module Details | Recupera informações sobre os módulos de serviço em execução em um endpoint, incluindo nome, legenda e caminho da imagem | Usando a Tanium, retorne informações sobre os módulos de serviço em execução no endpoint com o hostname _hostname_, para que eu possa verificar se há módulos de serviço inesperados na lista. Exiba os resultados em uma tabela, em ordem alfabética pelo nome do módulo de serviço, e retorne uma URL de Tanium Console Question Results para que eu possa consultar a lista de módulos de serviço em tempo real. |
| Incident Response | List Service Process Details | Recupera informações sobre os processos de serviço em execução em um endpoint, incluindo nome, ID do processo e caminho do arquivo | Usando a Tanium, retorne informações sobre os processos de serviço em execução no endpoint com o hostname _hostname_, para que eu possa verificar se há processos de serviço inesperados na lista. Exiba os resultados em uma tabela, em ordem alfabética pelo nome do processo de serviço, e retorne uma URL de Tanium Console Question Results para que eu possa consultar a lista de processos de serviço em tempo real. |
| Incident Response | List WMI Event Consumers | Recupera os consumidores de eventos da Windows Management Instrumentation (WMI) em execução em um endpoint | Usando a Tanium, retorne os consumidores de eventos WMI em execução no endpoint com o hostname _hostname_, para que eu possa confirmar que somente os consumidores de eventos esperados estão em execução, e retorne uma URL de Tanium Console Question Results para que eu possa consultar a lista de consumidores de eventos em tempo real. |
| Index | List File Details | Recupera detalhes de um arquivo pelo nome, incluindo os endpoints nos quais ele está instalado, o caminho e o tamanho do arquivo | Usando a Tanium, retorne informações sobre o arquivo chamado _file-name_, para que eu possa determinar se ele está em execução em endpoints não previstos. Exiba os resultados em uma tabela, em ordem alfabética, e retorne uma URL de Tanium Console Question Results para que eu possa consultar a lista em tempo real. OU Usando a Tanium, retorne informações sobre o arquivo chamado _file-name_ instalado no endpoint com o hostname _hostname_, para que eu possa determinar se ele está em execução em endpoints não previstos. Exiba os resultados em uma tabela, em ordem alfabética, e retorne uma URL de Tanium Console Question Results para que eu possa consultar informações em tempo real. |
| Threat Response | List Child Processes for Process File | Retorna todos os processos filhos em execução em um endpoint com base no nome de um arquivo de processo informado | Usando a Tanium, liste os processos filhos de _process-name_, para que eu possa analisar o uso de recursos. Exiba os resultados em uma tabela, em ordem alfabética pelo nome do processo, e retorne uma URL de Tanium Console Question Results para que eu possa consultar a lista de endpoints em tempo real. OU Usando a Tanium, liste os processos filhos de _process-name_ em execução no computador com o hostname _hostname_, para que eu possa analisar o uso de recursos. Exiba os resultados em uma tabela, em ordem alfabética pelo nome do processo, e retorne uma URL de Tanium Console Question Results para que eu possa consultar a lista de endpoints em tempo real. |
| Threat Response | List Endpoints with Process Command | Recupera até 10 endpoints que executam o comando de linha de comando informado | Usando a Tanium, retorne os endpoints que executam o comando de linha de comando _process-command_, para que eu possa confirmar que esse processo não está em execução em endpoints inesperados. Exiba os resultados em uma tabela, em ordem alfabética pelo nome do host, e retorne uma URL de Tanium Console Question Results para que eu possa consultar a lista de endpoints em tempo real. |
| Threat Response | List Endpoints with Process Name | Recupera até 10 endpoints que executam o processo informado | Usando a Tanium, retorne os endpoints que executam um processo chamado _process-name_, para que eu possa confirmar que esse processo não está em execução em endpoints inesperados. Exiba os resultados em uma tabela, em ordem alfabética pelo nome do host, e retorne uma URL de Tanium Console Question Results para que eu possa consultar a lista de endpoints em tempo real. |
| Threat Response | List Endpoints with Process MD5 Hash | Recupera até 10 endpoints que executam o processo informado correspondente ao valor de hash MD5 fornecido | Usando a Tanium, retorne todos os endpoints que executam um processo com o valor de hash MD5 _md5-hash-value_, para que eu possa confirmar que esse processo não está em execução com outro nome de arquivo. Exiba os resultados em uma tabela, em ordem alfabética pelo nome do host, e retorne uma URL de Tanium Console Question Results para que eu possa consultar a lista de endpoints em tempo real. |
| Threat Response | List File Operations | Recupera informações históricas sobre operações de arquivos nos endpoints, incluindo nome do endpoint, caminho do arquivo e tipo de operação, como criação ou exclusão | Usando a Tanium, retorne informações sobre operações de arquivos no endpoint chamado _hostname_ realizadas no caminho "_partial-file-path_" durante _time-frame_, para que eu possa determinar se ocorreu algum comportamento malicioso de arquivo no endpoint. Exiba os resultados em uma tabela, em ordem alfabética, e retorne uma URL de Tanium Console Question Results para que eu possa consultar a lista em tempo real. OU Usando a Tanium, retorne informações sobre operações de arquivos realizadas no caminho "_partial-file-path_" durante _time-frame_, para que eu possa determinar se houve criação ou exclusão maliciosa de arquivos. Exiba os resultados em uma tabela, em ordem alfabética, e retorne uma URL de Tanium Console Question Results para que eu possa consultar a lista em tempo real. |
| Threat Response | List Processes Connected To IPv4 Address | Recupera os processos em execução em um endpoint com o endereço IPv4 informado | Usando a Tanium, retorne os processos em execução no endpoint com o endereço IPv4 _ipv4-address_, para que eu possa analisar possíveis intrusões de segurança e o uso de recursos. Exiba os resultados em uma tabela, em ordem alfabética pelo nome do processo, e retorne uma URL de Tanium Console Question Results para que eu possa consultar a lista de endpoints em tempo real. |
| Threat Response | List Process Ran As User | Recupera os processos em execução em um endpoint como um determinado usuário | Usando a Tanium, retorne os processos em execução como o usuário _user-name_, para que eu possa determinar se há problemas de acesso não autorizado. Exiba os resultados em uma tabela, em ordem alfabética pelo nome do computador, e retorne uma URL de Tanium Console Question Results para que eu possa consultar a lista de endpoints em tempo real. OU Usando a Tanium, retorne os processos em execução como o usuário _user-name_ no endpoint com o hostname _hostname_, para que eu possa determinar se há problemas de acesso não autorizado. Exiba os resultados em uma tabela, em ordem alfabética pelo nome do processo, e retorne uma URL de Tanium Console Question Results para que eu possa consultar a lista de endpoints em tempo real. |

### Documentação pública
Para consultar a documentação completa, acesse [esta página](https://help.tanium.com/bundle/ug_connect_cloud/page/connect/ms_copilot_security.html).
