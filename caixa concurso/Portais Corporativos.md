São pontos centrais que reúnem informações significativas para o negócio, que permitem gerenciar tais informações de uma forma simples e intuitiva. É uma página que oferece **um único ponto de acesso** a informações em uma instituição que pode ser **por meio da Intranet:** **único acesso, porém, várias fontes** ou **internet: portais web**. 

![[pc-view.png]]

```ad-tip
##### Deve fornecer
Integração de Aplicação e Componentes. Ambiente de Desenvolvimento. Gestão, Manutenção e Monitoramento. Arquitetura de Sistemas. Desempenho. Segurança. Futuro do Fornecedor e Evolução da Plataforma.
```
### Arquitetura 
- **Camada de Apresentação ou Personalização**: componentes que definem como serão os aspectos visuais do portal, assim como as formas como usuários selecionam conteúdos de maior relevância. 
- **Taxonomia e Mecanismos de Busca**: os portais devem oferecer um mecanismo para que as informações possam ser encontradas por quem as procure. Essa camada engloba mecanismos de busca e auxílio no acesso a informações.
- **Aplicações Web**: engloba uma grande variedade de soluções, dependendo de seu contexto, tais como: intranet, internet, correio eletrônico, fórum de discussões, business, groupware, workflow, CMS, etc. 
- **Conectores**: essa camada é responsável pelo controle de acesso e integração entre sistemas de informações, tais como SGBD, ERP, CRM, etc. Na verdade, não é uma camada em si – é mais um suporte às outras camadas
### Classificação 
- **Portal Horizontal**:  É aquele que fornece informações e recursos sobre diversos assuntos como notícias,  entretenimento, compras, chat, e-mail, feeds, etc (Ex: Folha, Terra, Uol).
- **Portal Vertical**: É aquele que reúne informações de suporte para que seus usuários possam organizar e compartilhar dados sobre um assunto específico (Ex: Portal do Tesouro Nacional).
- **Portal de Informação/Conteúdo**: Serve para armazenar conteúdos de temas específicos, funcionando como máquinas de buscas. No entanto, não oferece recursos interativos ou colaborativos. Ele é conhecido como Portal Intranet e inclui links para informações dentro e fora da organização.
- **Portal de Negócio**: Tem como função disponibilizar informações necessárias para a tomada de decisões para usuários corporativos.
- **Portal de Suporte à Decisão**: Esse portal permite que os usuários organizem e encontrem informações corporativas em um conjunto de sistemas que constituem a cadeia produtiva de informações de negócios. Ele utiliza ferramentas inteligentes e aplicativos analíticos para capturar informações armazenadas em bases de dados operacionais, Data Warehouses ou sistemas externos.
- **Portal Cooperativo**: Utiliza ferramentas corporativas para prover acesso a informações geradas por grupos ou indivíduos utilizando ferramentas cooperativas de trabalhos em grupo (groupware) e de fluxo de tarefas/documentos (workflow). As informações manipuladas são geralmente não estruturadas e encontram-se sob a forma de textos, memorandos, gráficos, mensagens de correio eletrônico, boletins informativos.
- **Portal de Especialistas**: Deve ser completo e ter a capacidade de relacionar e unir pessoas de várias áreas com base em suas habilidades e experiências. A comunicação deve ser feita em tempo real. 
- **Portal de Conhecimento**: Ponto de convergência dos Portais de Informações, Portais Cooperativos e Portais de Especialistas, sendo capaz de implementar tudo que os outros tipos de portais implementam e, além disso, fornecer conteúdo personalizado de acordo com a atividade de cada usuário.
- **Portal de Informações Empresariais**: Utiliza metadados e a linguagem XML para integrar os dados não-estruturados, mantidos em arquivos textuais, relatórios, mensagens de correio eletrônico, gráficos, imagens, etc aos dados estruturados das bases de dados do Data Warehouse, fornecendo acesso às informações institucionais a partir de uma interface individualizada.
### Estágios 
1. **Referencial**: Máquina de busca, com catálogo hierárquico. 
2. **Personalizado**: O usuário, por meio de um identificador e uma senha, pode criar uma visão personalizada do conteúdo do portal, conhecida como “Minha Página”. Essa visão mostra apenas as categorias que interessam a cada usuário. Os usuários podem publicar documentos no repositório corporativo para que esses sejam também visualizados por outros usuários.
3. **Interativo**: Incorpora aplicativos que melhoram a produtividade das pessoas e equipes, tais como correio eletrônico, calendários, agendas, fluxos de atividades, gerência de projeto.
4. **Especializado**: Baseados em funções profissionais, para gerência de atividades específicas na instituição, tais como vendas, finanças, recursos humanos, etc. Essa geração envolve a integração de aplicativos corporativos com o portal, de forma que os usuários possam executar transações.
### Funcionalidades Básicas
1. **Colaboração**: As equipes devem ter a possibilidade de compartilharem funcionalidades de forma dinâmica e interativa. Além disso, essas equipes podem trabalhar de forma integrada, mesmo estando em locais diferentes. 
2. **Personalização**: Trata-se da possibilidade de cada usuário personalizar sua forma de navegação, layout, assim como definir facilmente os aplicativos que serão integrados ao seu próprio portal.
3. **Single Sign-on**: Trata-se da possibilidade de autenticação segura e única dos usuários do portal.
4. **Integração**: Permite reunir, em um único ambiente, todos os sistemas e aplicações web de uma organização.
5. **Gestão de Conteúdo**: Compreende o ciclo de criação, revisão, aprovação, indexação e publicação de conteúdo. Ele pode ser submetido a um fluxo de revisão e aprovação antes de ser publicado – para tal, inclui conceitos de workflow.
6. **Gestão do Conhecimento**: Compreende o gerenciamento das informações internalizadas pelos indivíduos que compõem uma organização. Os portais fornecem uma solução para as práticas de gestão do conhecimento em um único front-end.
7. **Mecanismos de Busca**: permite realizar buscas por informações em bancos de dados e outros arquivos disponíveis.****
8. **Taxonomia e Categorização**: Independentemente do poder do mecanismo de busca empregado, toda organização deve lidar com a questão da categorização e organização da informação. A categorização adiciona informação de indexação (metadados) aos documentos, para que estes sejam organizados de acordo com uma taxonomia e sejam facilmente encontráveis mais tarde.
### Portlet
Portal é uma aplicação que agrega vários portlets, permitindo aos usuários customizarem a camada de apresentação. Portlets são componentes web baseados em Java, gerenciado por um Container (Chamado de Pluto) e que processam requests, gerando conteúdo dinâmico. E o Portlet Container fica entre o Portal e os Portlets, fornecendo um ambiente de execução, semelhante ao Servlet Container e às Servlets.

```ad-info
##### Fragmento
O conteúdo gerado por um Portlet é conhecido como fragmento. Esses fragmentos são pedaços de marcação (Exemplo: HTML, XHTML, WML) que seguem um conjunto de regras e podem ser agregados com outros fragmentos para formar um documento completo. Tipicamente, um conjunto de portlets formam uma página do portal. Eles já são pré-fabricados e podem ser usados em diversos ambientes.
```

![[pc-porlet.png]]

```ad-summary
##### JSR 286
- Permite a manipulação de eventos;
- Permite o compartilhamento de parâmetros;
- Permite o endereçamento de recursos;
- Permite o alinhamento com WSRP 2.0;
- Oferece suporte ao AJAX;
- Atendimento dos requerimentos de armazenamento de preferências do usuário;
```
#### Container Portlet
Responsável por controlar o ciclo de vida de um Portlet (`init`, `processAction`, `render` e `destroy `), fornecendo informações sobre seu ambiente, assim como controlando as requisições do usuário e coletando respostas.

![[pc-portlet-container.png]]

Na imagem, um cliente autenticado faz uma requisição HTTP para o portal, que manda o Portlet Container invocar o Portlet App específico. O resultado é devolvido para o portal, que o agrega junto de outros resultados e envia de volta para o cliente.

```ad-note
##### Semelhanças com Servlets
Ambos são componentes web baseados em java; ambos são gerenciados por um contêiner especializado; ambos geram conteúdo dinâmico; ambos possuem um ciclo de vida gerenciado por um contêiner; ambos interagem com cliente web via requisição e resposta; entre outros.
```

```ad-note
##### Diferenças de Servlets
Portlets só geram fragmentos e, não, documentos completos; não estão diretamente vinculados a uma URL; podem existir vários em uma única página do portal; possuem modos mais refinados de manipular requisições, ações e renderizações; entre outras.
```
### RSS
É conteúdo web ou resumos de conteúdo web juntamente com os links para as versões completas deste conteúdo. O Really Simple Syndication (RSS) possibilita distribuir conteúdo web atualizado para diversos outros sites. Se você assina o Feed RSS de algum site ou portal, você receberá notícias e atualizações de diversos sites sem ter que visitá-los. O RSS é um formato XML que permite a publicação de um item de informação e sua disponibilização a diversos programas, chamados agregadores.
### Modelo de Acessibilidade do Governo Eletrônico
Tem o compromisso de ser o norteador no desenvolvimento e a adaptação de conteúdos digitais do governo federal, garantindo o acesso a todos. As recomendações do eMAG seguem a implementação internacional WCAG (Web Content Accessibility Guidelines: Recomendações de Acessibilidade para Conteúdo Web), permitindo que a implementação da acessibilidade digital seja conduzida de forma padronizada, de fácil implementação, coerente com as necessidades brasileiras e em conformidade com os padrões internacionais.
#### Recomendações 
- Seguir o modelo semântico corretamente instituído pela W3C.
- Todo vídeo gravado deve possuir legendas e uma transcrição em libras.
- Áudio gravado deve possuir uma transcrição descritiva e é desejável a alternativa em libras.
- A decisão de utilizar-se de novas instâncias – por exemplo abas ou janelas - para acesso a páginas e serviços ou qualquer informação deve ser de escolha do usuário. Assim, não devem ser utilizados
	-  Pop-ups;
	- A abertura de novas abas ou janelas;
	- O uso do atributo `target=“_blank”`;
	- Mudanças no controle do foco do teclado;
	- Entre outros elementos, que não tenham sido solicitadas pelo usuário.
- Não criar páginas com atualização automática periódica. (não utilizar atributos como `<'meta http-equiv="refresh" content="30" /'>,`)
- Fornecer alternativa para modificar limite de tempo, deve haver opções de desligar, ajustar ou prolongar esse limite.
- Se algum elemento de uma página possuir conteúdo em um idioma diferente do principal, este deverá estar identificado pelo atributo `lang` do html.
- Os documentos devem ser disponibilizados preferencialmente em HTML. Também podem ser disponibilizados no formato ODF ou PDF.
#### Processo de Criação
1. **Padrões Web**: Para se criar um ambiente online efetivamente acessível é necessário, primeiramente, que o código esteja dentro dos padrões Web internacionais definidos pelo W3C.
2. **Recomendações de Acessibilidade**: As diretrizes ou recomendações de acessibilidade (WCAG) explicam como tornar o conteúdo Web acessível a todas as pessoas, destinando-se aos criadores de conteúdo Web (autores de páginas e criadores de sítios) e aos programadores de ferramentas para criação de conteúdo.
3. **Avaliação de Acessibilidade**: Após a construção do ambiente online de acordo com os padrões Web e as diretrizes de acessibilidade, é necessário testá-lo para garantir sua acessibilidade.
4. **Manutenção de Acessibilidade**: A promoção da acessibilidade é um processo contínuo, recomenda-se que testes sejam realizados, de forma pontual, a cada alteração de conteúdo e validações globais em espaços determinados de tempo.
#### Elementos padronizados de acessibilidade digital no Governo Federal
Esses elementos padronizados de acessibilidade digital que devem estar presentes em todos os sítios do governo federal para facilitar o acesso ao cidadão.
##### Barra de Acessibilidade
- Alto contraste
- Atalhos (para Menu, Conteúdo e Busca)
- Acessibilidade (link para a página contendo os recursos de acessibilidade do sítio)
##### Mapa do sítio
O mapa do sítio deve ser disponibilizado em forma de lista hierárquica (utilizando os elementos de lista do HTML), podendo conter quantos níveis forem necessários.
##### Página de descrição com os recursos de acessibilidade
Esta página apresenta os recursos de acessibilidade presentes no sítio, como as teclas de atalho disponíveis, as opções de alto contraste, detalhes sobre testes de acessibilidade realizados (validadores automáticos, leitores de tela e validação humana) no sítio e outras informações pertinentes a respeito de sua acessibilidade. O link para a página contendo os recursos de acessibilidade deve ser disponibilizado na barra de acessibilidade.
#### Práticas desaconselhadas 
Algumas práticas, apesar de comuns, configuram-se não só como empecilhos para o acesso de pessoas com deficiência, mas também, o acesso por dispositivos móveis.

- Uso de animações e aplicações FLASH;
- Uso de CAPTCHAS em formulários;
- Tabelas para fins de diagramação;
- Atualizações automáticas periódicas;
- Elementos e atributos considerados depreciados pelo W3C.
