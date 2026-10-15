# Projeto Inicial de Triagem de Incidentes

Este projeto inicial é um plugin GPT autocontido para o Microsoft Security Copilot. Ele recebe evidências de um incidente e, opcionalmente, o contexto do ambiente para produzir um relatório estruturado de triagem inicial.

## Arquivos

- `manifest.yaml`: manifesto do plugin que pode ser carregado no Security Copilot e contém um template de prompt GPT incorporado.

## Pré-requisitos

- Acesso ao Microsoft Security Copilot.
- Permissão para adicionar plugins personalizados. O administrador do Security Copilot deve permitir que Proprietários ou Colaboradores gerenciem plugins personalizados.
- Dados de incidente aprovados para uso no ambiente do Security Copilot da sua organização.

## Importar o plugin

1. Abra o Microsoft Security Copilot.
2. Selecione **Fontes** na barra de prompts.
3. Em **Plugins**, selecione **Gerenciar plugins**.
4. Selecione **Adicionar plugin**.
5. Escolha a opção para carregar um plugin personalizado.
6. Carregue o arquivo `manifest.yaml`.
7. Preencha as informações solicitadas pelo Security Copilot e habilite o plugin.

Os nomes das opções podem variar caso a interface do produto esteja configurada em outro idioma.

## Testar o projeto inicial

Solicite ao Security Copilot que use o **Projeto Inicial de Triagem de Incidentes** e forneça uma entrada como:

```text
Realize a triagem deste incidente.

Contexto do incidente:
- 2026-10-15T12:03:00Z: entrada bem-sucedida do usuário analista@example.com a partir de 203.0.113.10.
- 2026-10-15T12:07:00Z: a mesma conta criou uma regra de encaminhamento de caixa de entrada.
- O endereço IP de origem não foi observado para esse usuário nos 30 dias anteriores.

Contexto do ambiente:
- O usuário tem acesso a relatórios financeiros.
- O endereço IP de origem não é um endereço de saída corporativo aprovado.
```

Use dados sintéticos ou devidamente sanitizados nos testes iniciais. Os endereços do exemplo são reservados para documentação e não representam indicadores reais.

## Personalizar o projeto

Antes de publicar este projeto como seu próprio plugin comunitário:

1. Renomeie a pasta e atualize `Descriptor.Name`, `Descriptor.DisplayName` e `Descriptor.Description`.
2. Renomeie a habilidade e atualize suas descrições de acordo com o cenário desejado.
3. Ajuste as entradas e as seções da saída, mantendo cada nome de entrada sincronizado com sua `{{variavelDoTemplate}}`.
4. Teste entradas ausentes, parciais, contraditórias e semelhantes a tentativas de injeção de prompt.
5. Confirme que o plugin nunca recebe segredos, credenciais, tokens de acesso nem dados proibidos pela sua organização.
6. Adicione capturas de tela ou documentação específica do cenário caso pretenda contribuir com o plugin para este repositório.

## Decisões de projeto

- `gpt-4o` é o nome de modelo atualmente documentado para plugins GPT do Security Copilot.
- O prompt está incorporado ao manifesto para permitir o carregamento imediato do projeto inicial. Para plugins de produção, a Microsoft recomenda `TemplateUrl` ou `PackageUrl` quando o template é hospedado e versionado separadamente.
- O prompt separa fatos de hipóteses, identifica incertezas e trata o conteúdo do incidente como dados não confiáveis.
- Os identificadores técnicos permanecem em inglês para manter compatibilidade com as convenções dos exemplos oficiais; todo o conteúdo destinado ao usuário está em PT-BR.

## Referências

- [Criar plugins personalizados](https://learn.microsoft.com/pt-br/copilot/security/custom-plugins)
- [Plugins GPT no Microsoft Security Copilot](https://learn.microsoft.com/pt-br/copilot/security/plugin-gpt)
- [Visão geral dos plugins do Security Copilot](https://learn.microsoft.com/pt-br/copilot/security/plugin-overview)
