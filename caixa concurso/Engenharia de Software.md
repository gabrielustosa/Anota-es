# Análise e Projeto Orientados a Objetos
A perspectiva empregada na análise é de _objetos_ (coisas, conceitos ou entidades). Durante a Análise OO, a ênfase está em achar e descrever objetos (ou conceitos) no domínio do problema. Por exemplo, num sistema de informação para uma biblioteca, alguns dos conceitos são _Livro_, _Biblioteca_, _Usuário_. Tais objetos podem ter atributos e responsabilidades. Durante o projeto orientado a objeto, a ênfase está em achar objetos lógicos de software que poderão ser eventualmente implementados usando uma linguagem de programação OO. Tais objetos podem ter atributos e métodos. Durante a construção (programação OO), os objetos do projeto são implementados e testados.

O foco é entender o domínio do problema e modelar esse entendimento em termos de objetos. Esses objetos devem refletir as entidades reais do domínio e suas interações, bem como o desenvolvimento de um modelo orientado a objetos do domínio da aplicação. 

Um projetista não começa pela identificação das diferentes funcionalidades dos sistemas. Uma motivação para essa abordagem é que mudanças na especificação dos requisitos tendem a afetar menos os objetos do que as funções.

Processos de projeto orientado a objetos envolvem projetar as classes de objetos e os relacionamentos entre essas classes. Essas classes definem os objetos no sistema e suas interações. Quando o projeto é concebido como um programa em execução, os objetos são criados dinamicamente a partir dessas definições de classe.

```ad-tip
Como um todo, se preocupa com o que terá de ser realizado.

**Análise**: Focada na identificação e domínio do problema ou negócio.
**Projeto**: Criação de um modelo OO para satisfazer os requisitos.
```

São abordagens de análise orientada a objeto:

1. RUP - [[Engenharia de Software#Processo Unificado|Processo Unificado]]
2. OMT (Object Modeling Technique), técnica antecessora do UML.
# Processo Unificado 
Um conjunto de atividades executadas para transformar um conjunto de requisitos do cliente em um sistema de software. Promove o uso de melhores práticas, como desenvolvimento orientado a casos de uso, arquitetura baseada em componentes, controle de versões, e a integração contínua. 

- Estrutura a arquitetura do sistema em componentes, permitindo assim uma melhor modularidade e reutilização.
- Utiliza toda uma definição em UML.
- Dirigido por casos de usos
- Centrado na arquitetura, Interativo e incremental
- Tem foco em riscos

É geralmente descrito sobre três perspectivas:

1. Uma perspectiva dinâmica, representado pelas fases, que mostra as fases do modelo ao longo do tempo.
2. Uma perspectiva estática, representados pelas disciplinas, que mostra as atividades realizadas no processo.
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
É decomposto ao longo do tempo em quatro fases sequenciais, cada uma concluída por um marco importante; cada fase é essencialmente um período de tempo entre dois marcos principais. Ao final de cada fase, é realizada uma avaliação para determinar se os objetivos da fase foram cumpridos. Uma avaliação satisfatória permite que o projeto passe para a próxima fase. As 4 quatro fases sequenciais são: **Concepção (Inception), Elaboração (Elaboration),  Construção (Construction) e Transição (Transition)**. 

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
 Implica transferência do sistema da comunidade de desenvolvimento para a comunidade de usuários e em seu funcionamento em um ambiente real. Tipicamente, essa fase inclui várias iterações, incluindo versões beta, versões de disponibilidade geral, além de correções de erros e lançamentos de aprimoramento. Isso é ignorado na maioria dos modelos de processo de software, mas é, de fato, uma atividade cara e, às vezes, problemática. Na conclusão dessa fase, você deve ter um sistema de software documentado e funcionando corretamente em seu ambiente operacional.
 
 ## MARCOS
- Fase Iniciação: Identificar escopo ou objetivo do ciclo de vida
- Fase Elaboração: Arquitetura, equipe e projeto estabilizado de acordo com o ciclo de vida
- Fase Construção: Capacidade operacional inicial
- Fase Transição: Lançamento (Release) do produto.
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
```
 
 ## Disciplina
 Descreve as sequências das atividades e as iterações com que participa, sendo realizadas a qualquer momento do ciclo.
 ![[engs-pu-disc.png]]
```ad-tip
#### Disciplinas mais utilizada em cada fase
**Concepção**: Requisitos, Modelagem de Negócios;
**Elaboração**: Análise e Design, Requisitos;
**Construção**: Implementação, Testes;
**Transição**: Inplantação, Gerência de Configuração e Mudância;
```

1. **Modelagem de Negócios**:
    - A TI precisa entender o funcionamento do negócio, e o cliente deve compreender como a TI pode contribuir para melhor suportar os negócios.
    - A comunicação entre engenheiros de software, desenvolvedores, clientes e usuários deve ser definida e aprimorada.
    - A modelagem de negócios permite descrever como a visão da organização pode ser usada como base para descrever o processo, os papéis e responsabilidades no projeto.
2. **Requisitos**:
    - Explica como transformar as necessidades das partes interessadas em requisitos específicos que serão usados para criar o sistema.
3. **Análise e Projeto (Design)**:
    - Visa criar uma abstração do sistema.
    - Define classes, pacotes e subsistemas com interfaces bem definidas.
    - Descreve como cada objeto das classes irá colaborar para viabilizar os casos de uso do sistema.
4. **Implementação**:
    - Presente principalmente na fase de construção.
    - Consiste na organização e criação do código, binários, executáveis, componentes e testes de unidade.
    - Também descreve como reutilizar componentes.
5. **Teste**:
    - Mais importante ao fim da fase de construção e início da fase de transição.
    - São feitos testes de integração para verificar se os requisitos foram corretamente implementados.
    - O objetivo é garantir que os defeitos sejam tratados antes da implantação do software.
6. **Implantação**:
    - Envolve a entrega do software ao usuário final.
    - Inclui atividades como criação de releases, embalagem, distribuição, instalação e suporte aos usuários.
7. **Gerenciamento de Configuração e Mudança**:
    - Trata do controle de versão e dependências de artefatos, como documentos e modelos.
    - Gerencia as solicitações de mudanças para esses artefatos, classificando-as em vários estados, listando as causas raiz, a natureza (defeito ou melhoria), prioridade, etc.
    - Pode utilizar sistemas de controle de versão e de gerenciamento de ciclo de vida (ALM – Application Life Cycle Management) para viabilizar e facilitar a execução da disciplina.
8. **Ambiente**:
    - Relacionado à disponibilização de ferramentas apropriadas de software para a equipe de desenvolvimento.
9. **Gerenciamento de Projeto**:
    - Planeja o projeto em dois níveis de detalhamento.
    - Descreve as iterações e os processos de acompanhamento e métricas dessas iterações .
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
#### Diagramas de Classe
Um diagrama de classe fornece uma visão estática ou estrutural do sistema. Ele não mostra a natureza dinâmica das comunicações entre os objetos das classes no diagrama. A visibilidade é indicada pelos sinais –, #, ~ ou +, que indicam, respectivamente, visibilidade ``private``, ``protected``, ``package`` ou ``public``.  Atributos estáticos podem ser referenciados sendo sublinhados. 

```ad-tip
###### ~ (package)
Pode ser acessado pela própria classe ou por qualquer classe que pertença ao mesmo pacote. 
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
 
 ```ad-tip
 ##### Navegabilidade 
 Representada por uma seta em um dos fins da associação, determina o sentido em que os métodos poderão ser disparados.
 - É opcional (caso não exista, singificará que as informações podem transitar bilateralmente entre as classes.)
```
 
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
 
 ## Classe Associativa
 São necessárias nos casos em que existem atributos relacionados à associação que não podem ser armazenados por nenhuma das classes envolvidas. Costumam ser utilizadas principalmente em associações que apresentem multiplicidade muitos (\*) em todas as suas extremidades.
 ![[engs-uml-clsassoc.png]]
 ## Associação Qualificada 
 Quando existe um atributo único em uma classe, é possível criar uma associação qualificada, que é uma forma de identificar individualmente um objeto dentro de uma coleção (uma coleção pode ser definida como um conjunto de instâncias associadas a outro objeto). O qualificador de uma associação é representado por um pequeno retângulo ligado ao final da associação.
 ![[engs-uml-assq.png]]
 ## Associação Unária
 Este tipo de associação ocorre quando existe um relacionamento de um objeto de uma classe com objetos da mesma classe. No exemplo, funcionário pode ou não chefiar vários funcionários.
 ![[engs-uml-dcasu.png]]
##### Restrições OCL
Essa linguagem procura fornecer um maior formalismo na declaração de restrições, procurando, assim, evitar a ambiguidade em suas representações. Por exemplo, que em uma classe `PessoaFisica` queiramos deixar explícito que nenhum objeto dessa classe poderá conter um valor inferior a 18 em seu atributo idade. Em OCL, poderíamos representar isso da seguinte maneira:

![[engs-uml-dcrestr.png]]

Há, ainda, outros tipos de restrições que podem ser aplicados a atributos. Por exemplo, pode-se definir um atributo como {readOnly} (somente leitura), determinando que seu valor só pode ser lido e não modificado.

![[engs-uml-dcrestrro.png]]
 
 Também é possível determinar que um atributo é estático (Static). Um atributo estático é apresentado sublinhado.
 
![[engs-uml-dcrestrst.png]]

As restrições podem ainda ser utilizadas para definir melhor a semântica de classes especializadas derivadas de classes gerais. As restrições predefinidas para classes especializadas são:

• **Completa (complete)** – Quando todas as subclasses possíveis foram derivadas da classe geral.
• **Incompleta (incomplete)** – Quando ainda é possível derivar novas subclasses.
• **Separada (disjoint)** – Quando as subclasses são mutuamente exclusivas, ou seja, no momento em que uma instância pertence a uma subclasse, não poderá de forma alguma pertencer a nenhuma das outras subclasses derivadas.

A figura abaixo fornece um exemplo de classes especializadas separadas e completas.

![[engs-uml-dcrestrme.png]]

Nesse exemplo, foram derivadas duas subclasses a partir da classe Pessoa, as classes Física e Jurídica. Dentro do escopo em que estão inseridas, não existem mais classes que possam ser derivadas da classe Pessoa, por isso a restrição entre as classes generalizadas é completa. Além disso, no momento em que uma pessoa for física, não poderá ser jurídica, e vice-versa. Portanto, a especialização também é separada (disjoint).

• Sobreposta (overlapping) – Quando o fato de pertencer a uma subclasse não impede que pertença a outras.

A figura apresenta um exemplo, no qual, a partir da classe Veiculo, derivaram-se duas subclasses Aéreo e Aquático. Como poderiamos ainda derivar uma classe para veículos terrestres, colocou-se uma restrição incompleta e, como pode ocorrer de um veículo ser tanto aéreo quanto aquático, como é o caso do hidroavião, acrescentamos, ainda, a restrição de sobreposta (overlapping) à especialização. Como é possível perceber, as restrições podem ser combinadas, sendo separadas por vírgulas.

![[engs-uml-dcrestrme2.png]]
#### Diagrama de Objeto
O diagrama de objetos tem como objetivo fornecer uma “visão” dos valores armazenados pelos objetos das classes, definidas no diagrama de classes, em um determinado momento do sistema. Assim, embora o diagrama de classes seja estático, podem ser criados diagramas de objetos, onde as possíveis situações pelas quais os objetos das classes passarão podem ser simuladas.

![[engs-uml-do.png]]
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
###### Casos de Uso
Os casos de uso são utilizados para capturar os requisitos funcionais do sistema, ou seja, referem-se a serviços, tarefas ou funcionalidades identificados como necessários ao software e que podem ser utilizados de alguma maneira pelos atores que interagem com o sistema.
- **Caso Primario**: Quando se refere a um processo importante, que enfoca um dos requisitos funcionais do software, como realizar um saque ou emitir um extrato em um sistema de controle bancário.
- **Caso Secundário**: Refere a um processo periférico, como a manutenção de um cadastro ou a emissão de um relatório simples.
```
#### Diagramas de Sequência
Ao contrário dos diagramas de classe e de implantação, que mostram a estrutura estática de um componente de software, o diagrama de sequência é utilizado para indicar as comunicações dinâmicas entre objetos durante a execução de uma tarefa (caso de uso). Ele mostra a ordem temporal na qual as mensagens são enviadas entre os objetos para executar aquela tarefa. Podemos usar um diagrama de sequência para mostrar as interações em um caso de uso ou em um cenário do sistema de software. Obviamente, o diagrama de sequência depende também do diagrama de classes, uma vez que as classes dos objetos utilizados no diagrama de sequência estão descritas nele. No entanto, o diagrama de sequência é uma excelente forma de validar e complementar o diagrama de classes, pois é ao modelar um diagrama de sequência que se percebe quais métodos são necessários declarar em que classes.

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
Este diagrama está amplamente associado ao diagrama de sequência: na verdade, um complementa o outro. As informações mostradas no diagrama de comunicação são, com frequência, praticamente as mesmas apresentadas no diagrama de sequência, porém com um enfoque diferente, visto que esse diagrama não se preocupa com a temporalidade do processo, concentrando-se em como os elementos do diagrama estão vinculados e quais mensagens trocam entre si durante um processo.

![[engs-uml-dco.png]]
#### Diagrama de Atividade
O diagrama de atividade mostra o comportamento dinâmico de um sistema ou de parte de um sistema por meio do fluxo de controle entre ações que o sistema executa. Ele é similar a um fluxograma, exceto que pode mostrar fluxos concorrentes. O componente principal de um diagrama de atividade é um nó de ação, representado por um retângulo arredondado, que corresponde a uma tarefa executada por um sistema de software. Setas que vão de um nó ação para outro indicam o fluxo de controle. Isto é, uma seta entre dois nós ação significa que, depois que a primeira ação é completada, a segunda ação começa. A escolha do diagrama de atividades é apropriada quando se destina a capturar o fluxo de tarefas entre múltiplos participantes.

![[imgs/engenharia de software/engs-uml-da.png]]
##### Símbolos 
![[engs-uml-da-s.png]]

 ## Join Node
 Combina fluxos concorrentes em um único fluxo. Quando cada fluxo de entrada possui um token aguardando, um token é produzido na saída.
![[engs-uml-da-join.png]] 

 ## Fork Node 
 Divide um único fluxo em fluxos concorrentes. Cada token de entrada produz um token em cada conector de saída.
 
![[engs-uml-da-fork.png]]
#### Diagrama de Estado
Utilizado para modelar o comportamento de um objeto ao longo do tempo, incluindo seus diferentes estados e as transições que ocorrem em resposta a eventos específicos. São muito usados para modelar o comportamento de Interfaces, Casos de Uso, Instâncias de classes. Um diagrama de máquina de estados deve seguir a regra de que existe **apenas um estado inicial**. Esse é o ponto de partida para que a máquina comece sua execução. A partir daí, a máquina pode transitar por vários estados conforme sua especificação e reagir a diferentes eventos, até eventualmente chegar a um número não especificado de estados finais.

![[engs-uml-de.png]]
#### Diagrama de Componentes
Representa a organização e a dependência entre os componentes físicos do sistema, como bibliotecas, módulos ou pacotes.

![[engs-uml-dcom.png]]
#### Diagrama de Pacotes
Diagrama estrutural que mostra como elementos de um sistema são organizados em pacotes, bem como as dependências entre esses pacotes. Eles são úteis para organizar e estruturar um sistema em elementos de mais alto nível, facilitando o gerenciamento de complexidade do sistema.

![[engs-uml-dp.png]]
#### Diagrama de Perfil
permite definir tipos padronizados de estereótipos, valores rotulados e restrições. A UML define o mecanismo de perfils como um
"mecanismo leve de extensão" da linguagem. Permite adaptar os modelos UML para diferentes plataformas e domínios.
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
- Diagrama de Comunicação
# Engenharia de Requisitos
Os requisitos de um sistema são as descrições do que o sistema deve fazer, os serviços que oferece e as restrições a seu funcionamento. Este, é o processo de descobrir, analisar, documentar e verificar esses serviços e restrições. Idealmente, eles devem especificar somente o comportamento externo do sistema. A elaboração de requisitos é norteada pela criação e pelo refinamento de cenários que descrevem como o usuário e outros atores interagirão com o sistema. Cada cenário de usuário é analisado a fim de extrair classes de análise, ou seja, entidades do domínio de negócio visíveis para o usuário. O documento de requisitos não deve incluir detalhes da arquitetura ou projeto do sistema.  Eles podem ser usados como parte do contrato para a implementação do sistema e devem consistir em uma especificação completa e detalhada de todo o sistema.

```ad-tip
##### Modelo Conceitual
É uma representação abstrata das entidades, conceitos e relações importantes em um determinado domínio de aplicação. Ele descreve os conceitos fundamentais que são relevantes para o sistema que está sendo desenvolvido, independentemente de como o sistema será implementado.

- É definido no processo de elicitação de requisitos.
```

```ad-info
##### Tipos de requisitos
- **Normais**: objetivos declarados
- **Esperados**: implícitos e podem ser tão básicos que o cliente não declara explicitamente
- **Extraordinários**: vão além das expectativas do usuários
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

```ad-summary
#### Matriz de rastreabilidade de requisitos
É uma ferramenta que explicita a relação direta dos requisitos entre si ou com os outros componentes do projeto. Assim, caso alguma alteração seja feita no projeto, sabe-se quais requisitos serão afetados com tal mudança.
```
#### Requisitos Não Funcionais (como deve ser feito)
São restrições aos serviços ou funções oferecidos pelo sistema. Incluem restrições de timing, restrições no processo de desenvolvimento, propriedades emergentes e restrições impostas pelas normas. Ao contrário das características individuais ou serviços do sistema, os requisitos não funcionais, muitas vezes, aplicam-se ao sistema como um todo.

- Eles podem estar relacionados às propriedades emergentes do sistema, como confiabilidade, tempo de resposta e ocupação de área.
- Um único requisito não funcional, tal como um requisito de proteção, pode gerar uma série de requisitos funcionais relacionados
-  São frequentemente mais críticos que requisitos funcionais individuais. 
- Como exemplo, a **interoperabilidade**, que é a capacidade do sistema de se comunicar e operar com outros sistemas, é um exemplo de requisito não funcional.
- Sempre que possível, os requisitos não funcionais devem ser escritos quantitativamente, para que possam ser objetivamente testados. 
##### Requisitos de Produto (Software)
Esses requisitos especificam ou restringem o comportamento do software . É um requisito de disponibilidade que define quando o sistema deve estar disponível e o tempo diário permitido de seu não funcionamento. Exemplos incluem os requisitos de desempenho quanto à rapidez com que o sistema deve executar e quanta memória ele requer, os requisitos de confiabilidade que estabelecem a taxa aceitável de falhas, os requisitos de proteção e os requisitos de usabilidade.
 ## Exemplo Real
 O MHC-PMS deve estar disponível para todas as clínicas durante as horas normais de trabalho (segunda a sexta-feira, 8h30 às 17h30). Períodos de não operação dentro do horário normal de trabalho não podem exceder cinco segundos em um dia.
##### Requisitos Organizacionais (Políticas)
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
 
```ad-summary
#####  SMART
 O método SMART é um acrônimo que serve de guia para definir objetivos de maneira eficaz. 
- **S** – Específico: O objetivo ou requisito deve ser claro e preciso.
- **M** – Mensurável: Deve ser possível mensurar o progresso e o sucesso.
- **A** – Alcançável: Deve ser realista e atingível.
- **R** – Relevante: Deve ser relevante para a organização, alinhado com suas metas.
- **T** – Temporal: Deve ter um prazo definido.
```
##### Elicitação e Análise
Visam descobrir requisitos. A elicitação e análise de requisitos podem envolver diversos tipos de pessoas em uma organização para obter informações sobre o domínio da aplicação, os serviços que o sistema deve oferecer, o desempenho do sistema, restrições de hardware e assim por diante.
1. Descoberta de requisitos do sistema.
2. Classificação, agrupação e organização de requisitos.
3. Priorização e negociação de requisitos.
4. Especificação de requisitos. 

![[engs-req-ela.png]]

```ad-summary
###### Modelo Espiral
Modelo de processo de software evolucionário que acopla a natureza iterativa da prototipação com os aspectos sistemáticos e controlados do modelo cascata. Fornece potencial para o rápido desenvolvimento de versões cada vez mais completas do software. é um gerador de modelos de processos dirigidos a riscos e é utilizado para guiar a engenharia de sistemas intensivos de software, que ocorre de forma concorrente e tem múltiplos envolvidos.
```

```ad-tip
#### Levantamento vs Elaboração
 - **Levantamento**: Primeira fase do processo de engenharia de requisitos. Seu objetivo é identificar, coletar e documentar os requisitos do sistema.
 - **Elaboração**: Ocorre após o levantamento de requisitos. Seu objetivo é transformar os requisitos de alto nível coletados durante o levantamento em requisitos mais detalhados e compreensíveis.
```
##### Especificação
Converte os requisitos em alguma forma-padrão de documentação das funcionalidades e restrições do software. Este processo é essencial para dar direção ao desenvolvimento e garantir que o produto final atenda às expectativas.
##### Validação
Verificar se os requisitos realmente definem o sistema que o cliente quer. Ela se sobrepõe à análise, uma vez que está preocupada em encontrar problemas com os requisitos. A validação de requisitos é importante porque erros em um documento de requisitos podem gerar altos custos de retrabalho quando descobertos durante o desenvolvimento ou após o sistema já estar em serviço.

```ad-tip
#### Verificação vs Validação
  - **Verificação**: Processo que ocorre durante o desenvolvimento do software. Seu objetivo é garantir que o software está sendo construído corretamente, de acordo com as especificações dos requisitos.
  - **Validação**: A validação de requisitos ocorre após a construção do software, durante a fase de testes. Seu objetivo é garantir que o software atenda às necessidades reais do cliente e aos objetivos de negócio.
```
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
##### Workshops
Elicitação em grupo usada em uma reunião estruturada. Devem fazer parte do grupo uma equipe de analistas e uma seleção dos stakeholders que melhor representam a organização e o contexto em que o sistema será usado, obtendo assim um conjunto de requisitos bem definidos.
##### JAD
O JAD facilita a criação de uma visão compartilhada do que o produto de software deve ser. Através da sua utilização os desenvolvedores ajudam os usuários a formular problemas e explorar soluções. Dessa forma, os usuários ganham um sentimento de envolvimento, posse e responsabilidade com o sucesso do produto.
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
# Qualidade de Software
Qualidade de software trata sobre a maturidade dos processos de uma organização, visando a qualidade do produto gerado e a consequente satisfação dos seus clientes. É importante entender que a qualidade de um software não está restrita apenas a sua funcionalidade, mas também a como ele satisfaz requisitos tais como usabilidade, confiabilidade, eficiência, manutenibilidade e portabilidade, entre outros, o que pode incluir aspectos não explicitados formalmente, mas que são esperados pelo usuário.

```ad-info
##### Norma ISO/IEC 9126 
Características de qualidade de produto de Software.
- **Funcionalidade**: Adequação, Acurácia, Interoperabilidade, Segurança de acesso e Conformidade;
- **Confiabilidade**: Maturidade, Tolerância a falhas, Recuperabilidade e Conformidade;
- **Usabilidade**: Inteligibilidade, Apreensibilidade, Operacionalidade, Atratividade e Conformidade;
- **Eficiência**: Comportamento em relação ao tempo, Utilização de recursos e Conformidade;
- **Manutenibilidade**: Analisabilidade, Modificabilidade, Estabilidade e Conformidade;
- **Portabilidade**: Adaptabilidade, Capacidade para ser instalado, Coexistência, Capacidade para substituir e Conformidade.
```

```ad-warning
A maturidade determina o nível qualidade.
```
### CMMI
Em suma, O CMMI é um framework para medir maturidade dos processos de TI. Este procura nortear a organização no sentido de implementar a melhoria contínua do processo de software, e o faz através de um modelo que contempla duas representações, divididas em níveis, priorizando de forma lógica as ações a serem realizadas. Quanto maior o nível, maior a maturidade da organização, o que pode se traduzir em maior qualidade do produto final, com maior previsibilidade em cronogramas e orçamentos.

Essas duas representações possíveis são:
##### Representação Por Estágios (Abrangente)
Disponibiliza uma sequência pré-determinada para melhoria baseada em estágios que não deve ser desconsiderada, pois cada estágio serve de base para o próximo. É caracterizado por Níveis de Maturidade (_Maturity Levels_)
##### Representação Continua  (Incremental)
Possibilita a organização utilizar a ordem de melhoria que melhor atender os objetivos de negócio da empresa. É caracterizado por Níveis de Capacidade (_Capability Levels_)
#### Maturidade
Os níveis de maturidade do CMMI na representação contínua são os seguintes:

- Nível 0 - Incompleto: Os processos não estão implementados ou não alcançam os objetivos da área de processo.
- Nível 1 - Executado: Os processos estão implementados e atingem os objetivos.
- Nível 2 - Gerenciado: Os processos são planejados, executados, monitorados e controlados.
- Nível 3 - Definido: Os processos são bem caracterizados e entendidos e são descritos em padrões, procedimentos, ferramentas e métodos.
- Nível 4 - Gerenciado Quantitativamente: Os processos são controlados usando técnicas estatísticas e quantitativas.
- Nível 5 - Otimizado: O foco é na melhoria contínua dos processos através de inovação e otimização tecnológica.

![[engs-qs-cmmi-n.png]]

### MPS-BR
Define a capacidade de um processo por meio de resultados esperados e níveis de maturidade, refletindo como os processos estão institucionalizados na organização. A medida que a organização evolui, espera-se que a capacidade para desempenhar os processos melhore, conforme descrito na afirmativa. O MPS.BR é um modelo de referência que visa estabelecer um padrão para a maturidade dos processos de software, sendo amplamente adotado, especialmente no Brasil.
#### MR-MPS-SW
O Modelo de Referência MPS para Software (MR-MPS-SW) define níveis de maturidade que resultam de uma combinação entre processos e sua capacidade. 

A definição dos processos segue os requisitos para um modelo de referência de processo apresentados na ISO/IEC 15504-2, especificando o propósito e os resultados esperados de sua execução. Isso possibilita a avaliação e atribuição de graus de efetividade na execução dos processos. 

A capacidade do processo refere-se à habilidade do processo para atingir os objetivos de negócio atuais e futuros, e está relacionada ao cumprimento dos atributos de processo associados aos processos de cada nível de maturidade.
#### Níveis de Maturidade
O modelo MPS-BR define 7 níveis de maturidade cuja escala inicia-se no nível **G** e progride até o nível **A**. 

![[engs-qa-mps-br.png]]

- Na passagem para um nível de maturidade superior, os processos anteriormente implementados devem passar a ser executados no nível de capacidade exigido neste nível superior.

1. **G** – Parcialmente Gerenciado: somente gerenciamento de requisitos e projetos;
2. **F** – Gerenciado: Controles de mediação, gerência de configuração, conceitos de aquisição e garantia de qualidade;
3. **E** – Parcialmente Definido: processos como treinamento, adaptação de processos para gerência de projetos e melhoria e o controle do processo organizacional;
4. **D** – Largamente Definido: validação, verificação, liberação, instalação e integração;
5. **C** – Definido: Gerência de riscos;
6. **B** – Gerenciado Quantitativamente: Desempenho dos processos e sua gerência quantitativa;
7. **A** – Otimização: Inovação e análise de causas contínuas;

```ad-summary
#### Maturidade Inicial
- Caracterizado pela ausência de processos padronizados e repetitivos.
- Atividades são realizadas de maneira ad hoc, muitas vezes dependendo de esforços individuais.
- O foco está na resolução de problemas imediatos.
#### Maturidade Gerenciado
- Introduz práticas de gerenciamento de projetos para melhorar a previsibilidade.
- Processos começam a ser documentados e padronizados.
- Controle básico sobre os projetos é estabelecido.
#### Maturidade Definido
- Processos são completamente documentados, padronizados e integrados.
- Há um comprometimento com a melhoria contínua.
- Papéis e responsabilidades são bem definidos.
- Foco em estabelecer processos eficientes.
#### Maturidade Quantitativamente Gerenciado
- Introduz a medição quantitativa para entender e controlar o desempenho dos processos.
- Estabelece objetivos quantitativos para melhorar a qualidade e a eficiência.
- Tomada de decisão baseada em dados.
#### Maturidade em Otimização
- Foco na melhoria contínua e inovação.
- Processos são continuamente ajustados e otimizados.
- Inovações tecnológicas e melhores práticas são incorporadas.
- Organização busca a excelência e a adaptação às mudanças.
```
