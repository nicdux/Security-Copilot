![Logotipo do Security Copilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)
# Ativos de alto risco da superfície de ataque externa

**Plugins necessários**: *Microcrosoft Defender threat intelligence*, *Microsoft Defender External attack Surface management*

**Entrada necessária**: < Companyname >

**Descrição**: este Promptbook identifica ativos de alto risco que foram alvos recentes.

1. **Obtenha insights do EASM sobre uma organização específica**:
   ```
   Get the high priority attack surface insights using a prebuilt footprint for <CompanyName> using External Attack surface Management
   ```
2. **Capture CVEs específicas do resumo**:
   ```
   List all the CVE IDs from the above summary
   ```
3. **Veja como as CVEs estão relacionadas a artigos sobre ameaças**:
   ```
   Check if any of the CVE IDs are associated with any MDTI articles
   ```
4. **Contextualize os artigos sobre ameaças**:
   ```
   List all the articles and the dates they were published
   ```
5. **Restrinja os resultados a artigos publicados em um período curto**:
   ```
   List all the articles which were published in the last 3 months
   ```
6. **Identifique quais agentes de ameaça estão associados aos artigos**:
   ```
   Tell me of any threat actors associated with these articles
   ```
7. **Identifique os setores visados pelos agentes de ameaça**:
   ```
   What industries do these threat actors target?
   ```
8. **Liste os ativos que foram visados**:
   ```
   List all the approved host and IP addresses from the <CompanyName> attack surface associated with the CVE IDs found in the MDTI articles in the last 3 months
   ```

