# Introdução
![Logotipo do Security CoPilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)
#### 🎓 Nível: 100 (iniciante)
#### ⌛ Tempo estimado para concluir este laboratório: 10 minutos

### Objetivos

Ao concluir este guia técnico, você terá as seguintes habilidades:<br>

* Carregar um plugin personalizado do tipo GPT.<br>
* Aprender a usar a habilidade fetchUrl.<br>
* Aprender a usar a habilidade DefangUrl.<br>
* Gerar um relatório que aproveite os dados do MDTI e a fonte do plugin personalizado.<br>



### Cenário
Neste workshop técnico, os participantes aprenderão a carregar um plugin personalizado do Microsoft Security Copilot do tipo GPT.<br>
Para concluir esta tarefa com êxito, você precisa atender aos seguintes pré-requisitos:<br>

* Você precisa ter seu próprio locatário e uma instância do Microsoft Security Copilot.<br>
* Você precisa ter permissão para carregar um plugin personalizado.<br>



### Instruções
<br>

#### Carregar o plugin personalizado


1. Obtenha o arquivo chamado **"DefangsURLs.yaml"** neste diretório.<br>
2. Examine-o para entender a simplicidade da criação de um plugin do tipo GPT.<br>
3. Carregue o plugin personalizado e verifique se ele está ativado.<br>

<img src="https://github.com/Yaniv-Shasha/SecurityCopilot/blob/cfcd1baf606277478b7512be8bf3e43c7074f870/Workshop/Custom_Plugin/Task01_Send_jokeByemail/Images/upload_plugin.jpg"/>


<img src="https://github.com/Yaniv-Shasha/SecurityCopilot/blob/f15ba2df94fbba97cb9adf70426cdf4d471b28fb/Workshop/Custom_Plugin/Task02_Defang_URL/images/plugin-turnON.jpg"/>


#### Caso de uso

Você é analista de resposta a incidentes e está investigando um incidente prolongado.<br>
Seu colega forneceu um arquivo JSON que contém atividades de pesquisa de DNS do servidor DNS.<br>


**Sua tarefa é:**<br>

1. Buscar as informações de DNS para o contexto da sessão do Copilot.

> ⭐ Observação: <br>

Para usar a opção FetchURL, o **plugin Web** público precisa estar habilitado.

<img src="./images/public_web.jpg"/><br>

2. Extrair somente as URLs desse arquivo.
3. Usar a habilidade de pontuação de reputação do MDTI para avaliar essas URLs.
4. Identificar URLs com pontuação acima de 75.
5. Para compilar um relatório com suas conclusões, usar o plugin personalizado que você acabou de carregar para neutralizar (**Defang**) as URLs suspeitas.


#### Como realizar esta tarefa

* Use a habilidade "fetchurl" para acessar o arquivo localizado no mesmo diretório. É importante obter a representação bruta do arquivo.<br>
* Use a habilidade do MDTI e o DefangUrl para criar o relatório.


#### Exemplo de prompt:

1. Fetchurl https://raw.githubusercontent.com/Yaniv-Shasha/SecurityCopilot/main/Workshop/Custom_Plugin/Task02_Defang_URL/UrlstoFetch_Task02.json.<br>

2. Liste separadamente todas as consultas DNS desse arquivo.<br>

3. Verifique a pontuação de reputação dos domínios acima.<br>

4. Neutralize as URLs de todos os domínios com pontuação de reputação acima de 75.

5. Crie um relatório que inclua somente a URL neutralizada e a pontuação de reputação.<br>

#### ✅ Resultados finais:


<img src="./images/final_result.jpg"/>