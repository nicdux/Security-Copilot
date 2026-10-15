# Investigação de incidentes do Defender

<br>

## DESCRIÇÃO

Os dois plugins personalizados, "Custom Plugin Defender Device Investigation" e "Custom Plugin Defender Device Info", fornecem diversas habilidades do Security Copilot para apoiar a investigação e a busca de ameaças em dispositivos no Microsoft Defender XDR.

<br>

## TIPO E REQUISITOS

- **TIPO**: KQL (Defender)
- **FONTE**: tabelas do schema do Defender for Endpoint
- **REQUISITOS**: acesso ao Defender XDR

<br>

## O “Custom Plugin Defender Device Investigation” fornece as seguintes habilidades:

Título: **Arquivo — Arquivos baixados**

- Descrição: lista os arquivos baixados neste dispositivo em um período específico nos últimos 30 dias.

Título: **Arquivo — Arquivos baixados nos últimos 15 dias**

- Descrição: lista os arquivos baixados neste dispositivo nos últimos 15 dias.

Título: **Arquivo — Eventos de dispositivo relacionados a este arquivo**

- Descrição: exibe os eventos do dispositivo que incluem o nome do arquivo em um período específico.

Título: **Arquivo —** **Eventos de arquivos confidenciais**

- Descrição: lista os eventos de arquivos confidenciais neste dispositivo nos últimos dez dias.

Título: **Arquivo — Origem do arquivo**

- Descrição: exibe a origem ou fonte do arquivo nos últimos 30 dias.

Título: **Processo —** **Resumo das execuções de processos**

- Descrição: resume as execuções de processos neste dispositivo em um período específico.

Título: **Processo — Execuções detalhadas de processos**

- Descrição: detalha todos os eventos de execução de processos no dispositivo em um período curto, por exemplo, uma hora.

Título: **Processo — Eventos detalhados de processos**

- Descrição: detalha eventos específicos de execução de processos no dispositivo em um período definido.

Título: **Movimentação lateral — RDP para o dispositivo**

- Descrição: conexão RDP de entrada neste dispositivo em um período específico.

Título: **Movimentação lateral — Entrada no dispositivo**

- Descrição: eventos de entrada de outros dispositivos neste dispositivo em um período específico.

Título: **Movimentação lateral — Entradas no dispositivo nos últimos dez dias**

- Descrição: eventos de entrada de outros dispositivos neste dispositivo nos últimos dez dias.

Título: **Rede — Eventos de rede de saída**

- Descrição: eventos de rede de saída do dispositivo, incluindo tentativas e conexões com falha.

Título: **Rede — Eventos de rede de entrada**

- Descrição: eventos e tentativas de rede de entrada do dispositivo em um período específico.

Título: **Rede — Portas de escuta do dispositivo**

- Descrição: exibe as portas de escuta do dispositivo em um período específico.

Título: **Eventos do dispositivo — Eventos de tarefas agendadas**

- Descrição: eventos de tarefas agendadas observados em um dispositivo em um período específico.

Título: **Eventos do dispositivo — Eventos de conta de usuário**

- Descrição: eventos de conta de usuário observados em um dispositivo em um período específico.

Título: **Eventos do dispositivo — Conta de usuário adicionada ou removida de um grupo local**

- Descrição: conta de usuário adicionada ou removida de um grupo local em um período específico.

Título: **Atividades suspeitas — Regras de ASR acionadas**

- Descrição: regras de ASR acionadas neste dispositivo nos últimos sete dias.

Título: **Atividades suspeitas — Detecção de scripts do AMSI**

- Descrição: detecções de script da Windows Antimalware Scan Interface (AMSI) nos últimos sete dias.

Título: **Atividades suspeitas — Eventos do Exploit Guard**

- Descrição: eventos do Exploit Guard detectados neste dispositivo nos últimos sete dias.

Título: **Atividades suspeitas — Eventos da Proteção de Rede**

- Descrição: eventos da Proteção de Rede acionados neste dispositivo nos últimos sete dias.

Título: **Atividades suspeitas — Tentativas de adulteração do dispositivo**

- Descrição: possíveis tentativas de adulteração neste dispositivo nos últimos sete dias.

<br>

## O “Custom Plugin Defender Device Info” oferece as seguintes habilidades:

Título: **Informações do sistema operacional do dispositivo**

- Descrição: informações mais recentes do sistema operacional do dispositivo, usando o nome do dispositivo como entrada.

Título: **IPs atuais e anteriores do dispositivo**

- Descrição: IPs atuais e anteriores atribuídos a este dispositivo nos últimos dez dias.

Título: **Usuários do dispositivo e contagem de entradas**

- Descrição: lista os usuários que entraram neste dispositivo e o número de vezes nos últimos dez dias.

Título: **Informações de alertas do dispositivo**

- Descrição: alertas observados neste dispositivo nos últimos 30 dias.

Título: **Aplicativos instalados no dispositivo**

- Descrição: aplicativos instalados atualmente neste dispositivo.

Título: **Informações de vulnerabilidades do dispositivo**

- Descrição: vulnerabilidades identificadas neste dispositivo.

Título: **Vulnerabilidades críticas do dispositivo**

- Descrição: vulnerabilidades com pontuação CVSS 7 ou superior ou com exploit disponível publicamente.