![Visão geral do Security Copilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)

# Guia do Security Copilot para criar seu plugin personalizado

**Nome do plugin
**Autor: John DOE**
**Publicador: Example**

Este plugin permite enriquecer investigações usando inteligência contra ameaças de fontes personalizadas:
	1. Verificar uma URL ou um domínio
	2. Verificar um endereço IP

Blog técnico
https://learn.microsoft.com/en-us/security-copilot/

**Observação**
Verifique se você tem tokens de API suficientes antes de invocar qualquer habilidade para evitar falhas.

## **Pré-requisitos**
1. Entre em sua conta Example.

2. Para criar uma nova "API Key", clique em "Add & Integration Key".

   ![APIKey](https://learn.microsoft.com/en-us/security-copilot/media/plugin-button.png)  
   
3. Será exibida uma caixa de diálogo para inserir o nome da API. Dê à chave um nome curto, mas descritivo, como "Security Copilot API Key".

4. Copie a chave de API para um local seguro e descarte qualquer cópia desnecessária com cuidado.


## Selecione ou carregue o arquivo de manifesto anexado no console do Security Copilot
1. Clique em Deploy to Azure.
[![Implantar no Azure](https://aka.ms/deploytoazurebutton)](https://aka.ms/LINK)
  

2. Insira a seguinte chave de API no campo value:
	```
	"API Key": x-apikey
	```
	## Como invocar o plugin e as habilidades
1. **Importante**
   Depois de selecionar ou carregar o arquivo, clique no botão "Set Up", insira a chave de API copiada conforme os pré-requisitos acima e pressione "Save".

2. Use um prompt em linguagem natural dos exemplos abaixo ou use a invocação direta de habilidade ("/").


## Habilidades e prompts
1. Habilidade 1: pergunte ao Example Plugin sobre esta URL.
- Exemplos de prompt: Informe sobre esta [URL]; O que o Example Plugin informa sobre este [domain]
- Entradas: [URL]
2. Habilidade 2: pergunte ao Example Plugin sobre este endereço IP.


## Perguntas frequentes (FAQ)
1. **Importante**
   Se os prompts não funcionarem, verifique se você está usando um dos prompts compatíveis acima. Caso contrário, use a invocação direta de habilidade "/".
