# Introdução
![Logotipo do Security CoPilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)
#### 🎓 Nível: 100 (iniciante)
#### ⌛ Tempo estimado para concluir este laboratório: 10 minutos

### Objetivos

Ao concluir este guia técnico, você terá as seguintes habilidades:<br>

* Carregar um plugin personalizado do tipo API.<br>
* Aprender a usar o promptbook de análise de scripts.<br>
* Aprender a analisar e codificar scripts.<br>
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

> ⭐ Observação: <br>
Se você já concluiu o Módulo 4, não é necessário carregar o plugin novamente.<br>


1. Obtenha o arquivo chamado **"Geo.yaml"** neste diretório.<br>
2. Examine-o para entender a simplicidade da criação de um plugin do tipo API.<br>
3. Carregue o plugin personalizado e verifique se ele está ativado.<br>

<img src="./images/upload_plugin.jpg"/>


<img src="./images/plugin_turn_on.jpg"/>


#### Caso de uso


Você é analista de SOC no domínio Woodgrove. Durante a investigação de um incidente de ponto de extremidade, encontrou um script suspeito em execução no servidor da DMZ. Sua tarefa é analisar esse script e compartilhar as conclusões com a equipe.<br>



**Sua tarefa é:**<br>

1. Inserir as informações do script contidas em script_decode.txt e pedir ao Copilot que as decodifique.
2. Extrair somente os IPs desse script.
3. Usar a pontuação de reputação do MDTI para avaliar esses IPs.
4. Identificar os IPs e suas pontuações.
5. Para compilar um relatório com suas conclusões, usar o plugin personalizado que você acabou de carregar para obter a geolocalização dos IPs suspeitos.
6. Compartilhar um relatório que inclua a pontuação de reputação e os dados de GeoIP.



#### Exemplos de prompts:

1. Decodifique o script acima "Substitua isto pelo script que você copiou".<br>

<img src="./images/decode.png"/>

2. Verifique a pontuação de reputação do IP acima.<br>

3. Obtenha a geolocalização do IP acima.<br>

4. Crie um relatório que inclua a pontuação de reputação e o endereço GeoIP.<br>


#### ✅ Resultados finais:


<img src="./images/final_free%20text.png"/>



 ⭐**Tarefa bônus:** <br>

1. Copie o script de script_decode.txt.<br>

<img src="./images/prompbooks.jpg"/> <br>


2. Inicie o promptbook da ferramenta "Suspicious Script Analysis".
3. Cole o script copiado na etapa um no campo indicado e clique em "Executar".
4. Distribua o relatório gerado e avalie se o script é mal-intencionado.