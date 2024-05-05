# Padrões Criacionais
Fornecem mecanismos de criação de objetos que aumentam a flexibilidade e a reutilização de código.
### Factory Method 
Fornece uma interface para criar objetos em uma superclasse, mas permite que as subclasses alterem o tipo de objetos que serão criados. Separa o código de construção do produto do código que realmente usa o produto. Portanto, é mais fácil estender o código de construção do produto independentemente do restante do código.

![[pp-facm.png]]
### Abstract Method
Permite que você produza famílias de objetos relacionados sem ter que especificar suas classes concretas. A primeira coisa que o padrão Abstract Factory sugere é declarar explicitamente interfaces para cada produto distinto da família de produtos (ex: cadeira, sofá ou mesa de centro). Então você pode fazer todas as variantes dos produtos seguirem essas interfaces.

![[pp-absm.png]]
### Builder
Constrói objetos complexos passo a passo. O padrão permite que você produza diferentes tipos e representações de um objeto usando o mesmo código de construção. O padrão Builder sugere que você extraia o código de construção do objeto para fora de sua própria classe e mova ele para objetos separados chamados builders.

![[pp-builder.png]]

### Prototype 
Permite copiar objetos existentes sem fazer seu código ficar dependente de suas classes. O padrão Prototype delega o processo de clonagem para o próprio objeto que está sendo clonado. O padrão declara um interface comum para todos os objetos que suportam clonagem. Geralmente, tal interface contém apenas um único método `clonar`. Esse método cria um objeto da classe atual e carrega todos os valores de campo para do antigo objeto para o novo.

![[pp-prot.png]]
### Singleton
Permite a você garantir que uma classe tenha apenas uma instância, enquanto provê um ponto de acesso global para essa instância. Criar um método estático de criação que age como um construtor. Esse método chama o construtor privado por debaixo dos panos para criar um objeto e o salva em um campo estático. Todas as chamadas seguintes para esse método retornam o objeto em cache.

![[pp-singl.png]]
# Padrões Estruturais
Explicam como montar objetos e classes em estruturas maiores, enquanto ainda mantém as estruturas flexíveis e eficientes.
### Adapter 
Permite objetos com interfaces incompatíveis colaborarem entre si. Ele é um objeto especial que converte a interface de um objeto para que outro objeto possa entendê-lo. Um adaptador encobre um dos objetos para esconder a complexidade da conversão acontecendo nos bastidores. O objeto encobrido nem fica ciente do adaptador.

![[pp-adpt.png]]
### Bridge
Permite que você divida uma classe grande ou um conjunto de classes intimamente ligadas em duas hierarquias separadas, abstração e implementação, que podem ser desenvolvidas independentemente umas das outras. 
- Abstração: a camada GUI da aplicação 
- Implementação: As APIs do sistema operacional.

![[pp-bridge.png]]
### Composite 
Permite que você componha objetos em estruturas de árvores e então trabalhe com essas estruturas como se elas fossem objetos individuais. Usar o padrão Composite faz sentido apenas quando o modelo central de sua aplicação pode ser representada como uma árvore. Por exemplo, imagine que você tem dois tipos de objetos: `Produtos` e `Caixas`. Uma `Caixa` pode conter diversos `Produtos` bem como um número de `Caixas` menores. Essas `Caixas` menores também podem ter alguns `Produtos` ou até mesmo `Caixas` menores que elas, e assim em diante. O padrão Composite sugere que você trabalhe com `Produtos` e `Caixas` através de uma interface comum que declara um método para a contagem do preço total.

![[pp-compos.png]]
### Decorator 
Permite que você acople novos comportamentos para objetos ao colocá-los dentro de invólucros de objetos que contém os comportamentos. Acrescentando ou removendo responsabilidades a objetos individuais dinamicamente

![[pp-deco.png]]
### Facade
fornece uma interface simplificada para uma biblioteca, um framework, ou qualquer conjunto complexo de classes. Neste exemplo, o padrão **Facade** simplifica a interação com um framework complexo de conversão de vídeo.

![[pp-facade.png]]
### Flyweight
Permite a você colocar mais objetos na quantidade de RAM disponível ao compartilhar partes comuns de estado entre os múltiplos objetos ao invés de manter todos os dados em cada objeto. O padrão Flyweight sugere que você pare de armazenar o estado extrínseco dentro do objeto. Ao invés disso, você deve passar esse estado para métodos específicos que dependem dele. Somente o estado intrínseco fica dentro do objeto, permitindo que você o reutilize em diferentes contextos. Como resultado, você vai precisar de menos desses objetos uma vez que eles diferem apenas em seu estado intrínseco, que tem menos variações que o extrínseco.

![[pp-flyweight.png]]
### Proxy
Permite que você forneça um substituto (surrogate) ou um espaço reservado para outro objeto. Um proxy controla o acesso ao objeto original, permitindo que você faça algo ou antes ou depois do pedido chegar ao objeto original. O padrão Proxy sugere que você crie uma nova classe proxy com a mesma interface do objeto do serviço original. Então você atualiza sua aplicação para que ela passe o objeto proxy para todos os clientes do objeto original. Ao receber uma solicitação de um cliente, o proxy cria um objeto do serviço real e delega a ele todo o trabalho. Se você precisa executar alguma coisa tanto antes como depois da lógica primária da classe, o proxy permite que você faça isso sem mudar aquela classe. Uma vez que o proxy implementa a mesma interface que a classe original, ele pode ser passado para qualquer cliente que espera um objeto do serviço real.

![[pp-proxy.png]]
### Gateway
Visa facilitar a interação e comunicação entre um sistema principal e sistemas externos, como bibliotecas, serviços remotos, bancos de dados ou arquivos. Ele atua como um ponto central para lidar com a complexidade desses sistemas externos, oferecendo uma interface mais familiar e conveniente para o sistema principal.

![[pp-gat.png]]
# Padrões Comportamentais
Cuidam da comunicação eficiente e da assinalação de responsabilidades entre objetos.
### Chain of Responsability 
Permite que você passe pedidos por uma corrente de handlers. Ao receber um pedido, cada handler decide se processa o pedido ou o passa adiante para o próximo handler na corrente. O **Chain of Responsibility** se baseia em transformar certos comportamentos em objetos solitários chamados handlers. O padrão sugere que você ligue esses handlers em uma corrente. Cada handler ligado tem um campo para armazenar uma referência ao próximo handler da corrente. Além de processar o pedido, handlers o passam adiante na corrente.

![[pp-chain.png]]
### Command
Transforma um pedido em um objeto independente que contém toda a informação sobre o pedido. Essa transformação permite que você parametrizem diferentes requisições, filas ou requisições de log, suportar operações reversíveis, atrasar ou colocar a execução do pedido em uma fila, e suporte operações que não podem ser feitas. O padrão Command sugere que os objetos GUI não enviem esses pedidos diretamente. Ao invés disso, você deve extrair todos os detalhes do pedido, tais como o objeto a ser chamado, o nome do método, e a lista de argumentos em uma classe comando separada que tem apenas um método que aciona esse pedido.
![[pp-cmd.png]]
### Iterator
Permite a você percorrer elementos de uma coleção sem expor as representações dele (lista, pilha, árvore, etc.). A ideia principal do padrão Iterator é extrair o comportamento de travessia de uma coleção para um objeto separado chamado um iterador. 

![[pp-iterator.png]]
### Mediator
Permite que você reduza as dependências caóticas entre objetos. O padrão restringe comunicações diretas entre objetos e os força a colaborar apenas através do objeto mediador, reduzindo o acoplamento entre elas. O padrão Mediator sugere que você deveria cessar toda comunicação direta entre componentes que você quer tornar independentes um do outro. Ao invés disso, esses componentes devem colaborar indiretamente, chamando um objeto mediador especial que redireciona as chamadas para os componentes apropriados. Como resultado, os componentes dependem apenas de uma única classe mediadora ao invés de serem acoplados a dúzias de outros colegas.

![[pp-mediator.png]]
### Memento
Permite que você salve e restaure o estado anterior de um objeto sem revelar os detalhes de sua implementação. O padrão Memento delega a criação dos retratos do estado para o próprio dono do estado, o objeto originador. Portanto, ao invés de outros objetos tentarem copiar o estado do editor “a partir do lado de fora”, a própria classe do editor pode fazer o retrato já que tem acesso total a seu próprio estado. O padrão sugere armazenar a cópia do estado de um objeto em um objeto especial chamado _memento_. Os conteúdos de um memento não são acessíveis para qualquer outro objeto exceto aquele que o produziu. Outros objetos podem se comunicar com mementos usando uma interface limitada que pode permitir a recuperação dos metadados do retrato (data de criação, nome a operação efetuada, etc.), mas não ao estado do objeto original contido no retrato.
 
![[pp-meme.png]]
### Observer
Permite que você defina um mecanismo de assinatura para notificar múltiplos objetos sobre quaisquer eventos que aconteçam com o objeto que eles estão observando. O padrão Observer sugere que você adicione um mecanismo de assinatura para a classe publicadora para que objetos individuais possam assinar ou desassinar uma corrente de eventos vindo daquela publicadora. Esse mecanismo consiste em 1) um vetor para armazenar uma lista de referências aos objetos do assinante e 2) alguns métodos públicos que permitem adicionar assinantes e removê-los da lista.

![[pp-obs.png]]
### State
Permite que um objeto altere seu comportamento quando seu estado interno muda. O padrão State é intimamente relacionado com o conceito de uma Máquina de Estado Finito. A ideia principal é que, em qualquer dado momento, há um número finito de estados que um programa possa estar. Dentro de qualquer estado único, o programa se comporta de forma diferente, e o programa pode ser trocado de um estado para outro instantaneamente. Contudo, dependendo do estado interno atual, o programa pode ou não trocar para outros estados. Essas regras de troca, chamadas transições, também são finitas e pré determinadas. O padrão State sugere que você crie novas classes para todos os estados possíveis de um objeto e extraia todos os comportamentos específicos de estados para dentro dessas classes. Ao invés de implementar todos os comportamentos por conta própria, o objeto original, chamado contexto, armazena uma referência para um dos objetos de estado que representa seu estado atual, e delega todo o trabalho relacionado aos estados para aquele objeto.

![[pp-state.png]]
- Essa estrutura pode ser parecida com o padrão Strategy, mas há uma diferença chave. No padrão State, os estados em particular podem estar cientes de cada um e iniciar transições de um estado para outro, enquanto que estratégias quase nunca sabem sobre as outras estratégias.
### Strategy 
Permite que você defina uma família de algoritmos, coloque-os em classes separadas, e faça os objetos deles intercambiáveis. O padrão Strategy sugere que você pegue uma classe que faz algo específico em diversas maneiras diferentes e extraia todos esses algoritmos para classes separadas chamadas estratégias.

![[pp-strat.png]]
### Template Method
Define o esqueleto de um algoritmo na superclasse mas deixa as subclasses sobrescreverem etapas específicas do algoritmo sem modificar sua estrutura. O padrão do Template Method sugere que você quebre um algoritmo em uma série de etapas, transforme essas etapas em métodos, e coloque uma série de chamadas para esses métodos dentro de um único método padrão. As etapas podem ser tanto `abstratas`, ou ter alguma implementação padrão. Para usar o algoritmo, o cliente deve fornecer sua própria subclasse, implementar todas as etapas abstratas, e sobrescrever algumas das opcionais se necessário (mas não o próprio método padrão).

![[pp-templ.png]]
### Visitor
Permite que você separe algoritmos dos objetos nos quais eles operam. O padrão Visitor sugere que você coloque o novo comportamento em uma classe separada chamada visitante, ao invés de tentar integrá-lo em classes já existentes. O objeto original que teve que fazer o comportamento é agora passado para um dos métodos da visitante como um argumento, desde que o método acesse todos os dados necessários contidos dentro do objeto.

![[pp-visit.png]]