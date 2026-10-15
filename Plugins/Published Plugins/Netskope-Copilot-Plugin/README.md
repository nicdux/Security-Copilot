# MsftCoPilotPlugin

A Microsoft aprimorou o Security Copilot pré-instalando um conjunto de plugins para seus serviços de segurança e sites usados com frequência. Além disso, você pode incorporar plugins personalizados da Netskope, ampliando os recursos de IA generativa em sua plataforma Netskope.

Requisitos
Verifique se você tem uma conta ativa do Microsoft Security CoPilot e consegue entrar em: https://securitycopilot.microsoft.com/
Para obter mais informações sobre o Security CoPilot, consulte: Introdução ao Microsoft Security Copilot Early Access Program
Crie um arquivo YAML local chamado NetskopeCoPilotSkill.yaml (o nome do arquivo pode ser qualquer um). Em seguida, cole o conteúdo indicado abaixo no arquivo YAML:

https://github.com/mitchellgulledge2/MsftCoPilotPlugin/blob/main/Manifest.yaml

Observe que será necessário adicionar o domínio do seu tenant na linha 18 do arquivo YAML.

Além do arquivo local, você também precisará do token da API Netskope do seu tenant com permissões Read para os endpoints da API Netskope v2 abaixo:

![Endpoints da API Netskope v2](https://github.com/mitchellgulledge2/MsftCoPilotPlugin/assets/145486744/9e9c9c6e-bc48-47b7-b3df-b0c42ac1b221)

![Permissões dos endpoints da API Netskope v2](https://github.com/mitchellgulledge2/MsftCoPilotPlugin/assets/145486744/0b5535b9-0f88-4a3b-991d-551520e99668)

Para obter mais informações sobre como criar um token de API v2, consulte: https://docs.netskope.com/en/netskope-help/admin-console/rest-api/rest-api-v2-overview-312207/

Como carregar o plugin Netskope como um plugin personalizado
Como instalar plugins personalizados
É aqui que você carregará o Netskope Threat Hunting and Reporting Plugin.

Todo plugin do Copilot exige um arquivo de manifesto no formato YAML ou JSON, por exemplo, skillset.yaml ou skillset.json, que descreva os metadados do plugin e como invocá-lo. Esse arquivo está disponível no link acima.

1. Selecione o ícone de plugin do Security Copilot.

2. Em Manage plugins, role a página até a seção Custom.

![Seção Custom em Manage plugins](https://github.com/mitchellgulledge2/MsftCoPilotPlugin/assets/145486744/f5f98d18-72c1-4b89-8849-7c86e3e3a746)

3. Selecione Add plugin. Você pode escolher entre um plugin do Security Copilot e um plugin da OpenAI.

 ![Opções para adicionar um plugin](https://github.com/mitchellgulledge2/MsftCoPilotPlugin/assets/145486744/4e1a4e73-c361-4b0e-a5ef-648f3dee84df)

4. Em Select an upload format, clique em Security Copilot plugin e carregue o arquivo YAML criado na seção Requisitos.

![Carregamento do arquivo YAML](https://github.com/mitchellgulledge2/MsftCoPilotPlugin/assets/145486744/17b535b0-1e93-4efa-9fd2-5cebaade63e4)

5. Por fim, você poderá colar o token da API Netskope obtido nas etapas anteriores. Consulte as informações acima.

Exemplos de prompts da Netskope

![Exemplo de prompt da Netskope 1](https://github.com/mitchellgulledge2/MsftCoPilotPlugin/assets/145486744/cf4ca7b8-18da-4a29-a432-46a231c9cf17)
![Exemplo de prompt da Netskope 2](https://github.com/mitchellgulledge2/MsftCoPilotPlugin/assets/145486744/b422225b-7803-4fde-93c2-ad2e16fd8f91)
![Exemplo de prompt da Netskope 3](https://github.com/mitchellgulledge2/MsftCoPilotPlugin/assets/145486744/65dc4d28-6000-4e21-81b7-560f5e42f632)
![Exemplo de prompt da Netskope 4](https://github.com/mitchellgulledge2/MsftCoPilotPlugin/assets/145486744/029eccfa-4691-4e75-a8e0-d38e5c8e7945)
![Exemplo de prompt da Netskope 5](https://github.com/mitchellgulledge2/MsftCoPilotPlugin/assets/145486744/0103c513-4246-4051-9555-59526f7a4477)

Você pode validar se as seis habilidades estão visíveis inserindo /get, como mostrado abaixo:

![Validação das seis habilidades com /get](https://github.com/mitchellgulledge2/MsftCoPilotPlugin/assets/145486744/f6f458d5-e5d5-426b-a1ff-d38ccb866896)
