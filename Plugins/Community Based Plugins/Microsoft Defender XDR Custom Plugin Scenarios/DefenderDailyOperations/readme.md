# Operações diárias do Defender

## DESCRIÇÃO
Este plugin ajuda a compreender a abordagem recomendada para integrar várias habilidades relacionadas em um único plugin. O exemplo de código fornecido demonstra a combinação de duas habilidades para obter informações de algumas tabelas do Defender. Você pode ampliar este exemplo para extrair detalhes adicionais de tabelas personalizadas, entre outras fontes.

---

## TIPO E REQUISITOS
**TIPO**: KQL (Defender) <br>
**FONTE**: tabelas _DeviceInfo_ e _EmailEvents_ <br>
**REQUISITOS**: acesso ao Defender XDR

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
      <td><b>GetDefenderDevices</b></td>
      <td align="center">Obtém os dez principais dispositivos do Defender com base no estado do dispositivo e na exposição nas últimas oito horas</td>
      <td>
        <ul>
          <li>
            <i>devicehealthstate</i> <br> (Active, Misconfigured, Inactive)
          </li>
          <li><i>exposurelevel</i></li> (Low, Medium, High)
        </ul>
      </td>
    </tr>
    <tr>
      <td><b>GetLatestEmailsByRecipient</b></td>
      <td align="center">Obtém os emails mais recentes recebidos pelo usuário com o endereço de email especificado</td>
      <td>
        <ul>
          <li><i>email</i></li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>


---

## PROMPTS DE EXEMPLO

- `« Obtenha os emails mais recentes recebidos pelo usuário <YOUR-EMAIL-ADDRESS> »`
- `« Mostre os dispositivos do Defender com estado de integridade Active e nível de exposição High »`
---

## CAPTURAS DE TELA
<div align="center">
  <img src="https://github.com/Azure/Security-Copilot/tree/main/Images/Community%20Plugins/DefenderDailyOperations/GetLatestEmailsByRecipient.png" width="700"> </img>
  <img src="https://github.com/Azure/Security-Copilot/tree/main/Images/Community%20Plugins/DefenderDailyOperations/GetDefenderDevices.png" width="700"> </img>
</div>
