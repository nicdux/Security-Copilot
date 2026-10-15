# Introdução
![Logotipo do Security CoPilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)
#### 🎓 Nível: 100 (iniciante)
#### ⌛ Tempo estimado para concluir este laboratório: 10 minutos

### Objetivos

Ao concluir este guia técnico, você terá as seguintes habilidades:<br>

* Capacidade de carregar um plugin personalizado do tipo KQL.<br>
* Compreensão de como enriquecer as informações dos usuários usando uma lista externa.<br>
* Proficiência na geração de relatórios com a fonte do plugin personalizado.<br>

### Cenário
Neste workshop técnico, os participantes aprenderão a carregar um plugin personalizado do Microsoft Security Copilot do tipo API.<br>
Para concluir esta tarefa com êxito, você precisa atender aos seguintes pré-requisitos:<br>

* Você precisa ter seu próprio locatário e uma instância do Microsoft Security Copilot.<br>
* Você precisa ter permissão para carregar um plugin personalizado.<br>



### Instruções
<br>

#### Carregar o plugin personalizado


1. Obtenha o arquivo chamado **"UsersHR.yml"** no diretório especificado.<br>
2. Examine um plugin do tipo KQL.<br>
3. Altere a configuração no arquivo YAML para incluir sua assinatura, o grupo de recursos (em que o Sentinel está implantado) e o workspace do Log Analytics (em que o Sentinel está implantado).<br>

<img src="./images/update_config.jpg"/>

<br>

> ⭐ Observação: <br>

Para obter o **Tenant ID, Subscription ID, Resource Group e o nome do Log Analytics Workspace**, consulte a documentação do Azure.<br>

4. Carregue o plugin personalizado e confirme sua ativação.<br>


<img src="./images/upload_plugin.jpg"/>

<br>
<img src="./images/upload_plugin_wood.jpg"/>


#### Caso de uso


Como analista de SOC no domínio Woodgrove, você está envolvido na investigação de um incidente do SAP. Durante a investigação, identificou um usuário realizando uma atividade suspeita, especificamente o download de um arquivo do sistema SAP. Para responder rapidamente, é fundamental enriquecer o perfil desse usuário com dados do sistema de RH, chamado **WoodgroveHR**.<br>

Como esse incidente ocorreu em um ambiente isolado, seu colega da Woodgrove-airgap forneceu os detalhes do incidente no formato JSON, que você precisa acessar e usar em análises adicionais.<br>


**Sua tarefa é:**<br>

1. Buscar o incidente do Sentinel no ambiente isolado para a memória da sessão do Copilot.
> ⭐ Observação: <br>

Para usar a opção FetchURL, o **plugin Web** público precisa estar habilitado.

<img src="./images/public_web.jpg"/><br>

2. Use o plugin personalizado **WoodgroveHR User Directory** que acabou de carregar e chame-o explicitamente.<br>
  Dica: você pode fazer isso digitando **/wood**.<br>

<img src="./images/call_plugin.jpg"/>

3. Pesquise o usuário vítima do incidente.<br>

<img src="./images/add_paramter.jpg"/>

4. Gere um relatório que inclua o resumo do incidente e os dados do usuário enriquecidos pelo WoodgroveHR.<br>


#### Exemplos de prompts:

1. Fetch url https://raw.githubusercontent.com/Yaniv-Shasha/SecurityCopilot/main/Workshop/Custom_Plugin/Task05_KQL/Sentinel_Incident.json.<br>



2. Você precisa chamar explicitamente a habilidade personalizada carregada digitando **/woodgroveHD**.<br>

> ⭐ Observação: <br>
  Dica: você pode fazer isso digitando **/wood**.<br>

<img src="./images/call_plugin.jpg"/>

3. Adicione o nome do usuário como parâmetro de entrada do plugin **/woodgroveHD**.<br>

<img src="./images/add_paramter.jpg"/>

4. Gere um relatório que resuma o incidente e inclua as informações do usuário.

<br>


#### ✅ Resultados finais:
<img src="./images/final_results.jpg"/>