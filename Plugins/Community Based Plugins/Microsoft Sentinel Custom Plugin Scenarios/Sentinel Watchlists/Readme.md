# Integração de listas de observação do Sentinel ao Security Copilot

## DESCRIÇÃO
Este plugin demonstra a possibilidade de integrar dados de uma lista de observação do Microsoft Sentinel ao Security Copilot. <br>
O manifesto se refere a uma lista de observação que contém usuários confiáveis (**TrustedUsers**), mas pode ser facilmente adaptado a outras listas.

``` kql
Template: |-
            _GetWatchlist('TrustedUsers') | distinct TrustedUsers
```
---

## TIPO E REQUISITOS
**TIPO**: KQL (Sentinel) <br>
**FONTE**: qualquer lista de observação do Sentinel <br>
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
      <td><b>GetTrustedUsers</b></td>
      <td align="center">Obtém a lista de usuários confiáveis mantida como uma lista de observação do Microsoft Sentinel</td>
      <td>
        <ul>
        </ul>
      </td>
    </tr>
  </tbody>
</table>


---

## PROMPTS DE EXEMPLO

- `« Obtenha os usuários confiáveis no Sentinel »`
---

## CAPTURAS DE TELA
<div align="center">
  <img src="https://github.com/mariocuomo/Security-Copilot/blob/main/Images/Community%20Plugins/WatchlistKQL/TrustedUserWatchlist.png" width="700"> </img>
</div>

Para obter mais informações, consulte: [Criação de um plugin KQL do Security Copilot para consultar listas de observação do Sentinel](https://rodtrent.substack.com/p/creating-a-copilot-for-security-kql)
