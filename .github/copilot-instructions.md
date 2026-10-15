# Diretrizes do projeto

## Idioma

- Escreva toda documentação, explicação, mensagem destinada ao usuário, exemplo e texto de interface em português do Brasil (PT-BR).
- Use redação clara e neutra, compreensível também para leitores de Portugal e de outros países lusófonos, evitando regionalismos desnecessários.
- Escreva em PT-BR os comentários necessários para explicar regras de negócio, decisões de segurança, limitações ou comportamentos não evidentes.
- Não adicione comentários que apenas repitam o código. Quando um comentário for necessário, explique com clareza o motivo da implementação, suas restrições e os efeitos esperados.
- Preserve em inglês nomes impostos por schemas, APIs, protocolos, produtos e ferramentas.
- Use identificadores técnicos em inglês quando isso mantiver compatibilidade com o ecossistema ou seguir a convenção da tecnologia utilizada.
- Ao usar um termo técnico em inglês na documentação, explique-o em PT-BR na primeira ocorrência quando o significado não for evidente.

## Documentação

- Inclua instruções completas de pré-requisitos, configuração, execução, validação e solução de problemas relevantes.
- Mantenha exemplos seguros e reproduzíveis, sem credenciais, tokens, segredos ou dados pessoais reais.
- Atualize a documentação relacionada sempre que uma alteração modificar configuração, comportamento ou forma de uso.

## Código e configuração

- Priorize código claro e autoexplicativo; complemente apenas os trechos não triviais com comentários detalhados em PT-BR.
- Mantenha textos de prompts, descrições de plugins e respostas geradas em PT-BR, salvo quando outro idioma for requisito explícito da integração.
- Preserve os nomes de campos definidos pelas especificações do Microsoft Security Copilot, OpenAPI, Azure Resource Manager e demais contratos externos.

## Validação

- Valide sintaxe, schemas e correspondência entre variáveis de entrada e templates antes de concluir alterações.
- Registre na resposta final, em PT-BR, os comandos executados e o resultado das verificações.
