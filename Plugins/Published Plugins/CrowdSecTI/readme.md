# CrowdSec Threat Intelligence

Este plugin permite aprimorar investigações de IP com inteligência contra ameaças fornecida pela **CrowdSec** e obter informações como:
   - Reputações selecionadas de IPs e intervalos de IP
   - Avaliação do nível de ruído de fundo
   - Registros detalhados de comportamentos maliciosos
   - Técnicas MITRE associadas ao IP
   - Países visados pelo invasor
   - Classificação do invasor
   - Métricas históricas de atividade e agressividade (abrangendo as últimas 24 horas, 7 dias, 30 dias e todo o período)

[Encontre aqui informações detalhadas sobre o produto](https://www.crowdsec.net/cyber-threat-intelligence)

## **Pré-requisitos**

1. O plugin exige uma chave de API, que pode ser obtida ao criar uma conta gratuita [aqui](https://app.crowdsec.net/signup).

Depois de entrar, você pode criar e gerenciar suas chaves de API na seção **Settings > API Keys**:

![Criar chave de API](Images/create-api-key.png)

2. No gerenciador de plugins, localize o plugin CrowdSec e habilite-o.

![Habilitar plugin](Images/enable-crowdsec-plugin.png)

3. Clique no botão "Set Up", insira a chave de API da CrowdSec e pressione "Save".

![Configurar chave de API](Images/configure-api-key.png)


## Como invocar o plugin e as habilidades

1. Use um prompt em linguagem natural dos exemplos abaixo ou use a invocação direta de habilidade ("/").


## Habilidades e prompts

1. Consultar endereço IP: pergunte à CrowdSec sobre um IP.
   - Exemplos de prompt:
     - O que a CrowdSec pode informar sobre este IP: [IP]
     - De acordo com a CrowdSec, quais são os principais países visados por este IP: [IP]
   - Entradas: [IP]

## Perguntas frequentes (FAQ)

1. **Importante**: problemas de invocação
   Se os prompts não funcionarem, verifique se você está usando um dos prompts compatíveis acima. Caso contrário, use a invocação direta de habilidade "/".
