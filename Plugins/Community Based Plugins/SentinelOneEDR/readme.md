# Plugin personalizado do SentinelOne EDR
Boas-vindas ao plugin personalizado do SentinelOne! Aqui você terá acesso a funcionalidades avançadas desenvolvidas para aprimorar sua experiência com o SentinelOne:
### Instruções
#### Carregar o plugin personalizado

1. Obtenha o arquivo [SentinelOne_Manifest.yaml](https://github.com/Azure/Copilot-For-Security/blob/main/Plugins/Community%20Based%20Plugins/SentinelOneEDR/SentinelOne_Manifest.yaml) deste diretório.
2. Carregue o plugin personalizado.
3. Adicione a URL da instância do servidor SentinelOne e a chave de API.

<p align="center">
<img src="./images/upload_config.png?raw=true">
</p>



## Uso dos plugins:

- **Get_S1_alerts:** obtém alertas por nome de regra no SentinelOne.<br>
                                        #ExamplePrompts Obtenha alertas por nome de regra no SentinelOne.<br>
                                        #ExamplePrompts Filtre alertas pelo estado do incidente no SentinelOne.<br>
                                        #ExamplePrompts Pesquise alertas pelo caminho do arquivo de origem no SentinelOne.<br>
                                        #ExamplePrompts Limite o número de alertas retornados pelo SentinelOne.<br>
                                        #ExamplePrompts Classifique alertas por coluna no SentinelOne.<br>
                                        #ExamplePrompts Filtre alertas por severidade no SentinelOne.<br>
                                        #ExamplePrompts Pesquise alertas pelo nome do processo de origem no SentinelOne.<br>

<p align="center">
<img src="./images/get_alerts_input.png?raw=true">
</p>

- **Get_S1_DeviceInfo** obtém os agentes e seus dados que correspondem ao filtro. Esse comando fornece o ID do agente, que pode ser usado em outros comandos.<br>
                                        #ExamplePrompts Obtenha informações e dados dos agentes no produto SentinelOne EDR.<br>
                                        #ExamplePrompts Obtenha detalhes e dados relacionados dos agentes com a integração do SentinelOne.<br>
                                        #ExamplePrompts Acesse facilmente os dados dos agentes com o SentinelOne EDR.<br>
                                        #ExamplePrompts Obtenha informações dos agentes por meio da integração do SentinelOne.<br>
                                        #ExamplePrompts Obtenha IDs e dados relacionados dos agentes para aprimorar as operações de segurança com o SentinelOne.<br>
                                        #ExamplePrompts Use a plataforma SentinelOne EDR para obter facilmente informações dos agentes.<br>
<p align="center">
<img src="./images/DeviceInfo_input.png?raw=true">
</p>

- **Get_S1_Application** obtém os aplicativos instalados de um agente específico no SentinelOne.<br>
                                        #ExamplePrompts Obtenha a lista de softwares instalados em um dispositivo especificado usando o SentinelOne.<br>
                                        #ExamplePrompts Colete dados sobre as instalações de software vinculadas a um agente específico usando o <br>SentinelOne.<br>
                                        #ExamplePrompts Obtenha informações sobre os aplicativos atualmente implantados em um computador especificado por meio do SentinelOne.<br>
                                        #ExamplePrompts Extraia um catálogo de programas instalados do sistema de um agente especificado usando o SentinelOne.<br>
                                        #ExamplePrompts Acesse o inventário de aplicativos instalados vinculados a determinado agente do SentinelOne.<br>
                                        #ExamplePrompts Obtenha um relatório detalhado das instalações de software associadas a um ponto de extremidade específico do SentinelOne.<br>
<p align="center">
<img src="./images/application_input.png?raw=true">
</p>

- **Get_S1_Threats** obtém os dados das ameaças que correspondem ao filtro. É recomendável usar os filtros. Cada ameaça gera várias linhas de dados, que podem atingir rapidamente o limite da página.<br>
                                      #ExamplePrompts Obtenha dados de ameaças usando a plataforma do SentinelOne.<br>
                                      #ExamplePrompts Obtenha informações de ameaças com a integração do SentinelOne.<br>
                                      #ExamplePrompts Acesse no SentinelOne os dados de ameaças que correspondem ao filtro.<br>
                                      #ExamplePrompts Colete detalhes das ameaças com eficiência usando os filtros do SentinelOne.<br>
                                      #ExamplePrompts Obtenha no SentinelOne linhas de dados de ameaças que atingem rapidamente o limite da página.<br>
                                      #ExamplePrompts Use a operação 'Get_S1_Threats' no SentinelOne para obter dados de ameaças.<br>
<p align="center">
<img src="./images/thread_input.png?raw=true">
</p>

- **Get_Hash_S1_Reputation** obtém a reputação de um hash usando o SHA1 obrigatório. Para obter o hash, execute "threats" — de preferência filtrado por Group ou Site — e use o valor Content Hash do arquivo.<br>
                                      #ExamplePrompts Obtenha a reputação de um hash usando o SentinelOne.<br>
                                      #ExamplePrompts Obtenha a pontuação de reputação de um hash com a integração do SentinelOne.<br>
                                      #ExamplePrompts Acesse os detalhes de reputação de um hash específico usando a plataforma do SentinelOne.<br>
                                      #ExamplePrompts Colete no SentinelOne as informações de reputação de um hash usando o SHA1 obrigatório.<br>
                                      #ExamplePrompts Obtenha a pontuação de reputação de um hash usando o serviço de reputação do SentinelOne.<br>
                                      #ExamplePrompts Use a operação 'Get_Hash_Reputation' no SentinelOne para obter a reputação de um hash.<br>
<p align="center">
<img src="./images/reputation_input.png?raw=true">
</p>

- **Get_S1_EventsTimeline** obtém os carimbos de data/hora do primeiro e do último evento da sequência de ataque da ameaça.<br>
                                       #ExamplePrompts Obtenha a linha do tempo dos eventos de um ID de ameaça específico usando o SentinelOne.<br>
                                       #ExamplePrompts Obtenha os carimbos de data/hora do primeiro e do último evento da sequência de ataque de uma ameaça com a integração do SentinelOne.<br>
                                       #ExamplePrompts Acesse a sequência cronológica de eventos associados a um ID de ameaça por meio da plataforma do SentinelOne.<br>
                                       #ExamplePrompts Colete no SentinelOne os detalhes da linha do tempo, incluindo os carimbos de data/hora do primeiro e do último evento da sequência de ataque de uma ameaça.<br>
                                       #ExamplePrompts Obtenha no SentinelOne a linha do tempo dos eventos de uma ameaça, indicando o início e o fim do ataque.<br>
                                       #ExamplePrompts Use a operação 'Get_S1_EventsTimeline' no SentinelOne para obter a linha do tempo dos eventos vinculados a um ID de ameaça.<br>
<p align="center">
<img src="./images/timeline_input.png?raw=true">
</p>

Aprimore sua exploração do SentinelOne com essas ferramentas avançadas, desenvolvidas para simplificar o processo de pesquisa e análise. Vamos começar! 🚀<br>
