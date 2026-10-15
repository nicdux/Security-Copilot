![Logotipo do Security Copilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)
# Análise de entrada do usuário

**Plugins necessários**: Microsoft Entra, Microsoft Intune

**Entradas necessárias**: UPN

**Descrição**: investigue as entradas do usuário, acesse seu perfil de risco, identifique a conformidade do dispositivo e conclua com um resumo da análise.

1. Recupere o histórico do usuário que está sendo investigado
 ```
What is <UPN> sign-in history?
 ```
2. Recupere informações sobre entradas que falharam
 ```
Are there any failed sign-in attempts? If so, what are the details?
 ```
3. Recupere informações sobre os aplicativos acessados durante os eventos de entrada
 ```
What applications has the user accessed during these sign-in events?
 ```
4. Verifique a conformidade dos dispositivos usados pelo usuário
```
What device(s) has the user used for these sign-ins? Are these devices compliant and managed?
```
5. Recupere a localização das entradas do usuário
```
What is the sign-in location and IP address used for sign-in?
```
6. Consulte o nível de risco do usuário
```
What is the risk level during sign-in? Are there any detected risk events?
```
7. Consulte o status das entradas do usuário
```
What is the user's sign-in status? Are there any failures? If so, what are the reasons for these failures?
```
8. Verifique se o usuário utiliza MFA
```
Does the user's sign-in satisfy the Multi-Factor Authentication (MFA) requirement?
```
9. Consulte as políticas de acesso condicional aplicadas ao usuário
```
/What specific conditional access policies were applied during these sign-in events
```
10. Verifique a última alteração de senha do usuário
```
When did the user last change their password?
```
11. Resuma a investigação
```
Can you summarize the above investigation and provide a conclusion and recommendation
