# GreyNoise Enterprise
**Autores: Shiv Patel + Brad Chiappetta**

**Publicadores: Microsoft + GreyNoise**

Este plugin permite enriquecer investigações usando a inteligência contra ameaças da GreyNoise:
1. Consultar informações sobre um IP
2. Executar uma consulta da GreyNoise

Informações sobre o produto:
https://www.greynoise.io/greynoise-product

**Observação**
Verifique se você tem uma assinatura da GreyNoise com capacidade de Search suficiente para seu uso.

## **Pré-requisitos**
1. Entre em sua [conta GreyNoise](https://viz.greynoise.io/account/plan).
2. Acesse sua chave de API da GreyNoise na [guia My API Key](https://viz.greynoise.io/account/api-key).
3. Copie a chave de API para inseri-la no Co-Pilot.


## Selecione ou carregue o arquivo de manifesto anexado no console do Copilot for Security
1. No gerenciador de plugins, localize o plugin GreyNoise Enterprise e habilite-o.
![Habilitar plugin](images/GreyNoiseEnterprise_plugin.png)

    ## Como invocar o plugin e as habilidades
2. **Importante**
   Depois de selecionar ou carregar o arquivo, clique no botão "Set Up", insira a chave de API copiada conforme os pré-requisitos acima e pressione "Save".
![Inserir chave](images/GreyNoiseEnterprise_settings.png)

3. Use um prompt em linguagem natural dos exemplos abaixo ou use a invocação direta de habilidade ("/").


## Habilidades e prompts
1. Consultar o contexto do IP: pergunte à GreyNoise se este IP é um scanner da Internet.
   - Exemplos de prompt: Informe sobre o endereço IP [IP] usando o banco de dados da GreyNoise; Localize o GreyNoise IP Context do IP [IP]
   - Entradas: [IP]
2. Fazer uma consulta rápida de IP: solicite à GreyNoise uma verificação rápida deste IP.
   - Exemplos de prompt: Consulte o IP [IP] na GreyNoise usando uma busca rápida; Use a GreyNoise para fazer uma verificação rápida de [IP]
   - Entradas: [IP]
3. Consultar vários IPs: solicite à GreyNoise uma verificação rápida de vários IPs.
   - Exemplos de prompt: Consulte os IPs [IP, IP, IP] na GreyNoise usando uma busca rápida; Use a GreyNoise para fazer uma verificação rápida de [IP, IP, IP]
   - Entradas: [List of IPs]
4. Consultar IP no RIOT: pergunte à GreyNoise se este IP está associado a um serviço comercial comum.
   - Exemplos de prompt: Use a GreyNoise para verificar as informações do RIOT sobre o IP [IP]; Quero conhecer as informações do RIOT da GreyNoise sobre o IP [IP]
   c
5. Consultar GNQL: consulte a GreyNoise usando a GreyNoise Query Language (GNQL).
   - Exemplos de prompt: Use a GreyNoise para verificar as informações da GNQL sobre [QUERY]; Consulte a GNQL para [QUERY]; Pesquise todos os IPs que verificam sensores localizados na Alemanha com a GNQL do GreyNoise Enterprise [QUERY]
   - Entradas: [QUERY]
6. Consultar CVE: use as estatísticas da GreyNoise Query Language (GNQL) para consultar informações de CVE no conjunto de dados da GreyNoise.
   - Exemplos de prompt: Use a GreyNoise para verificar as estatísticas sobre [CVE]; O que a GreyNoise sabe sobre [CVE]
   - Entradas: [CVE]

## Perguntas frequentes (FAQ)
1. **Importante**
   Se os prompts não funcionarem, verifique se você está usando um dos prompts compatíveis acima. Caso contrário, use a invocação direta de habilidade "/".
