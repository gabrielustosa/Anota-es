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
# Métricas e Estimativas de Software
As métricas de software são medidas que não se baseiam em leis quantitativas da matemática ou da física. Na maioria das vezes, elas são indiretas, abertas ao debate. Estas fornecem uma indicação em tempo real da eficácia dos seus processos de software (análise, projeto e testes) e da qualidade geral do software sendo criado.
#### Medidas, métricas e indicadores
Embora os termos medida, medição e métricas sejam frequentemente usados indistintamente, é importante notar as diferenças sutis entre eles. Quando um único dado é coletado (por exemplo, o número de erros descobertos em um componente de software), foi estabelecida uma medida. A medição ocorre como resultado da coleta de um ou mais pontos de dados (por exemplo, um conjunto de revisões de componente e testes de unidade são investigados para coletar medidas do número de erros para cada um). Uma métrica de software relaciona as medidas individuais de alguma maneira (por exemplo, o número médio de erros encontrados por revisão ou o número médio de erros encontrados por teste de unidade).

Um engenheiro de software coleta medidas e desenvolve métricas para obter indicadores. Um indicador é uma métrica ou combinação de métricas que fornecem informações sobre o processo de software, em um projeto de software ou no próprio produto.

Para a criação de uma nova métrica, esta deve ser relativamente fácil de aprender ou derivar, seu cálculo não deve exigir esforço ou tempo fora do normal. A métrica deve satisfazer as noções intuitivas do engenheiro sobre o atributo do produto considerado (p. ex., uma métrica que mede coesão de módulos deve crescer em valor à medida que o nível de coesão aumenta). A métrica deve sempre produzir resultados que não sejam ambíguos.
#### Análise de dados de Software
Pode fornecer aos engenheiros de software métricas significativas para melhores tomadas de decisões baseadas no uso de ferramentas automatizadas, capazes de processar grandes conjuntos de dados dinâmicos de métricas e medidas de engenharia. A análise de software pode ajudar os desenvolvedores a tomar decisões sobre: 

- **Testes direcionados**: Para ajudar a focar os recursos de testes de regressão e de testes de integração.
- **Refatoração direcionada**: Para ajudar a tomar decisões estratégicas sobre como evitar grandes custos de dívida técnica.
- **Planejamento de versões**: Para ajudar a garantir que as necessidades de mercado e as características técnicas do produto de software serão levadas em conta.
- **Entendimento sobre os clientes**: Para ajudar os desenvolvedores a obter informações que levam a ações concretas sobre o uso do produto por parte dos clientes no campo durante a engenharia do produto.
- **Avaliação da estabilidade**: Para ajudar gerentes e desenvolvedores a monitorar o estado do protótipo em evolução e antecipar necessidades de manutenção futuras.
- **Inspeção direcionada**: Para ajudar as equipes a determinar o valor de atividades de inspeção individuais, a sua frequência e o seu escopo.
# Análise de Ponto Função
A Análise de Pontos de Função é uma técnica de medição das funcionalidades de um software sob o ponto de vista do usuário, ou seja, determina o tamanho funcional do software. A técnica mede o software quantificando as tarefas e serviços (isto é, funcionalidade) que o software fornece ao usuário, primordialmente com base no projeto lógico. Este é derivado por meio de uma relação empírica baseada em medidas calculáveis (diretas) do domínio de informações do software e avaliações qualitativas da complexidade do software.

Os objetivos da análise de pontos de função são:
- Medir a funcionalidade implementada no software, que o usuário solicita e recebe;
- Medir a funcionalidade impactada pelo desenvolvimento, melhoria e manutenção de software, independentemente da tecnologia utilizada na implementação.

Ponto de Função (PF) é a unidade de medida que tem por objetivo tornara medição independente da tecnologia utilizada para a construção do software. Essa medida está diretamente relacionada aos requisitos de negócio que o software se destina a abordar, ou seja, busca medir o que o software faz e não como ele foi construído. Portanto, pode ser facilmente aplicada em uma ampla gama de ambientes de desenvolvimento e ao longo do ciclo de um projeto de desenvolvimento, desde a definição de requisitos até o uso operacional completo. A técnica fornece uma medida objetiva e comparativa que auxilia na avaliação, planejamento, gestão e controle da produção de software.
#### Processos

![[arq-analpf.png]]

1. **Obter documentação disponível do projeto**: A contagem de pontos de função se inicia com a análise da documentação disponível do projeto em questão, visando à identificação dos requisitos funcionais.
2. **Propósito da Contagem**: Uma contagem deve prover uma resposta a um problema do negócio e é o problema do negócio que determina o propósito. O objetivo, nesta etapa, é tornar claro o que se pretende atingir com a contagem que será feita. Exemplos de tipos de propósito da contagem são:
	- Projeto de Desenvolvimento: Este tipo de contagem mede a funcionalidade entregue ao usuário na primeira instalação do software, quando o projeto estiver completo.
	- Projeto de Melhoria (baseline): Este tipo de contagem mede as modificações em uma aplicação já existente que adicione, altere ou exclua funções entregues ao usuário quando o projeto estiver completo.
	- Aplicação: Este tipo de contagem está relacionado à aplicação instalada. Representa a baseline da contagem de pontos de função de uma aplicação, ou seja, é uma medida das funções atuais providas ao usuário.
3. **Escopo da aplicação**: define o conjunto de requisitos funcionais de usuários para ser incluídos na contagem. 
	- Define o (sub)conjunto do software que está sendo medido;
	- É determinado pelo propósito para a realização da contagem de pontos de função;
	- Identifica quais funções serão incluídas na medida de tamanho funcional assim como fornecer respostas relevantes para o propósito da contagem
	- Pode incluir mais de uma aplicação.
4. **Fronteira da aplicação**:  Uma interface conceitual entre o software sob estudo e seus usuários. A fronteira deve ser definida com base na perspectiva de negócio, nas áreas funcionais separadas como pode ser visto pelo usuário, não em considerações técnicas (por exemplo, arquitetura do sistema). 
	A fronteira da aplicação:
	- Define o que é externo à aplicação;
	- Indica a fronteira entre o software que está sendo medido e o usuário;
	- Atua como uma ‘membrana’ através da qual os dados processados pelas transações (EEs, SEs e CEs) passam para dentro e para fora da aplicação
	- Envolve os dados lógicos mantidos pela aplicação (ALIs);
	
```ad-tip
##### Ordem de execução de contagem 
Na prática, a contagem não tem uma ordem fixa para contagem dos tipos de função. No entanto, é recomendável iniciar pelas **funções de dados**, pois elas representam os dados manipulados pelas transações e são a base da aplicação. Após entender os dados com que o sistema trabalha, passa-se a contagem das **funções de transação**, que são as funcionalidades que alteram esses dados ou permitem aos usuários interagir com eles. 
```
#### Funções de dados
As funções de dados representam a funcionalidade oferecida ao usuário para satisfazer requisitos de armazenamento de dados internos e externos. Uma função de dado pode ser um arquivo lógico interno (ALI) ou um arquivo de interface externo (AIE).
##### Arquivo Lógico Interno (ALI)
Grupo de dados ou informações de controle logicamente relacionados, identificável pelo usuário, mantido dentro da fronteira da aplicação. A intenção primária de um ALI é armazenar dados mantidos através de um ou mais processos elementares da aplicação sendo contada.
##### Arquivo de Interface Externa (AIE)
Grupo de dados logicamente relacionados ou informação de controle, reconhecido pelo usuário, referenciado pela aplicação sendo medida, mas que é mantido dentro da fronteira de outra aplicação. A intenção primária de um AIE é armazenar dados referenciados por um ou mais processos elementares dentro da fronteira da aplicação medida. Isto significa que um AIE contado por uma aplicação deve ser um ALI em outra aplicação. Deverão ser considerados na complexidade de um AIE apenas os itens de dados e os registros lógicos referenciados pela aplicação que está sendo contada.
#### Funções Transacionais
Uma função de transação é um processo elementar que oferece funcionalidade ao usuário para processar dados. Uma função de transação é uma entrada externa, saída externa, ou consulta externa.
##### Entrada Externa (EE)
Processo elementar que processa dado (ou informações de controle) vindo de fora da fronteira da aplicação. A principal intenção de uma EE é manter um ou mais ALI e/ou alterar o comportamento do sistema.
##### Consulta Externa (CE)
Processo elementar que envia dados ou informações de controle para fora da fronteira da aplicação. A principal intenção de uma CE é apresentar informação ao usuário por meio de uma simples recuperação de dados ou informações de controle de um ALI ou AIE. A lógica de processamento não deve conter fórmula matemática ou cálculo, criar dados derivados, manter um ou mais ALI e/ou alterar o comportamento do sistema
##### Saída Externa (SE)
Processo elementar que gera dados ou informações de controle que saem pela fronteira da aplicação. A principal intenção de uma SE é apresentar dados ao usuário através de outra lógica de processamento que não apenas a recuperação de dados ou informações de controle. A lógica de processamento deve conter fórmula matemática ou cálculo, criar dados derivados, manter um ou mais ALI e/ou alterar o comportamento do sistema.

| Tipo | Baixa | Média | Alta  |
| ---- | ----- | ----- | ----- |
| ALI  | 7 PF  | 10 PF | 15 PF |
| AIE  | 5 PF  | 7 PF  | 10 PF |
| EE   | 3 PF  | 4 PF  | 6 PF  |
| SE   | 4 PF  | 5 PF  | 7 PF  |
| CE   | 3 PF  | 4 PF  | 6 PF  |

#### Nível de Detalhamento de Contagens
A contagem de pontos de função pode ser realizada com diferentes níveis de detalhe: indicativa, estimada e detalhada. O nível de detalhamento a ser escolhido depende de alguns fatores como a finalidade da contagem, as informações disponíveis para subsidiar a contagem, a etapa do ciclo de vida do desenvolvimento, dentre outros.
##### Contagem Indicativa
A contagem indicativa é utilizada para estimar de forma rápida o tamanho de projetos de desenvolvimento de novas aplicações. Devido ao pouco conhecimento do sistema que se precisa estimar, ela é baseada somente na identificação de quantos arquivos lógicos (ALIs e AIEs) existirão na aplicação. A contagem indicativa é realizada da seguinte forma:

- Determina-se a quantidade das funções do tipo dado (ALIs e AIEs)
##### Contagem Estimada
A contagem estimada é utilizada quando é possível identificar as funções do sistema, porém não se define a complexidade (tipos de dados, tipos de registros e arquivos referenciados).

Dessa forma, assume-se uma complexidade padrão para as funções, sendo as funções de dados (ALIs e AIEs) classificadas como de baixa complexidade, enquanto as funções transacionais (EEs, CEs e SEs) são classificadas como de média complexidade.

A contagem estimada é realizada da seguinte forma: 
- Determina-se todas as funções de todos os tipos (ALI, AIE, EE, SE, CE); 
- Toda função do tipo dado (ALI, AIE) tem sua complexidade funcional avaliada como Baixa; 
- Toda função transacional (EE, SE, CE) é avaliada como de complexidade média; 
- Calcula-se o total de pontos de função não ajustados.
##### Contagem Detalhada
A contagem detalhada é a contagem usual de pontos de função e é realizada da seguinte forma:

- Determina-se todas as funções de todos os tipos (ALI, AIE, EE, SE, CE);
- Determina-se a complexidade de cada função (Baixa, Média, Alta);
- Calcula-se o total de pontos de função não ajustados.