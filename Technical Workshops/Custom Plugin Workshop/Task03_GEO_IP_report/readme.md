# Introdução
![Logotipo do Security CoPilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)
#### 🎓 Nível: 100 (iniciante)
#### ⌛ Tempo estimado para concluir este laboratório: 10 minutos

### Objetivos

Ao concluir este guia técnico, você terá as seguintes habilidades:<br>

* Carregar um plugin personalizado do tipo API.<br>
* Aprender a usar a habilidade fetchUrl.<br>
* Gerar um relatório que aproveite a fonte do plugin personalizado.<br>



### Cenário
Neste workshop técnico, os participantes aprenderão a carregar um plugin personalizado do Microsoft Security Copilot do tipo API.<br>

> ⭐ Observação: <br>
**Ao usar um plugin personalizado do tipo API, lembre-se de que os dados são transferidos para fora do seu locatário e enviados a um ponto de extremidade remoto. Neste laboratório, trabalhamos com dados de exemplo. Leve isso em consideração ao manipular dados internos.**
<br>

Para concluir esta tarefa com êxito, você precisa atender aos seguintes pré-requisitos:<br>

* Você precisa ter seu próprio locatário e uma instância do Microsoft Security Copilot.<br>
* Você precisa ter permissão para carregar um plugin personalizado.<br>



### Instruções
<br>

#### Carregar o plugin personalizado


1. Obtenha o arquivo chamado **"Geo.yaml"** neste diretório.<br>
2. Examine-o para entender a simplicidade da criação de um plugin do tipo API.<br>
3. Carregue o plugin personalizado e verifique se ele está ativado.<br>

<img src="https://github.com/Yaniv-Shasha/SecurityCopilot/blob/5cd2b8bb01eb8e3762371631aef03dd55697aded/Workshop/Custom_Plugin/Task03_GEO_IP_report/images/upload_plugin.jpg"/>


<img src="./images/plugin_turn_on.jpg"/>


#### Caso de uso

Você está preparando um relatório de enriquecimento com base em um incidente anterior. Como parte da coleta de evidências, recebeu um arquivo com listas de endereços IP.<br>
Sua tarefa é avaliar a pontuação de reputação desses IPs e compartilhar aqueles com pontuação acima de 70.<br>

O gerente do SOC solicitou que você inclua no relatório tanto o endereço IP quanto sua localização geográfica completa.<br>



**Sua tarefa é:**<br>

1. Inserir essas informações do CSV no Copilot (use a versão bruta).
2. Extrair somente os IPs desse arquivo.
3. Usar a pontuação de reputação do MDTI para avaliar esses IPs.
4. Identificar IPs com pontuação acima de 75.
5. Para compilar um relatório com suas conclusões, usar o plugin personalizado que você acabou de carregar para obter a geolocalização dos IPs suspeitos.
6. Compartilhar um relatório que inclua a pontuação de reputação e os dados de GeoIP.


#### Como realizar esta tarefa

1. Use a habilidade **"fetchurl"** para acessar o arquivo localizado no mesmo diretório. É importante obter a representação bruta do arquivo.<br>

#### Exemplos de prompts:

1. Fetchurl https://raw.githubusercontent.com/Yaniv-Shasha/SecurityCopilot/main/Workshop/Custom_Plugin/Task03_GEO_IP_report/CiscoSEG.csv<br>

> ⭐ Observação: <br>

Para usar a opção FetchURL, o **plugin Web** público precisa estar habilitado.

<img src="./images/public_web.jpg"/><br>

<br>

2. Liste separadamente todos os DeviceAddress desse arquivo.<br>

3. Verifique a pontuação de reputação dos IPs acima.<br>

4. Informe a geolocalização do IP cuja reputação esteja acima de 75.<br>

5. Gere relatórios que incluam a pontuação de reputação do endereço IP e informações de geolocalização.<br>


#### ✅ Resultados finais:


<img src="./images/final_results.jpg"/>