# Atividades de entrada no Security Copilot

## DESCRIÇÃO
Este plugin permite acompanhar quantas entradas ocorreram na experiência autônoma do Security Copilot e quem as realizou. Para cada identidade, é retornada a quantidade de entradas realizadas.

---

## TIPO E REQUISITOS
**TIPO**: KQL (Sentinel) <br>
**FONTE**: tabela _Signinlogs_ <br>
**REQUISITOS**: workspace do Log Analytics com o Sentinel habilitado

---

## HABILIDADES

<table>
  <tbody>
    <tr>
      <th>SkillName</th>
      <th align="center">Descrição</th>
      <th align="center">Parâmetros</th>
    </tr>
    <tr>
      <td><b>SecurityCopilotLogins</b></td>
      <td align="center">Obtém as entradas no portal autônomo do Security Copilot nos últimos três dias</td>
      <td>
        <ul>
        </ul>
      </td>
    </tr>
  </tbody>
</table>


---

## PROMPTS DE EXEMPLO

- `« Obtenha as entradas no portal autônomo do Security Copilot nos últimos três dias e detecte se há anomalias nos acessos dos usuários »`
---

## CAPTURAS DE TELA
<div align="center">
  <img src="https://github.com/mariocuomo/Security-Copilot/blob/main/Images/Community%20Plugins/SecurityCopilotLogins/LoginsAndAnomalies.png" width="700"> </img>
</div>


Para obter mais informações, consulte: [Plugin do Security Copilot: entradas no portal do Security Copilot](https://rodtrent.substack.com/p/copilot-for-security-plugin-copilot)
