# Obter comentários de incidentes do Sentinel

## DESCRIÇÃO
Este plugin mostra como obter comentários associados a um incidente do Sentinel para adicionar contexto a uma investigação realizada com o Security Copilot.

---

## TIPO E REQUISITOS
**TIPO**: KQL (Sentinel) <br>
**FONTE**: tabela _SecurityIncident_ <br>
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
      <td><b>SentinelIncidentComments</b></td>
      <td align="center">Obtém comentários de incidentes do Sentinel</td>
      <td>
        <ul>
          <li>
            <i>incidentNumber</i> <br>
          </li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>


---

## PROMPTS DE EXEMPLO

- `« Obtenha os comentários do Sentinel sobre o incidente <INCIDENT-NUMBER> e deduza o que foi feito para investigá-lo »`

---

## CAPTURAS DE TELA
<div align="center">
  <img src="https://github.com/mariocuomo/Security-Copilot/blob/main/Images/Community%20Plugins/SentinelIncidentComments/SentinelIncidentComments.png" width="700"> </img>
</div>
