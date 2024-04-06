# Arquitetura em Camadas
Cada camada tem uma responsabilidade diferente na aplicação. Cada camada forma uma abstração em volta da sua necessidade e trabalho à ser realizado dentro de uma requisição em particular. Além disso, barreiras devem existir de forma implícita entre elas. A camada mais baixa inclui software de apoio ao sistema — geralmente, apoio de banco de dados e de sistema operacional. Camada superior fornecendo recursos de interface com o usuário.
#### Apresentação
A camada do cliente (consumidor), deve ser responsável por lidar com toda a interface do(a) usuário(a) e lógicas de comunicação com navegadores.
#### Negócio
A camada de negócio deveria ser responsável por executar operações e fluxos de negócios específicos associados à uma requisição.
#### Persistência
A camada de persistência deveria ser responsável por persistir ou recuperar informações fisicamente salvas em alguma unidade de armazenamento.
#### Banco de Dados
A camada do banco de dados deveria ser responsável por manter os dados salvos de forma física.
# Arquitetura MVC
#### Model
É responsável por executar as regras de negócio
- O modelo representa os dados e a lógica de negócios da aplicação.
- Ele encapsula o acesso aos dados e fornece métodos para manipulá-los.
- É responsável por validar, armazenar e recuperar os dados do sistema.
#### Controller 
Recebe as requisições dos usuários. Envia comandos para o modelo e visão alterando seus estados. Controla o fluxo da aplicação
- O controlador atua como intermediário entre o modelo e a visão.
- Ele recebe as entradas do usuário, processa as solicitações e atualiza o modelo e a visão conforme necessário.
- O controlador é responsável por coordenar as ações e manter a consistência entre o modelo e a visão
#### View
Interface de visualização e interação com o usuário ou cliente. 
- A visão é passiva e não possui lógica de negócios.
# Arquitetura Orientada a Serviços (SOA)
Tipo de design de software que torna os componentes reutilizáveis usando interfaces de serviços com uma linguagem de comunicação comum em uma rede. A SOA é uma abordagem arquitetônica que se concentra na criação de serviços independentes e reutilizáveis, que representam diferentes funcionalidades de negócios.

- A comunicação entre os serviços é realizada por um sistema de "baixo acoplamento"
- É uma abordagem de arquitetura adotada pela empresa na totalidade.
- O **BPEL** é uma linguagem padrão para a descrição de processos de negócio e a orquestração de serviços web em uma arquitetura SOA.
- Diminui o custo com solução, visto que, reaproveita serviços já existentes. 
- Independente de estado de serviço.
- **Provedor** é o elemento que disponibiliza os serviços.
- **Registro central** é o elemento que ajuda os consumidores de serviços a encontrar os serviços que precisam.****

Nas arquiteturas orientadas a serviços (SOA), os componentes de sistema são serviços autônomos na forma distribuída e os clientes de serviço que desejam usar um serviço descobrem a especificação desse serviço e localizam o provedor de serviço, para, então, ligar sua aplicação a esse serviço específico e comunicar-se com ele usando protocolos de serviço padrão.
#### Componentes 
**Provedor de Serviços** -  responsável por **CRIAR e PUBLICAR** as interfaces no registro de serviços ou broker.
**Cliente ou Solicitador de Serviços** - responsável por **CONSULTAR** as interfaces que foram disponibilizados no registro de serviços.
**Registro ou Broker de Serviço** - responsável por **DISPONIBILIZAR** as interfaces.
#### Classificações 
**Entity Services** - Empregados em operações de CRUD.
**Utility Services** - Contemplando funcionalidades que não estejam diretamente relacionadas ao negócio (log, envio de e-mail, etc.).
**Task Services** -  Utilizados na automação de processos de negócio. Tais estruturas costumam implementar a composição de serviços, com o consumo de Entity e/ou Utility Services.
**Orchestrated Task Services** - Os quais incorporam lógica de orquestração e controlam o fluxo em composições de serviços que envolvam Entity, Utility e Task Services.
# Arquitetura Monolítica
Todos os componentes são construídos como uma única base de código e implantados como um único arquivo. Nesta variante da arquitetura monolítica, um único processo de aplicativo consiste em vários módulos. Cada um desses módulos pode funcionar de forma independente. Os módulos possuem interfaces e podem se comunicar entre si por meio dessas interfaces. O banco de dados subjacente é o mesmo e todos os módulos usam o mesmo banco de dados para todas as operações. Mesmo assim, todos os módulos precisam ser combinados para formar um único arquivo para implantação.
# Arquitetura Microsserviços  
Os microsserviços são uma arquitetura e uma abordagem para escrever programas de software. Com eles, as aplicações são desmembradas em componentes mínimos e independentes. Diferentemente da abordagem tradicional monolítica em que toda a aplicação é criada como um único bloco, os microsserviços são componentes separados que trabalham juntos para realizar as mesmas tarefas. Cada um dos componentes ou processos é um microsserviço. Essa abordagem de desenvolvimento de software valoriza a granularidade, a leveza e a capacidade de compartilhar processos semelhantes entre várias aplicações.
# Micro Front End
Micro Frontends é uma abordagem arquitetural que se concentra em decompor um aplicativo frontend em partes menores e mais gerenciáveis. Ela se inspira no conceito de microsserviços no desenvolvimento backend e o aplica ao frontend.