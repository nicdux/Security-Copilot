# Boas-vindas aos laboratórios do Microsoft Security Copilot!
# Introdução
![Logotipo do Security CoPilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)
## Criar prompts para um arquivo carregado no Security Copilot
#### ⌛ Tempo estimado para concluir este laboratório: 20 minutos
#### 🎓 Nível: 200 (proficiente)

#### Objetivos

Ao concluir este guia técnico, você terá as seguintes habilidades:<br>

* Aproveitar o plugin de carregamento de arquivo com prompts enviados diretamente pelo Security Copilot.<br>


#### Cenário
"Neste workshop técnico, os participantes aprenderão a pesquisar documentos e aproveitar as informações em cenários práticos de operações de segurança. Para concluir esta tarefa com êxito, você precisa atender aos seguintes pré-requisitos:<br>

* Você precisa ter seu próprio locatário e uma instância do Microsoft Security Copilot.<br>
* Arquivos carregados no módulo anterior.<br>


# Agenda do workshop: criar prompts para um arquivo carregado no Security Copilot

## 1. Acessar o documento da SANS ("Hunt Evil Poster")
- Acesse o documento na pasta de exemplos do GitHub: [PDF Hunt Evil Poster](https://github.com/Azure/Copilot-For-Security/blob/main/Technical%20Workshops/Knowledge%20base%20Workshop/Sample%20Files/Hunt%20Evil%20Poster.pdf), ou pelo link: https://www.sans.org/posters/hunt-evil/

![Hunt Evil 3](https://github.com/Azure/Copilot-For-Security/blob/main/Images/KB%20Images/huntevil3.png?raw=true)

- Verifique se o documento foi adicionado ao recurso de carregamento de arquivos do Security Copilot.

## 2. Criar prompts para arquivos carregados usando o Security Copilot

- Envie o primeiro prompt consultando os dados do documento. Vamos nos concentrar em alguns cenários; no documento Hunt Evil, buscaremos informações relacionadas à movimentação lateral, com foco em como ela é realizada por acesso remoto ou execução remota.

**Prompt 1: Você poderia mostrar, em formato de tabela, as IDs de evento associadas à execução remota no documento SANS_DFPS_FOR508_v4.10_02-23 (1).pdf dos arquivos carregados?**

![Cartaz Hunt Evil 1](https://github.com/Azure/Copilot-For-Security/blob/main/Images/KB%20Images/huntevilfileupload1.png)


**Prompt 2: Usando as IDs de evento acima, procure em meu ambiente do Defender qualquer evento associado a elas.**

![Cartaz Hunt Evil 2](https://github.com/Azure/Copilot-For-Security/blob/main/Images/KB%20Images/huntevilfileupload2.png)