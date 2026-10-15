# # IBM X-Force Thread Intelligence
**Publicador: Microsoft**

Informações do produto:
https://www.ibm.com/products/xforce-threat-intelligence

## Visão geral
O IBM X-Force é uma plataforma online desenvolvida para ajudar você a compreender e responder a ameaças de segurança. Esse serviço de nuvem permite acessar e distribuir informações sobre possíveis riscos de segurança, além de agir com base nelas. Com a plataforma, você pode descobrir rapidamente novas ameaças de segurança em todo o mundo, coletar informações úteis para sua proteção, conversar com especialistas e colaborar com outras pessoas que também buscam manter a segurança. O IBM X-Force Exchange combina conhecimento humano e processos automatizados, usando os amplos recursos do IBM X-Force para ajudar os usuários a se anteciparem a ameaças emergentes.

## Como invocar o plugin e as habilidades

1. Uma janela intitulada "Manage plugins" será aberta. Role para baixo até encontrar o plugin IBM X-Force.
<img src="images/ibm_settings.png" alt="configurações" width="500"/>


2. Clique no botão "Setup" do plugin IBM X-Force destacado na imagem acima. Uma nova janela será exibida.
<img src="images/ibm_select.png" alt="configurações" width="500"/>


3. Insira a chave de API e a senha do IBM X-Force no campo "Value" e clique no botão "Save". Após salvar, você verá uma confirmação.
<img src="images/ibm_insert.png" alt="configurações" width="500"/>


4. Use o conjunto de habilidades do IBM X-Force.
   1. Verifique se o plugin IBM X-Force está habilitado acessando a guia "Manage plugins" e confirmando que o seletor está ativo.
   2. Execute um prompt de exemplo, como `Mostre o WHOIS do IBM para www.bing.com.`



## Habilidades e prompts

1. Get Threat Intelligence Reports IBM: obtém relatórios premium de inteligência contra ameaças com base em determinado tipo de relatório.
   - Prompts de exemplo:
     - Fale sobre relatórios recentes de inteligência contra ameaças da IBM.
     - Mostre os relatórios de inteligência contra ameaças do IBM X-Force.
   - Entradas:
     - reportType
       - Description: o tipo de relatório de inteligência contra ameaças. Os tipos possíveis são threatanalysis, osintadvisory, malware, industry e threatgroup.
       - Required: true
       - Type: string
       - Example: "threatanalysis"
     - added_after
       - Description: obtém relatórios criados após a data especificada, por exemplo, 2022-10-12. Se não for informado, a consulta retornará os IPs mais recentes.
       - Required: false
       - Type: string
       - Example: "2022-10-12"
     - added_before
       - Description: obtém relatórios criados antes da data especificada, por exemplo, 2022-10-12. Se não for informado, a consulta retornará os IPs mais recentes.
       - Required: false
       - Type: string
       - Example: "2022-10-12"
     - limit
       - Description: a quantidade de relatórios de análise de malware retornados. O valor padrão é 200 e o limite não pode ser maior que 200.
       - Required: false
       - Type: integer
       - Example: 201
     - skip
       - Description: o ponto inicial para obter entradas. O valor padrão é 0.
       - Required: false
       - Type: integer
       - Example: 10
2. Get Threat Group Profiles IBM: obtém uma lista de perfis de grupos de ameaças.
   - Prompts de exemplo:
     - Quais são os perfis de grupos de ameaças mais recentes do X-Force?
     - Quais são os perfis de grupos de ameaças da IBM?
     - Mostre os 20 principais perfis de grupos de ameaças da IBM.
   - Entradas:
     - limit
       - Description: a quantidade de relatórios de análise de malware retornados. O valor padrão é 200 e o limite não pode ser maior que 200.
       - Required: false
       - Type: integer
       - Example: 201
     - skip
       - Description: o ponto inicial para obter entradas. O valor padrão é 0.
       - Required: false
       - Type: integer
       - Example: 10
3. Get Dns Records IBM: verifica um nome de domínio, endereço IP ou URL nos registros DNS do IBM X-Force.
   - Prompts de exemplo:
     - Mostre os registros DNS da IBM para www.bing.com.
     - Quais são os registros DNS do IBM X-Force para https://www.bing.com/search?q=microsoft&form=QBLH&sp=-1&lq=0&pq=microsof&sc=11-8&qs=n&sk=&cvid=166E76706804404BAA7390129EE88004&ghsh=0&ghacc=0&ghpl=?
     - Qual é o registro DNS da IBM para www.https://www.microsoft.com/?
   - Entradas:
     - input
       - Description: o nome de domínio, endereço IP ou URL a ser verificado para obter informações de DNS.
       - Required: true
       - Type: string
       - Example: "www.bing.com"
4. Get WHOIS IBM: retorna as informações WHOIS de um IP, URL ou domínio.
   - Prompts de exemplo:
     - Mostre os registros WHOIS da IBM para www.bing.com.
     - Qual é o WHOIS da IBM para https://www.bing.com/search?q=microsoft&form=QBLH&sp=-1&lq=0&pq=microsof&sc=11-8&qs=n&sk=&cvid=166E76706804404BAA7390129EE88004&ghsh=0&ghacc=0&ghpl=?
     - IBM WHOIS www.https://www.microsoft.com/?
   - Entradas:
     - host
       - Description: o nome de domínio, endereço IP ou URL a ser verificado para obter informações WHOIS.
       - Required: true
       - Rype: string
       - Example: "www.bing.com"