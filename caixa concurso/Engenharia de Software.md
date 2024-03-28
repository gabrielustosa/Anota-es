# Análise e Projeto Orientados a Objetos
A perspectiva empregada na análise é de _objetos_ (coisas, conceitos ou entidades). Durante a Análise OO, a ênfase está em achar e descrever objetos (ou conceitos) no domínio do problema. Por exemplo, num sistema de informação para uma biblioteca, alguns dos conceitos são _Livro_, _Biblioteca_, _Usuário_. Tais objetos podem ter atributos e responsabilidades. Durante o projeto orientado a objeto, a ênfase está em achar objetos lógicos de software que poderão ser eventualmente implementados usando uma linguagem de programação OO. Tais objetos podem ter atributos e métodos. Durante a construção (programação OO), os objetos do projeto são implementados e testados
# Processo Unificado 
Um conjunto de atividades executadas para transformar um conjunto de requisitos do cliente em um sistema de software. Promove o uso de melhores práticas, como desenvolvimento orientado a casos de uso, arquitetura baseada em componentes, controle de versões, e a integração contínua. 

- É baseado em componentes que utilizam interfaces.
- Utiliza toda uma definição em UML.
- Dirigido por casos de usos
- Centrado na arquitetura, Interativo e incremental

É geralmente descrito sobre três perspectivas:

1. Uma perspectiva dinâmica, que mostra as fases do modelo ao longo do tempo.
2. Uma perspectiva estática, que mostra as atividades realizadas no processo.
3. Uma perspectiva prática, que sugere boas práticas a serem usadas durante o processo.

 ```ad-info
 ##### Arquitetura
É um "mapa" do sistema, definindo partes do mesmo como relacionamentos, iterações, mecanismos. implementação, distribuição. É fundamental para entender a visão global, as possibilidades de reuso e evolução do sistema. 
##### Iterativo e incremental
O software não é implementado a partir de um instante no fim do projeto, o ciclo de vida no PU é implementado em iterações.
##### Iterações
É um miniprojeto que resulta em uma versão do sistema liberada interna ou externamente. Essa versão oferece uma melhora incremental sobre a interação anterior. 
```
#### Ciclo de Vida
É decomposto ao longo do tempo em quatro fases sequenciais, cada uma concluída por um marco importante; cada fase é essencialmente um período de tempo entre dois marcos principais. Ao final de cada fase, é realizada uma avaliação para determinar se os objetivos da fase foram cumpridos. Uma avaliação satisfatória permite que o projeto passe para a próxima fase. As 4 quatro fases sequenciais são: **Concepção (Inception), Elaboração (Elaboration),  Construção (Construction) e Transição (Transition)**. Cada fase, é subdivida em iterações que passam por todos os cinco fluxos do trabalho do processo: **Requisitos, Análise, Implementação e Testes**.

- Não se comporta como modelo de cascata, são estreitamente relacionadas ao negócio, e não a assuntos técnicos. 
- Os fluxos de trabalho podem ser realizados a qualquer momento durante o ciclo de desenvolvimento.
- Disciplinas podem ter mais ênfase do que outras.

![[engs-pu-ciclo.png]]

 ##### Concepção
  Estabelecer um business case para o sistema. Você deve identificar todas as entidades externas (pessoas e sistemas) que vão interagir com o sistema e definir as interações. Então, você deve usar essas informações para avaliar a contribuição do sistema para o negócio. Se essa contribuição for pequena, então o projeto poderá ser cancelado depois dessa fase.
 ##### Elaboração
 Desenvolver uma compreensão do problema dominante, estabelecer um framework da arquitetura para o sistema, desenvolver o plano do projeto e identificar os maiores riscos do projeto. No fim dessa fase, você deve ter um modelo de requisitos para o sistema, que pode ser um conjunto de casos de uso da UML, uma descrição da arquitetura ou um plano de desenvolvimento do software.
 ##### Construção
 A fase de construção envolve projeto, programação e testes do sistema. Durante essa fase, as partes do sistema são desenvolvidas em paralelo e integradas. Na conclusão dessa fase, você deve ter um sistema de software já funcionando, bem como a documentação associada pronta para ser entregue aos usuários.
 ##### Transição
 Implica transferência do sistema da comunidade de desenvolvimento para a comunidade de usuários e em seu funcionamento em um ambiente real. Isso é ignorado na maioria dos modelos de processo de software, mas é, de fato, uma atividade cara e, às vezes, problemática. Na conclusão dessa fase, você deve ter um sistema de software documentado e funcionando corretamente em seu ambiente operacional.
#### 4 Ps (Pessoa, Projeto, Produto e Processo)
 ##### Pessoas
 Financiam, escolhem, desenvolvem, gerenciam, testam, usam e são beneficiadas pelo produto.
 ##### Projetos
 Sofrem alterações, determinam os tipos de pessoas que irão trabalhar no projeto e os **artefatos** que serão usados.
 ##### Produto
 Código fonte, diagramas e outros artefatos
 ##### Processo
 Define **quem (papel/pessoa/trabalhadores)** faz **o que (artefato)**, **quando (disciplina)** e **como (atividades)**

```ad-info
##### Artefato
É qualquer tipo de informação criada por uma pessoa (diagramas UML, textos, modelos, interfaces)
##### Trabalhadores
Responsável pela produção ou modificação de artefatos; Exemplos (programador, analista, testador)
##### Atividades
Tarefa que o trabalhador executa afim de produzir ou modificar um artefato.
##### Disciplina
Descreve as sequências das atividades e as iterações com que participa, sendo realizadas a qualquer momento do ciclo.

```
#### Casos de Usos (Cenários de Uso)
Um caso de uso é uma sequência de ações, executada por atores que produzem um ou mais resultados de valor para outros atores. 

- Possibilitam que os requisitos funcionais possam ser capturados na perspectiva de cada usuário do sistema.
- Os testes são baseados nos casos de usos.
- Os requisitos funcionais são expressões através dos casos de uso, que são adicionados a cada interação.

```ad-info
###### Atores
É uma pessoa ou outro sistema

- Todo ator possui uma ou mais metas ao usar o sistema.
```
# UML
#### Diagramas de classe
Um diagrama de classe fornece uma visão estática ou estrutural do sistema. Ele não mostra a natureza dinâmica das comunicações entre os objetos das classes no diagrama. A visibilidade é indicada pelos sinais –, #, ~ ou +, que indicam, respectivamente, visibilidade ``private``, ``protected``, ``package`` ou ``public``.  Atributos estáticos podem ser referenciados sendo sublinhados. 

```ad-tip
###### ~ (package)
Pode ser acessado pela própria classe ou por qualquer classe que pertença ao mesmo pacote. (Pacote)
```

![[engs-uml-dc.png]]

Uma classe abstrata ou método abstrato é indicado pelo uso de itálico no nome da classe no diagrama de classes. Uma interface é indicada acrescentando-se a expressão ``<<interface>>``. 

![[engs-uml-dca.png]]

Os diagramas de classe também podem exibir relações entre classes. Uma classe que seja subclasse de outra classe é conectada a ela por uma seta com uma linha sólida como eixo e com uma ponta triangular vazia. A seta aponta da subclasse para a superclasse. Em UML, uma relação como essa é chamada de generalização  ``Horse -> Thoroughbred/QuarterHouse``. Uma seta tendo como eixo uma linha tracejada indica implementação de interface ``OwnedObject - Horse``. A associação entre duas classes indica que há uma relação estrutural entre elas. Associações são representadas por linhas sólidas. ``OwnedObject - Person``. Uma relação de dependência representa outra conexão entre classes e é indicada por uma linha tracejada (com setas opcionais nas extremidades e com rótulos opcionais) `Thoroughbred - Date`. 
##### Relacionamentos 
 ## Dependência
 Dependência fraca, usualmente transiente, que ilustra que uma classe usa informações de outra classe em algum momento.
 
![[engs-uml-dcd.png]]

 ## Associação
 Relacionamento mais forte que a dependência, indica que a classe mantém uma referência a outra classe ao longo do tempo. As associações podem conectar mais de duas classes.
 
![[engs-uml-dcas.png]]
  
  ## Agregação
  Relacionamento mais específico do que a associação, indica que uma classe é um contêiner ou uma coleção de outras classes. As classes contidas não dependem do contêiner - assim, quando o contêiner é destruído, as classes continuam existindo. 
   ![[engs-uml-ag.png]]
   ## Composição
   Variação mais específico da agregação, este relacionamento indica uma dependência de ciclo de vida forte entre as classes, de modo que quando um contêiner é destruído, seu conteúdo também é.
   ![[engs-uml-co.png]]
   ## Generalização/Especialização
   Relacionamento entre itens gerias (superclasses/classes-mãe) e tipos mais específicos desses itens (subclasses/classes-filha). Representa a herança entre as classes.
   
![[engs-uml-ge.png]]
##### Diagrama de Objeto
É usado para ilustrar instâncias de coisas contidas nos **Diagramas de Classes**. Essas instâncias são conhecidas como objetos e cada um é uma representação concreta de uma classe, em um determinado momento durante a execução do sistema. Esse diagrama é útil para visualizar, especificar e documentar as estruturas de objetos e mostrar como eles se relacionam uns com os outros, capturando assim o estado do sistema em um ponto específico no tempo.
#### Diagrama de Implantação
Focalizam a estrutura do sistema de software e são úteis para mostrar a distribuição física de um sistema de software entre plataformas de hardware e ambientes de execução. Por exemplo, suponha que você esteja desenvolvendo um pacote de renderização gráfica baseado na Web. Os usuários do seu pacote de software usarão o navegador Web para acessar o seu site e introduzir as informações de renderização. O seu site vai renderizar uma imagem gráfica de acordo com as especificações do usuário e a enviará de volta ao usuário. Como a renderização gráfica pode ser cara em termos de computação, você decide tirar a renderização do servidor Web, colocando-a em uma plataforma separada.

![[engs-uml-di.png]]
#### Diagrama de Casos de Uso
Ajudam a determinar a funcionalidade e as características do software sob o ponto de vista do usuário. Um caso de uso descreve como um usuário interage com o sistema, definindo os passos necessários para atingir um objetivo específico (p. ex., gravar uma lista de músicas em um CD). Variações na sequência de passos descrevem vários cenários (p. ex., o que acontece se as músicas da lista não couberem em um CD?). No diagrama de caso de uso, os casos de uso são mostrados como elipses. Os atores são conectados por linhas aos casos de uso que eles executam.

![[engs-uml-cu.png]]

```ad-info
###### Ator
Representa uma entidade externa que interage com o sistema, seja um usuário, outro sistema ou uma entidade organizacional.
###### Relacionamento de Comunicação
Conexão entre um ator e um caso de uso, mostrando a interação.
###### Relacionamento de Extensão `<<extend>>`
Um caso de uso estende outro, adicionando comportamento opcional. (não são utilizados entre atores)
###### Relacionamento de Inclusão `<<include>>`
Um caso de uso inclui as funcionalidades de outro, indicando que é necessário para sua execução.
```
#### Diagramas de Sequência
Ao contrário dos diagramas de classe e de implantação, que mostram a estrutura estática de um componente de software, o diagrama de sequência é utilizado para indicar as comunicações dinâmicas entre objetos durante a execução de uma tarefa (caso de uso). Ele mostra a ordem temporal na qual as mensagens são enviadas entre os objetos para executar aquela tarefa. Podemos usar um diagrama de sequência para mostrar as interações em um caso de uso ou em um cenário do sistema de software.

![[engs-uml-ds.png]]
##### Operadores 
- **alt** para situações alternativas (semelhante a "if-else");
- **opt** para situações opcionais (semelhante a "if" sem o "else");
- **loop** para repetições (semelhante a "while" ou "for");
- **par** para processamento paralelo;
- **critical** para regiões críticas que não devem ser interrompidas;
- **break** quebra de execução
- **neg** negação/interação inválida
- **strict** ordem sequencial estrita
##### Mensagens 
![[engs-uml-sem.png]]
#### Diagrama de Comunicação
Fornece outra indicação da ordem temporal das comunicações, mas dá ênfase às relações entre os objetos e classes em vez da ordem temporal. Em um diagrama de comunicação, os objetos que interagem são representados por retângulos. Associações entre objetos são representadas por linhas ligando os retângulos. Normalmente, há uma seta apontando para um objeto no diagrama, que inicia a sequência de passagem de mensagens. A seta é identificada com um número e um nome de mensagem. Se você estiver interessado em mostrar as relações entre os objetos, além das mensagens que estão sendo enviadas entre eles, o diagrama de comunicação provavelmente é uma opção melhor do que o diagrama de sequência. 

![[engs-uml-dco.png]]
#### Diagrama de Atividade
O diagrama de atividade mostra o comportamento dinâmico de um sistema ou de parte de um sistema por meio do fluxo de controle entre ações que o sistema executa. Ele é similar a um fluxograma, exceto que pode mostrar fluxos concorrentes. O componente principal de um diagrama de atividade é um nó de ação, representado por um retângulo arredondado, que corresponde a uma tarefa executada por um sistema de software. Setas que vão de um nó ação para outro indicam o fluxo de controle. Isto é, uma seta entre dois nós ação significa que, depois que a primeira ação é completada, a segunda ação começa. A escolha do diagrama de atividades é apropriada quando se destina a capturar o fluxo de tarefas entre múltiplos participantes.

![[engs-uml-da.png]]
##### Símbolos 
![[engs-uml-da-s.png]]
#### Diagrama de Estado
Utilizado para modelar o comportamento de um objeto ao longo do tempo, incluindo seus diferentes estados e as transições que ocorrem em resposta a eventos específicos. São muito usados para modelar o comportamento de Interfaces, Casos de Uso, Instâncias de classes. 

![[engs-uml-de.png]]
#### Diagrama de Componentes
Representa a organização e a dependência entre os componentes físicos do sistema, como bibliotecas, módulos ou pacotes.

![[engs-uml-dcom.png]]
#### Diagrama de Pacotes
Diagrama estrutural que mostra como elementos de um sistema são organizados em pacotes, bem como as dependências entre esses pacotes. Eles são úteis para organizar e estruturar um sistema em elementos de mais alto nível, facilitando o gerenciamento de complexidade do sistema.

![[engs-uml-dp.png]]
#### Classificação
**Diagramas Estáticos (ou Estruturais)** modelam a estrutura e organização de um sistema, incluindo informações sobre classes, atributos, métodos, pacotes, etc.
- Diagrama de Classes
- Diagrama de Objetos
- Diagrama de Componentes
- Diagrama de Implantação
- Diagrama de Pacotes

**Diagramas Dinâmicos (ou Comportamentais)** modelam eventos que ocorrem durante a execução de um sistema.
- Diagrama de Casos de Uso
- Diagrama de Sequência
- Diagrama de Atividades
- Diagrama de Estados
- Diagrama de Colaboração
# Engenharia de Requisitos
Os requisitos de um sistema são as descrições do que o sistema deve fazer, os serviços que oferece e as restrições a seu funcionamento. Este, é o processo de descobrir, analisar, documentar e verificar esses serviços e restrições. Idealmente, eles devem especificar somente o comportamento externo do sistema. A elaboração de requisitos é norteada pela criação e pelo refinamento de cenários que descrevem como o usuário e outros atores interagirão com o sistema. Cada cenário de usuário é analisado a fim de extrair classes de análise, ou seja, entidades do domínio de negócio visíveis para o usuário. O documento de requisitos não deve incluir detalhes da arquitetura ou projeto do sistema.  Eles podem ser usados como parte do contrato para a implementação do sistema e devem consistir em uma especificação completa e detalhada de todo o sistema.

```ad-tip
##### Modelo Conceitual
É uma representação abstrata das entidades, conceitos e relações importantes em um determinado domínio de aplicação. Ele descreve os conceitos fundamentais que são relevantes para o sistema que está sendo desenvolvido, independentemente de como o sistema será implementado.

- É definido no processo de elicitação de requisitos.
```
#### Requisitos de Usuário
São abstratos, mais gerais e de alto nível. São declarações, em uma linguagem natural com diagramas, de quais serviços o sistema
deverá fornecer a seus usuários e as restrições com as quais este deve operar.
#### Requisitos de Sistema
Expressam a descrição mais detalhadas das funções, serviços e restrições operacionais do sistema de software. O documento de requisitos do sistema (às vezes, chamado especificação funcional) deve definir exatamente o que deve ser implementado. 
#### Requisitos Funcionais (o que deve ser feito)
São declarações de serviços que o sistema deve fornecer, de como o sistema deve reagir a entradas específicas e de como o sistema deve se comportar em determinadas situações. Em alguns casos, os requisitos funcionais também podem explicitar o que o sistema não deve fazer.

- Descrevem detalhes mais específicos como funções do sistema, suas entradas e saídas, exceções etc.
- A especificação dos requisitos funcionais de um sistema deve ser completa e consistente.
- Exemplos disso incluem processar pagamentos, gerar relatórios ou autenticar usuários.
#### Requisitos Não Funcionais (como deve ser feito)
São restrições aos serviços ou funções oferecidos pelo sistema. Incluem restrições de timing, restrições no processo de desenvolvimento, propriedades emergentes e restrições impostas pelas normas. Ao contrário das características individuais ou serviços do sistema, os requisitos não funcionais, muitas vezes, aplicam-se ao sistema como um todo.

- Eles podem estar relacionados às propriedades emergentes do sistema, como confiabilidade, tempo de resposta e ocupação de área.
- Um único requisito não funcional, tal como um requisito de proteção, pode gerar uma série de requisitos funcionais relacionados
-  São frequentemente mais críticos que requisitos funcionais individuais. 
- Como exemplo, a **interoperabilidade**, que é a capacidade do sistema de se comunicar e operar com outros sistemas, é um exemplo de requisito não funcional.
- Sempre que possível, os requisitos não funcionais devem ser escritos quantitativamente, para que possam ser objetivamente testados. 
##### Requisitos de Produto
Esses requisitos especificam ou restringem o comportamento do software . É um requisito de disponibilidade que define quando o sistema deve estar disponível e o tempo diário permitido de seu não funcionamento. Exemplos incluem os requisitos de desempenho quanto à rapidez com que o sistema deve executar e quanta memória ele requer, os requisitos de confiabilidade que estabelecem a taxa aceitável de falhas, os requisitos de proteção e os requisitos de usabilidade.
 ## Exemplo Real
 O MHC-PMS deve estar disponível para todas as clínicas durante as horas normais de trabalho (segunda a sexta-feira, 8h30 às 17h30). Períodos de não operação dentro do horário normal de trabalho não podem exceder cinco segundos em um dia.
##### Requisitos Organizacionais
Esses são os requisitos gerais de sistemas derivados das políticas e procedimentos da organização do cliente e do desenvolvedor. Exemplos incluem como os usuários se autenticam para o sistema, os requisitos do processo operacional que definem como o sistema será usado, os requisitos do processo de desenvolvimento que especificam a linguagem de programação, o ambiente de desenvolvimento ou normas de processo a serem usadas, bem como os requisitos ambientais que especificam o ambiente operacional do sistema.
 ## Exemplo Real
 Usuários do sistema MHC-PMS devem se autenticar com seus cartões de identificação da autoridade da saúde.
##### Requisitos Externos
Esse tipo abrange todos os requisitos que derivam de fatores externos ao sistema e seu processo de desenvolvimento. Podem incluir requisitos reguladores, que definem o que deve ser feito para que o sistema seja aprovado para uso, por um regulador, tal como um banco central; requisitos legais, que devem ser seguidos para garantir que o sistema opere dentro da lei; e requisitos éticos, que asseguram que o sistema será aceitável para seus usuários e o público em geral.
 ## Exemplo Real
 O sistema deve implementar as disposições de privacidade dos pacientes, tal como estabelecido no HStan-03-2006-priv.

![[engs-req-nf.png]]
#### Requisitos Voláteis
Durante o processo de levantamento e análise, alguns requisitos podem mudar ou surgir devido a diversos fatores, como o aumento do entendimento sobre o sistema por parte dos stakeholders, mudanças no mercado ou na legislação.
- Requisitos mutáveis: Requisitos que se modificam por causa do ambiente do sistema.
-  Requisitos emergentes: Requisitos que surgem à medida que a compreensão do cliente do sistema se desenvolve
-  Requisitos consequentes: Requisitos que resultam da introdução do sistema de computador.
- Requisitos de compatibilidade: Requisitos que dependem de outros sistemas ou processos de negócio específicos dentro da organização.
#### Estrutura de um Documento de Requisitos
![[engs-req-dr.png]]
#### Processos 
Podem incluir quatro atividades de alto nível:
##### Estudo de Viabilidade 
Elas visam avaliar se o sistema é útil para a empresa.
##### Elicitação e Análise
Visam descobrir requisitos. A elicitação e análise de requisitos podem envolver diversos tipos de pessoas em uma organização para obter informações sobre o domínio da aplicação, os serviços que o sistema deve oferecer, o desempenho do sistema, restrições de hardware e assim por diante.
1. Descoberta de requisitos do sistema.
2. Classificação, agrupação e organização de requisitos.
3. Priorização e negociação de requisitos.
4. Especificação de requisitos. 

![[engs-req-ela.png]]
 
 ## Modelo Espiral
 Modelo de processo de software evolucionário que acopla a natureza iterativa da prototipação com os aspectos sistemáticos e controlados do modelo cascata. Fornece potencial para o rápido desenvolvimento de versões cada vez mais completas do software. é um gerador de modelos de processos dirigidos a riscos e é utilizado para guiar a engenharia de sistemas intensivos de software, que ocorre de forma concorrente e tem múltiplos envolvidos.
##### Especificação
Converte os requisitos em alguma forma-padrão de documentação das funcionalidades e restrições do software. Este processo é essencial para dar direção ao desenvolvimento e garantir que o produto final atenda às expectativas.
##### Validação
Verificar se os requisitos realmente definem o sistema que o cliente quer. Ela se sobrepõe à análise, uma vez que está preocupada em encontrar problemas com os requisitos. A validação de requisitos é importante porque erros em um documento de requisitos podem gerar altos custos de retrabalho quando descobertos durante o desenvolvimento ou após o sistema já estar em serviço.
#### Técnicas para o Levantamento de Requisitos
##### Questionário
Adequada para situações onde os usuários estão dispersos geograficamente ou quando se busca obter dados quantificáveis de um grande número de pessoas. Essa abordagem é eficiente em coletar informações de forma estruturada, permitindo análises estatísticas e uma compreensão abrangente das necessidades dos usuários.
##### Etnografia 
Técnica de observação que pode ser utilizada para compreender os requisitos sociais e organizacionais, ou seja, entender a política organizacional bem como a cultura de trabalho com objetivo de familiarizar-se com o sistema e sua história. O analista se insere no ambiente de trabalho em que o sistema será utilizado. O trabalho diário é observado e são anotadas as tarefas reais em que o sistema será utilizado. O principal objetivo da etnografia é que ela ajuda a descobrir requisitos de sistema implícitos, que refletem os processos reais, em vez de os processos formais, onde as pessoas estão envolvidas.
##### Prototipagem 
Tem por objetivo explorar aspectos críticos dos requisitos de um produto, implementando de forma rápida um pequeno subconjunto de funcionalidades deste produto. O protótipo é indicado para estudar as alternativas de interface do usuário; problemas de comunicação com outros produtos; e a viabilidade de atendimento dos requisitos de desempenho.
##### Entrevistas
Convém que o entrevistador dê margem ao entrevistado para expor as suas ideias. É necessário ter um plano de entrevista para que não haja dispersão do assunto principal e a entrevista fique longa, deixando o entrevistado cansado e não produzindo bons resultados.

- Requer interação direta e pode ser custosa em termos de tempo e recursos se os entrevistados estiverem em locais distintos.
# Experiência do Usuário (UX)
A experiência do usuário é fundamental para a acessibilidade e compreensão de uso do software. Isso significa levar em conta todas as ações e expectativas razoáveis do usuário durante cada passo do processo de desenvolvimento.  Para facilitar o gerenciamento da tarefa de elaborar uma experiência do usuário positiva, Garrett sugere dividi-la em seus elementos de componentes: estratégia, escopo, estrutura, esqueleto e superfície.

![[engs-ux-comp.png]]

- **Estratégia** - Identifica as necessidades do usuário e os objetivos de negócio. (é a base do UX)
- **Escopo** -  Inclui os requisitos funcionais e de conteúdo (ex., informações, mídias, serviços)
- **Estrutura** - Consiste no projeto de interação (como o sistema reage em resposta às ações dos usuários)
- **Esqueleto** -  Composto por três componentes: projeto informacional (ex., apresentação do conteúdo de forma a torná-lo compreensível para o usuário), projeto de interface (ex., organizar os objetos na tela da interface para que o usuário consiga trabalhar com a funcionalidade do sistema) e projeto de navegação (ex., o conjunto de elementos da tela que permite que os usuários se localizem na arquitetura da informação).
- **Superfície** - Apresenta o projeto visual ou a aparência do projeto acabado para os seus usuários.
#### Processo de Projeto
O projeto de interfaces do usuário começa com a identificação dos requisitos do usuário, de tarefas e dos ambientes. Uma vez que as tarefas de usuário tenham sido identificadas, cenários de usuário (casos de uso) são criados e analisados para definir um conjunto de ações e objetos de interface. Informações contidas no modelo de requisitos formam a base para a criação de um layout de tela que representa o design gráfico e o posicionamento de ícones, a definição de texto de tela descritivo, a especificação e a colocação de títulos para as janelas, bem como a especificação de itens de menu principais e secundários. Então, são usadas ferramentas para prototipação e, por fim, a implementação do modelo de projeto para interface.

![[engs-ux-ciclo.png]]

Três importantes princípios orientam o projeto de interfaces do usuário eficazes: 
1. Deixar o usuário no comando; 
2. Reduzir a carga de memória do usuário; 
3. Tornar a interface consistente. Para obter uma interface que observe esses princípios, deve ser realizado um processo de projeto organizado.
##### Interface
A interface do usuário é a janela para o software. Em muitos casos, ela molda a percepção do usuário quanto à qualidade de um sistema. Se a “janela” estiver embaçada, ondulada ou quebrada, o usuário poderá rejeitar um sistema computacional que, de outra forma, seria considerado poderoso. Por esse motivo, o desenvolvimento de uma interface do usuário começa com uma série de tarefas de análise:

 ## Análise dos usuários 
 Define personas para os perfis de vários usuários e é reunida com base em uma série de fontes técnicas e comerciais. (A análise do usuário permite que os desenvolvedores criem um mapa da jornada do cliente que serve de representação visual dos objetivos do artefato) 
 ## Análise de tarefas
 Define as tarefas e ações de usuários usando uma abordagem de refinamento ou orientada a objetos, aplicando casos de uso, elaboração de tarefa e objetos, análise de fluxos de trabalho e representações hierárquicas de tarefas para entender completamente a interação homem-computador. 
 ## Análise do ambiente 
 Identifica as estruturas físicas e sociais em que a interface deve operar.
 ## Análise dos cenários de uso
 São criados objetos e ações de interface que fornecem uma base para a criação de um layout de tela que represente o design gráfico e o posicionamento de ícones, a definição de texto de tela descritivo, a especificação e a colocação de títulos para as janelas, bem como a especificação de itens de menu principais e secundários. 

Pode ser criado um storyboard para ilustrar a navegação pelas telas desenvolvidas para o produto de modo a realizar tarefas específicas. Questões de projeto, como tempo de resposta, estrutura de comandos e ações, tratamento de erros e recursos de ajuda, são consideradas à medida que o modelo de projeto é refinado. Uma grande variedade de ferramentas de implementação é usada para construir um protótipo para avaliação por parte do usuário.
