![Logotipo do Security Copilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)
# Priorização de incidentes

**Plugin necessário**: *Microsoft 365 Defender*

**Entrada necessária**: < incidentID >

**Descrição**: estes prompts foram criados para orientar o Security Copilot em uma *priorização de incidentes* dentro de um ambiente, desde a identificação inicial até a geração de relatórios detalhados. Adapte-os ao contexto e aos sistemas específicos da sua organização.

1. **Priorize os incidentes existentes**:
   ```
   Give me the top 5 high severity incidents from Microsoft Defender XDR that I should prioritize today. If there are not high severity incidents, give me the top medium severity incidents with the most number of users affected.
   ```

2. **Aprofunde a análise de um incidente específico e pesquise os usuários envolvidos**:
   ```
   For the users involved in <incidentID>, can you give me details about any risky user sign-ins in the past week?
   ```

3. **Aprofunde a análise de uma conta de usuário específica**:
   ```
   Can you tell me if there are any other suspicious activities involving the user?
   ```

4. **Resuma as atividades do usuário**:
   ```
   Thank you! Can you summarize your findings about the user's suspicious activities including the incident it was involved in? Please include any indicators or vulnerabilities that were mentioned.
   ```

5. **Forneça recomendações para proteger melhor o ambiente contra a ameaça**:
   ```
   Can you give me a list of prioritized recommendations that I can do to remove the threat the user introduced in the network?
   ```

