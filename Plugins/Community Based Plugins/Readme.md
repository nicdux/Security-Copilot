![Visão geral do Security Copilot](https://github.com/Azure/Copilot-For-Security/blob/main/Images/ic_fluent_copilot_64_64%402x.png)

# Aviso
- Os plugins acima foram desenvolvidos pela comunidade para o Microsoft Security Copilot por meio de contribuições. É importante observar que esses plugins podem não ser totalmente abrangentes nem representar por completo os recursos das ferramentas de terceiros. Para conhecer uma variedade maior de funcionalidades e acessar plugins publicados por fornecedores e pela Microsoft para o Microsoft Security Copilot, consulte: [**Plugins publicados**](https://github.com/Azure/Copilot-For-Security/tree/main/Plugins/Published%20Plugins)

## Requisitos de publicação de IA responsável para plugins de terceiros do Microsoft Security Copilot

#### Requisitos de publicação de IA responsável para plugins de terceiros no GitHub:

1. O plugin deve ser publicado com uma [cópia preenchida do modelo de transparência fornecido no README do plugin](https://github.com/microsoft/copilot-for-security/blob/main/3P_Plugin_Upload/MSFT_Upload_Template/readme.md), descrevendo o uso pretendido, os principais recursos e informações sobre usos não pretendidos.
    * Todos os plugins devem ter uma descrição que identifique o público-alvo e os usos pretendidos, informe os produtos Microsoft e outros softwares compatíveis, quando aplicável, e inclua os pré-requisitos ou requisitos de uso. A descrição não deve simplesmente repetir o resumo do plugin.
    * Você deve descrever claramente quaisquer limitações, usos não pretendidos, condições ou exceções às funcionalidades e aos recursos descritos do plugin. Os recursos declarados devem estar relacionados às principais funções e à descrição do plugin.
    * O plugin, incluindo a descrição, os metadados e qualquer outro conteúdo fornecido, deve descrever seus recursos, pontos fortes e diferenciais, inclusive a compatibilidade com outras ofertas.
    * Não é permitido fazer marketing comparativo, incluindo usar logotipos ou marcas registradas de concorrentes na listagem da oferta ou incluir etiquetas ou outros metadados que façam referência a ofertas ou marketplaces concorrentes.

2. Os plugins não devem gerar, conter nem fornecer acesso a conteúdo gerado por inteligência artificial (IA) que seja impróprio, prejudicial ou ofensivo, em conformidade com as políticas descritas no item 3. O desenvolvedor do plugin deve agir em tempo hábil para solucionar problemas relatados por usuários ou pela Microsoft relacionados a conteúdo impróprio, prejudicial ou ofensivo.
    * A menos que seja necessário ao funcionamento adequado do plugin em casos de uso de segurança legítimos, as saídas do plugin não devem conter nem fornecer acesso a conteúdo impróprio, prejudicial ou ofensivo, incluindo, entre outros, conteúdo que:
        * Viole a Política de Uso Aceitável da Microsoft para Serviços Online.
        * Facilite ou exalte atividades prejudiciais no mundo real.
        * Possa representar risco à segurança, à saúde ou ao bem-estar de qualquer pessoa ou a propriedades.
        * Seja difamatório, calunioso ou ameaçador.
        * Seja potencialmente sensível ou ofensivo, ou defenda discriminação, ódio ou violência com base na participação em determinado grupo racial, étnico, nacional, linguístico, religioso ou outro grupo social, ou com base em gênero, idade ou orientação sexual.
        * Facilite ou exalte o uso excessivo ou irresponsável de álcool, produtos de tabaco, drogas ou armas.
        * Contenha conteúdo sexualmente explícito ou pornográfico.
        * Incentive, facilite ou exalte atividades ilegais no mundo real, incluindo a pirataria de conteúdo protegido por direitos autorais.
        * Inclua linguagem obscena ou palavrões excessivos e desnecessários.
        * Seja ofensivo em qualquer país ou região ao qual o plugin se destine. Um conteúdo pode ser considerado ofensivo em determinados países ou regiões devido a leis locais ou normas culturais.

3. O plugin não deve colocar em risco nem comprometer a segurança do usuário, do produto Security Copilot ou de serviços e sistemas relacionados. Estes são critérios relacionados:
    * Os usuários devem ser informados de que estão acessando fontes não autenticadas ao usar o plugin. Transfira dados de clientes somente com autenticação e criptografia em conformidade com os padrões do setor.

4. Se o plugin coletar informações de cartão de crédito ou usar um processador de pagamentos de terceiros que colete essas informações, o processamento do pagamento deverá atender ao Padrão de Segurança de Dados do Setor de Cartões de Pagamento (PCI DSS) vigente.
    * O plugin não deve instalar nem iniciar código executável no ambiente do usuário além do que estiver identificado na listagem da oferta ou puder ser razoavelmente esperado com base nela.
    * Responda o mais rápido possível a suspeitas de eventos de segurança, incluindo incidentes de segurança e vulnerabilidades no software do plugin e nas ofertas de serviço.
    * Teste o plugin e implemente controles técnicos e operacionais adequados para mitigar riscos, inclusive para reduzir o risco de [ataques de injeção de prompt](https://learn.microsoft.com/en-us/ai-builder/azure-openai-human-review#prompt-injection-attacks) em sistemas de IA generativa.

5. Na medida em que os plugins incluam o uso de tecnologia de inteligência artificial, você deve implementar e manter medidas técnicas e organizacionais adequadas para garantir que essa tecnologia esteja em conformidade com todas as leis e padrões do setor, inclusive os padrões e as políticas relacionados ao uso ético ou responsável da inteligência artificial. Mediante solicitação da Microsoft, você concorda em disponibilizar descrições dos controles técnicos e organizacionais implementados e mantidos por sua organização para o uso ético e responsável da tecnologia de inteligência artificial, além de outras informações razoavelmente solicitadas pela Microsoft sobre suas práticas e políticas.

6. A Microsoft reserva-se o direito de remover ou desabilitar um plugin por qualquer motivo, a qualquer momento e sem aviso prévio.
