![Logotipo do Security Copilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)

# Análise de rede — solicitação de URI

Inspirado no [GreyNoise Sift](https://www.greynoise.io/blog/introducing-sift-automated-threat-hunting) e nas possibilidades de auxiliar em diversas áreas nas quais o tráfego Web das camadas 4 a 7 é capturado em um SIEM e pode exigir uma análise adicional. Entre os casos de uso estão a análise de uma URI, do tráfego Web recebido ou o uso de um prompt em linguagem natural para KQL a fim de obter insights adicionais do Azure Web App Firewall.
<a  name="URI Analysis"></a>

Aviso de isenção de responsabilidade: estes prompts são apenas exemplos e estão sujeitos a alterações.




**Plugins necessários**: Microsoft Defender Threat intelligence, Microsoft Defender XDR

**Entrada necessária**: < AppServer >

**Entrada necessária**: < URIRequest >

**Descrição**: analise uma solicitação de servidor de aplicativos, verifique os parâmetros da URI, indique se ela está relacionada a uma CVE conhecida e apresente métodos para tratar a CVE no servidor.

1. Analise a solicitação de URI e os parâmetros do servidor de aplicativos
 ```
 A <appserver> web server recieved a web call <urirequest> , please decode what is being passed in the URI parameters and explain what this URI with parameters is doing in each step
 ```
2. Identifique CVEs conhecidas com base na solicitação Web
 ```
Are there any known CVEs associated with this exploit ?
 ```
3. Identifique um plano de mitigação da CVE no servidor de aplicativos Web
 ```
Can you provide a remediation plan with actionable steps for this exploit and the CVEs above
 ```
