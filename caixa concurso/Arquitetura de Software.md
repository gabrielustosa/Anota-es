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
O MVC é focado em aplicações interativas, sendo essa sua base arquitetural.
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

```ad-tip
-> É mais fácil de modificar uma camada sem afetar as outras;
-> Mais segurança na camada do servidor;
-> Em geral, diminui performance;
-> Maior esforço de desenvolvimento.
```
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
#### Benefícios
- **Flexibilidade:** A SOA facilita a integração de sistemas heterogêneos, tornando as aplicações mais adaptáveis a mudanças.
- **Manutenibilidade:** Ao isolar funcionalidades em serviços, a manutenção e atualização do código se tornam mais fáceis.
- **Escalabilidade:** A arquitetura permite o dimensionamento independente dos serviços para atender a demandas crescentes.
- **Reuso de código:** Os serviços reutilizáveis reduzem a duplicação de código e otimizam o desenvolvimento.
#### Desvantagens 
- **Complexidade:** O design e implementação de uma SOA podem ser mais complexos do que abordagens monolíticas.
- **Performance:** A comunicação entre serviços pode introduzir overhead e impactar a performance do sistema.
- **Governança:** É necessário estabelecer um bom plano de governança para garantir a consistência, segurança e interoperabilidade dos serviços.
# Arquitetura Monolítica
Todos os componentes são construídos como uma única base de código e implantados como um único arquivo. Nesta variante da arquitetura monolítica, um único processo de aplicativo consiste em vários módulos. Cada um desses módulos pode funcionar de forma independente. Os módulos possuem interfaces e podem se comunicar entre si por meio dessas interfaces. O banco de dados subjacente é o mesmo e todos os módulos usam o mesmo banco de dados para todas as operações. Mesmo assim, todos os módulos precisam ser combinados para formar um único arquivo para implantação.
# Arquitetura Microsserviços  
Os microsserviços são uma arquitetura e uma abordagem para escrever programas de software. Com eles, as aplicações são desmembradas em componentes mínimos e independentes. Diferentemente da abordagem tradicional monolítica em que toda a aplicação é criada como um único bloco, os microsserviços são componentes separados que trabalham juntos para realizar as mesmas tarefas. Cada um dos componentes ou processos é um microsserviço. Essa abordagem de desenvolvimento de software valoriza a granularidade, a leveza e a capacidade de compartilhar processos semelhantes entre várias aplicações.
# Micro Front End
Micro Frontends é uma abordagem arquitetural que se concentra em decompor um aplicativo frontend em partes menores e mais gerenciáveis. Ela se inspira no conceito de microsserviços no desenvolvimento backend e o aplica ao frontend.
# Arquitetura de solução
Foca na estruturação e definição de sistemas de software específicos dentro de um contexto mais amplo. Define os componentes do sistema, suas interações e como eles se integram à infraestrutura e outros sistemas. Considera aspectos como funcionalidade, escalabilidade, segurança e desempenho.

- Arquitetura de software: É uma disciplina mais abrangente que lida com todos os aspectos do design e desenvolvimento de software.
- Inclui desde a definição de requisitos até a implementação e testes do software.
- Abrange conceitos como padrões de design, metodologias de desenvolvimento e ferramentas de software
# Métricas e Estimativas de Software
As métricas de software são medidas que não se baseiam em leis quantitativas da matemática ou da física. Na maioria das vezes, elas são indiretas, abertas ao debate. Estas fornecem uma indicação em tempo real da eficácia dos seus processos de software (análise, projeto e testes) e da qualidade geral do software sendo criado.
### Técnicas de Estimativas
#### Técnicas baseadas em experiências
 Usam conhecimento adquirido em projetos anteriores de um mesmo domínio
#### Modelagem algorítmica de custos
É feito um modelo matemático esforço é calculado com base em estimativas de atributos do software, tamanho, processo, etc.
##### COCOMO II 
Modelo de estimativa de custos, baseado no COCOMO Considera abordagens mais modernas de desenvolvimento de software.
#### Projeto Preliminar
Usado quando os requisitos foram feitos, mas o projeto ainda não foi iniciado, o objetivo é fornecer uma estimativa aproximada de custo baixo (mesmo que imprecisa). A estimativa é feita em pontos de função e convertida para linhas de código.
#### Modelo de Reuso
Usado para calcular o esforço de integração de componentes reusáveis. Geralmente usado em conjunto com o modelo pós arquitetura

Impactado por três fatores principais
- SU: custos de compreender o código
- AA: custos de avaliação e tomada de decisão
- AFF: adaptação do código para reuso
#### Estimativa análoga (Similaridade)
A estimativa análoga baseia-se no princípio de que projetos similares terão custos similares. Portanto, ao comparar o projeto atual com projetos passados que foram semelhantes em tamanho e complexidade, é possível fornecer uma estimativa de custo aproximada.
#### Bottom-up (Agregação das estimativas)
A técnica bottom-up envolve a agregação das estimativas dos componentes individuais de nível mais baixo da Estrutura Analítica do Projeto (EAP) para obter a estimativa do projeto como um todo. Cada componente é detalhado e estimado separadamente, e essas estimativas são então somadas para obter uma estimativa total. Essa abordagem é mais precisa e detalhada, pois leva em consideração as características específicas de cada parte do projeto.
#### Paramétrica  (Modelos estatísticos)
Nesta técnica, a estimativa é feita com base em relações estatísticas entre os dados históricos e os parâmetros do projeto. Ela utiliza modelos matemáticos para calcular a duração ou o custo com base em variáveis como tamanho, complexidade, etc.
#### Três Pontos (Otimista, mais provável, pessimista)
Esta técnica envolve a estimativa de três valores para cada atividade: otimista, mais provável e pessimista. A estimativa final é calculada usando uma média ponderada desses três valores, o que leva em consideração incertezas e riscos associados à atividade.
#### Monte Carlo (Simulação)
Esta técnica utiliza simulações estatísticas para prever os resultados possíveis de um projeto com base em várias variáveis ​​e incertezas. Ela gera uma série de simulações para avaliar o impacto de diferentes cenários e incertezas no projeto.
### Medidas, métricas e indicadores
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
### Tipos de Métrica x Método de Medição
##### Métrica de Requisitos
Medir o software do ponto de vista do usuário, levando em conta como será a interação do mesmo com o software e o que é esperado de cada interação. As regras de negócio devem ser especificadas, assim como regras de interface entre o software e o usuário. No final da contagem é mensurado o quanto que o usuário solicita de requisitos e/ou quanto o mesmo recebe.

**Métodos de medição**: Análise de Pontos de Função e NESMA.
##### Métrica de Arquitetura
Medir a capacidade da arquitetura, em termos de quantidade de funcionalidades encapsuladas a mesma fornece para os projetistas, desenvolvedores e testadores.

**Métodos de medição**: Não existe métricas formais. A arquitetura pode ser analisada pela quantidade de componentes abstratos e interfaces de serviços não-funcionais que a mesma atende.
##### Métrica de Projeto UML
Mede a quantidade de artefatos UML descrevem o software de forma horizontal e vertical. Consideramos horizontal a quantidade de tipos de artefatos, tais como Diagramas de Classe, Sequências, Componentes, Implantação, etc. Verticalmente a quantidade de elementos por diagrama, tal como Nós no Diagrama de Implantação, classes no Diagrama de Classe, etc.

**Método de medição**: Não existe uma métricas formais. O Projeto UML é documentado de forma quantitativa, e a empresa deve criar um guia formalizando as regras de documentação com a finalidade de restringir o escopo de esforço, controlar a qualidade e tornar a base histórica de contagem efetiva para fins de estimativa.
##### Métrica de Banco de Dados
Mede as estruturas físicas e lógicas do banco de dados. Como o banco de dados está estruturado e as operações que são realizadas no mesmo devem ser mensuradas. É conveniente que até mesmo os tipos, periodicidades e tamanho de backup sejam mensurados e documentados. Por questões de gerenciamento é uma boa prática mensurar a arquitetura física do banco de dados, tal como Datafiles, Tablespaces, etc.

**Métodos de medição**: Por padrão é de costume dos DBAs mensurar a quantidade de tabelas, quantidade de registros em sua carga inicial e fator de crescimento de registros em cada tabela. Os registros são mensurados considerando um fator quantitativo e também físico em bytes, com base na quantidade de bytes de cada registro. Colunas do tipo BLOB, CLOB, FILE, etc. devem ser mensuradas separadamente se orientando também nos requisitos de negócio e requisitos não-funcionais.
##### Métrica de Implementação
Mede fisicamente o tamanho do código implementado. Esta medida pode ser o tamanho físico em quantidade de linhas de cada arquivo de código fonte, ou lógica utilizando a quantidade de comandos existem em cada linha de código fonte.

**Método de medição**: LOC (Line Of Code). 

```ad-summary
#### LOC (Line of Code)
Técnica utilizada para na contagem literal do número de linhas presentes no código-fonte, incluindo linhas em branco e comentários. A técnica LOC possui duas variantes, SLOC (Sorce Line Of Code) e LLOC (Logical Line Of Code), que medem respectivamente a quantidade de linhas físicas e quantidade de comandos por linha de código.
```
##### Métrica de Teste
Mede a quantidade de código que é coberto pelos testes. Existem diversos tipos de testes, Teste Unitário,  Teste Funcional, Teste de Aceitação, etc. O mais importante é ter devidamente documentado e acordado a quantidade mínima de código que deve ser coberto pela técnica escolhida.

**Método de medição**: Code Coverage.
##### Métrica de Performance
Com os atuais dispositivos de pequeno porte em relação aos computadores, tais como Tablets e Smartphones, a performance de execução da aplicação retornou a ser um fator crucial para o sucesso e fracasso de um software, podendo até mesmo não alcançar determinados usuários por conta de fatores também relacionados e capacidade de telecomunicação.

Previamente a produção do software, no momento em que o Arquiteto de Software estiver projetando o mesmo, deve-se documentar e estabelecer os requisitos mínimos e máximos de performance para o correto desenvolvimento da arquitetura de software e seleção de tecnologias e frameworks.

Cabe ao Arquiteto de Software orientar ao Analista de Requisitos a projetar a realização do negócio com telas (protótipos) contendo barras de progresso, ou até mesmo operações assíncronas quando o processamento for inevitavelmente pesado.

**Método de medição**: Mensurar em milissegundos a velocidade média que cada funcionalidade de negócio, que responde a cada ação do usuário nos tipos de dispositivos contemplados na arquitetura, estão de acordo o esperado.
##### Métrica de Implantação
A complexidade e cada atividade envolvida no processo de implantação do software afeta de forma significativa o projeto.

Na etapa de implantação, principalmente primeira implantação, muitas vezes é necessário diversos perfis de profissional, bem como os mais capacitados da equipe para realizar tais atividades. Caso a implantação não seja mensurada o gestor de projeto poderá encontrar um planejamento “obscuro” onde a estimativa de Custo, Prazo e Esforço é baseada simplesmente no “feeling” e suscetível a muitas falhas de planejamento, resultando em baixo lucro ou até mesmo prejuízo, juntamente com o constrangimento do cliente.

**Método de medição**: De acordo com a Base de Projetos formada pela empresa, deve-se obter o esforço médio de implantação com cada atividade da implantação, por exemplo, instalação de banco de dados, instalação de bibliotecas, configuração de usuários, etc.
##### Métrica de Integração
Projetos de software possuem alto risco ao desenvolver integrações. O Arquiteto de Software consegue estimar tecnicamente o esforço para integrar com determinado protocolo, mas jamais conseguirá estimar a estabilidade, risco, complexidade causada por pouca ou nenhuma documentação existente. Para evitar que problemas de integração sejam incorporados ao desenvolvimento do software e causa raiz para baixa produtividade da equipe, deve-se tratá-lo isoladamente com a finalidade de identificar o real riso e produtividade do mesmo, por exemplo, integrar com a Receita Federal, com o SAP, ou determinado banco financeiro, etc.

**Método de medição:** Mensurar o esforço e manter a produtividade na base de projetos separadamente, por exemplo, a produtividade para integrar um software com uma rede social, um órgão público, etc. deve ser mantido separadamente do esforço para desenvolver as funcionalidades para o usuário final.
##### Métrica de Operação
Mesmo com o software desenvolvido, implantado e integrado com sucesso nada adianta se não for possível operacionalizá-lo. Como o gestor conseguirá estimar tal operacionalização? A resposta é simples! Mensurar o nível de mudança do software, a depreciação das tecnologias requerendo atualizações e upgrades, a produtividade e perfis dos profissionais envolvidos nas soluções de incidentes e desenvolvimento de mudanças e melhorias, o índice de SLA acordado em todas as infraestruturas envolvidas e comparar tudo isso a base de projetos.

**Método de medição**: Reunir todas as atividades recorrentes, catalogar pelas criticidades, catalogar a produtividade de cada perfil da equipe em horas/criticidade. Assim poderá mensurar o prazo e custo médio para realizar determinada quantidade de atividades recorrentes com a equipe formada.
##### Métrica de Monitoramento
Uma operação por mais mensurada que seja não conseguirá fornecer informações suficiente para que ações proativas sejam tomadas para que um software não tenham incidentes de alta gravidade e risco. Para que possamos atuar proativamente e de forma preventiva temos que observar como que todo o ambiente onde o software está implantado se comporta, e para isso temos que monitorá-lo a maior quantidade de elementos possíveis.

A quantidade de elementos a serem monitorados determinará o custo do monitoramento e sua eficiência.

**Método de medição**: Levantar todos os itens de monitoramento do ambiente implantado e integrado, por exemplo, processador, memória, rede, internet, temperatura, espaço de armazenamento, etc. de toda infraestrutura. A quantidade de elementos definirá a complexidade de alertas e itens para atenção. Deve-se ter cuidado para não selecionar itens em demasia, pois sempre que isso acontece resulta em e-mails e SMS ignorados pelos técnicos como o “erro conhecido” infelizmente.
# Análise de Ponto Função
A Análise de Pontos de Função é uma técnica de medição das funcionalidades de um software sob o ponto de vista do usuário, ou seja, determina o tamanho funcional do software. A técnica mede o software quantificando as tarefas e serviços (isto é, funcionalidade) que o software fornece ao usuário, primordialmente com base no projeto lógico. Este é derivado por meio de uma relação empírica baseada em medidas calculáveis (diretas) do domínio de informações do software e avaliações qualitativas da complexidade do software.

Os objetivos da análise de pontos de função são:
- Medir a funcionalidade implementada no software, que o usuário solicita e recebe;
- Medir a funcionalidade impactada pelo desenvolvimento, melhoria e manutenção de software, independentemente da tecnologia utilizada na implementação.
- Estimular o custo ou esforço necessário para projetar, codificar e testar o software.
- Prever o número de erros que vão ser encontrados durante o teste.
- Prever o número de componentes e/ou o número de linhas de código projetados no sistema implementado.

Ponto de Função (PF) é a unidade de medida que tem por objetivo tornara medição independente da tecnologia utilizada para a construção do software. Essa medida está diretamente relacionada aos requisitos de negócio que o software se destina a abordar, ou seja, busca medir o que o software faz e não como ele foi construído. Portanto, pode ser facilmente aplicada em uma ampla gama de ambientes de desenvolvimento e ao longo do ciclo de um projeto de desenvolvimento, desde a definição de requisitos até o uso operacional completo. A técnica fornece uma medida objetiva e comparativa que auxilia na avaliação, planejamento, gestão e controle da produção de software.
#### Processos

```ad-note
##### Processo simplificado
1. Reunir a documentação disponível;
2. Determinar o escopo e a fronteira da contagem;
3. Medir as funções de dados (ALI e AIE);
4. Medir as funções de transação ( CE - SE - EE);
5. Calcular o tamanho funcional ( Contagem de desenvolvimento; Aplicação; ou Melhoria);
6. Documentar e reportar a contagem de pontos de função;
```

![[arq-analpf.png]]

1. **Obter documentação disponível do projeto**: A contagem de pontos de função se inicia com a análise da documentação disponível do projeto em questão, visando à identificação dos requisitos funcionais.
2. **Propósito da Contagem**: Uma contagem deve prover uma resposta a um problema do negócio e é o problema do negócio que determina o propósito. O objetivo, nesta etapa, é tornar claro o que se pretende atingir com a contagem que será feita. Por exemplo: _“Qual o tamanho deste software a nível funcional? Quanto tempo para desenvolver? Qual o tamanho da equipe?..”_. Os tipos de propósito da contagem são:
	- **Projeto de Desenvolvimento**: Este tipo de contagem mede a funcionalidade entregue ao usuário na primeira instalação do software, quando o projeto estiver completo.
	- **Projeto de Melhoria**: Este tipo de contagem mede as modificações em uma aplicação já existente que adicione, altere ou exclua funções entregues ao usuário quando o projeto estiver completo.
	- **Aplicação**: Este tipo de contagem está relacionado à aplicação instalada. Representa a baseline da contagem de pontos de função de uma aplicação, ou seja, é uma medida das funções atuais providas ao usuário.
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

![[arq-anlalpf-fa.png]]
##### Arquivo Lógico Interno (ALI)
Grupo de dados ou informações de controle logicamente relacionados, identificável pelo usuário, mantido dentro da fronteira da aplicação. A intenção primária de um ALI é armazenar dados mantidos através de um ou mais processos elementares da aplicação sendo contada.
##### Arquivo de Interface Externa (AIE)
Grupo de dados logicamente relacionados ou informação de controle, reconhecido pelo usuário, referenciado pela aplicação sendo medida, mas que é mantido dentro da fronteira de outra aplicação. A intenção primária de um AIE é armazenar dados referenciados por um ou mais processos elementares dentro da fronteira da aplicação medida. Isto significa que um AIE contado por uma aplicação deve ser um ALI em outra aplicação. Deverão ser considerados na complexidade de um AIE apenas os itens de dados e os registros lógicos referenciados pela aplicação que está sendo contada.
#### Funções Transacionais
Uma função de transação é um processo elementar que oferece funcionalidade ao usuário para processar dados. Uma função de transação é uma entrada externa, saída externa, ou consulta externa.
##### Entrada Externa (EE)
Processo elementar que processa dado (ou informações de controle) vindo de fora da fronteira da aplicação. A principal intenção de uma EE é manter um ou mais ALI e/ou alterar o comportamento do sistema. Representa o processamento de dados enviados pelo usuário.
##### Consulta Externa (CE)
Processo elementar que envia dados ou informações de controle para fora da fronteira da aplicação. A principal intenção de uma CE é apresentar informação ao usuário por meio de uma simples recuperação de dados ou informações de controle de um ALI ou AIE. A lógica de processamento não deve conter fórmula matemática ou cálculo, criar dados derivados, manter um ou mais ALI e/ou alterar o comportamento do sistema
##### Saída Externa (SE)
Processo elementar que gera dados ou informações de controle que saem pela fronteira da aplicação. A principal intenção de uma SE é apresentar dados ao usuário através de outra lógica de processamento que não apenas a recuperação de dados ou informações de controle. A lógica de processamento deve conter fórmula matemática ou cálculo, criar dados derivados, manter um ou mais ALI e/ou alterar o comportamento do sistema.

```ad-tip
**Entrada Externa**: pode ou não alterar o comportamento do sistema;
**Consulta Externa**: não irá alterar o comportamento do sistema.
**Saída Externa**: irá alterar o comportamento do sistema;
```
#### Tabela de Valores

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
# Estratégias de Migração de Aplicações para o ambiente de nuvem
A migração para a nuvem é um processo essencial para muitas organizações que desejam aproveitar os benefícios da computação em nuvem, como escalabilidade, flexibilidade e redução de custos.
#### Lift and Shift
A estratégia Lift and Shift (Elevar e Deslocar) envolve mover os aplicativos e sistemas existentes para a nuvem sem fazer grandes alterações em sua arquitetura ou funcionalidade. É uma abordagem relativamente simples e rápida de migração para a nuvem, pois requer menos modificações nos aplicativos existentes.

A ideia principal por trás do Lift and Shift é transferir os aplicativos de um ambiente on-premise (local) para um ambiente de nuvem, como infraestrutura como serviço (IaaS) ou máquinas virtuais. Os aplicativos são “elevados” do ambiente atual e “deslocados” para a nuvem, mantendo sua configuração e arquitetura básicas.

Algumas características e considerações da estratégia Lift and Shift são:

1. **Migração rápida**: Como não são necessárias grandes modificações na arquitetura e no código dos aplicativos, a migração pode ser realizada de forma relativamente rápida. Isso permite que as organizações aproveitem rapidamente os benefícios da nuvem, como escalabilidade e disponibilidade.
2. **Menor custo de migração**: Comparado a estratégias de modernização, o Lift and Shift geralmente tem um custo de migração menor. Isso ocorre porque não há necessidade de refatorar ou reescrever o código dos aplicativos existentes.
3. **Utilização limitada dos recursos da nuvem**: Ao adotar a estratégia Lift and Shift, os aplicativos são executados em uma infraestrutura de nuvem semelhante à infraestrutura local. Isso significa que os aplicativos podem não aproveitar totalmente os recursos nativos da nuvem, como escalabilidade automática, serviços gerenciados e arquiteturas sem servidor.
4. **Necessidade de gerenciamento contínuo**: Apesar de migrar para a nuvem, ainda é necessário gerenciar e manter a infraestrutura e os aplicativos. Os patches de segurança, atualizações e outras tarefas de administração ainda precisam ser realizadas.
#### Modernização da Arquitetura
A estratégia de modernização de arquitetura é um processo mais abrangente de migração para a nuvem. Envolve redesenhar ou reestruturar os aplicativos durante a migração, a fim de aproveitar ao máximo os recursos nativos da nuvem e adotar práticas modernas de desenvolvimento de software.

A modernização de arquitetura visa superar algumas das limitações da abordagem Lift and Shift, permitindo que os aplicativos aproveitem os benefícios da nuvem de forma mais completa. Alguns pontos-chave da modernização de arquitetura incluem:

1. **Replanejamento da arquitetura**: Nessa estratégia, é feita uma análise da arquitetura existente para identificar oportunidades de melhoria e otimização. Pode envolver a reorganização dos componentes do sistema em uma abordagem baseada em microsserviços, que favorece a escalabilidade, a modularidade e a resiliência dos aplicativos.
2. **Adoção de contêineres**: A modernização de arquitetura muitas vezes inclui a adoção de contêineres, como o Docker, para encapsular os aplicativos e suas dependências em unidades isoladas e portáteis. Isso facilita a implantação consistente e escalável dos aplicativos em diferentes ambientes de nuvem.
3. **Uso de serviços gerenciados**: A estratégia busca utilizar serviços gerenciados oferecidos pelas provedoras de nuvem para tarefas comuns, como bancos de dados, armazenamento e filas de mensagens. Isso reduz a carga operacional de gerenciamento desses recursos e permite que a equipe de desenvolvimento foque mais no desenvolvimento do aplicativo em si.
4. **Arquitetura sem servidor (Serverless)**: A modernização de arquitetura também pode envolver a adoção de uma arquitetura sem servidor, na qual as responsabilidades operacionais são transferidas para a provedora de nuvem. Os aplicativos são divididos em funções individuais, que são executadas sob demanda em resposta a eventos específicos. Isso permite uma maior escalabilidade automática e uma cobrança com base no uso efetivo dos recursos.
5. **Automação e orquestração**: A modernização de arquitetura também pode incluir a implementação de ferramentas de automação e orquestração, como o Kubernetes, para gerenciar e escalar os aplicativos de forma eficiente, garantindo alta disponibilidade e resiliência.

A modernização de arquitetura é mais complexa e demorada em comparação com a estratégia Lift and Shift, pois requer mudanças mais significativas nos aplicativos e em sua infraestrutura. No entanto, essa abordagem permite que os aplicativos aproveitem ao máximo os recursos e serviços oferecidos pela nuvem, resultando em maior eficiência, escalabilidade e flexibilidade.
#### Modernização da Aplicação
A modernização de aplicação é uma estratégia mais abrangente e intensiva em termos de esforço do que as estratégias de Lift and Shift e modernização de arquitetura. Nessa abordagem, o objetivo é refatorar ou reescrever o código dos aplicativos existentes para melhorar sua eficiência, escalabilidade, segurança e recursos.

Ao modernizar uma aplicação, alguns pontos importantes a serem considerados são:

1. **Reavaliação das necessidades e requisitos**: Antes de iniciar a modernização, é essencial entender os objetivos de negócio e as necessidades dos usuários. Isso ajudará a determinar quais aspectos da aplicação precisam ser melhorados ou adicionados durante o processo de modernização.
2. **Adoção de práticas de desenvolvimento ágil**: A modernização de aplicação muitas vezes envolve a adoção de metodologias ágeis de desenvolvimento de software. Isso permite ciclos de desenvolvimento mais curtos, feedback contínuo dos usuários e flexibilidade para realizar ajustes ao longo do processo.
3. **Otimização de código**: Durante a modernização, é importante revisar e otimizar o código existente. Isso pode envolver a eliminação de código desnecessário, a melhoria do desempenho, a otimização do uso de recursos e a aplicação de boas práticas de codificação.
4. **Integração de novas tecnologias e recursos**: A modernização de aplicação pode incluir a incorporação de tecnologias e recursos modernos. Isso pode envolver a adoção de arquitetura baseada em microsserviços, a utilização de serviços gerenciados da nuvem, a implementação de recursos de inteligência artificial ou aprendizado de máquina, entre outros.
5. **Melhoria da segurança**: A modernização de aplicação pode ser uma oportunidade para reforçar a segurança dos aplicativos. Isso pode incluir a implementação de medidas de segurança adicionais, a correção de vulnerabilidades conhecidas e a adoção de boas práticas de segurança durante o desenvolvimento.
6. **Testes e garantia de qualidade**: Durante o processo de modernização, é importante realizar testes rigorosos para garantir a funcionalidade correta da aplicação. Isso pode incluir testes de unidade, testes de integração, testes de desempenho e testes de segurança.

A modernização de aplicação pode ser um processo complexo e demorado, pois exige modificações significativas no código e na funcionalidade dos aplicativos existentes. É importante ter um planejamento adequado, considerar os recursos necessários e definir metas claras para a modernização.

```ad-summary
#### Outros tipos de migração em núvem

**Improve and move:** **o ambiente é modernizado durante a migração**, adicionando recursos de nuvem como balanceamento de carga e alta disponibilidade, aprimorando as cargas de trabalho em relação ao ambiente antigo.

**Rip and Replace:** Nesse modelo você **prepara um “aplicativo” totalmente novo**, tornando-o nativo a nuvem, nesse projeto para reescrever seu aplicativo você conseguirá explorar o máximo potencial da nuvem e todos os seus recursos.
```
# Computação Serverless
Serverless é um modelo de desenvolvimento e execução de aplicativos da cloud computing que permite aos desenvolvedores construir e executar códigos de aplicativo sem fornecer ou gerenciar servidores ou infraestrutura de backend. O provedor de cloud trata do resto, fornecendo a infraestrutura em cloud necessária para executar o código, e aumentando e diminuindo a capacidade da infraestrutura sob demanda, conforme necessário.

Dada a sua combinação exclusiva de atributos e benefícios, a arquitetura serverless é adequada para casos de uso em torno de microsserviços, backends móveis, e processamento de fluxo de eventos e dados.
### Serverless e microsserviços
O caso de uso mais comum de serverless atualmente é o suporte a arquiteturas de microsserviços. O modelo de microsserviços é focado na criação de pequenos serviços que executam uma única tarefa e se comunicam com outro por meio de APIs. Embora os microsserviços também possam ser desenvolvidos e operados usando PaaS ou contêineres, o serverless obteve um impulso significativo devido aos seus atributos em torno de pequenos bits de código, ajuste de escala automático ou inerente, fornecimento rápido e um modelo de precificação que nunca cobra por capacidade inativa.
### Backends de API
Qualquer ação (ou função) em uma plataforma serverless pode ser transformada em um terminal HTTP pronto para ser consumido por clientes web. Quando ativado para a web, essas ações são chamadas de ações da web. Após ter ações da web, é possível montá-las em uma API completa com um gateway de API que proporciona segurança adicional, suporte a OAuth, limitação de taxa e suporte a domínio customizado.
### Processamento de dados
O serverless é adequado para trabalhar com texto estruturado, áudio, imagem e dados de vídeo, em torno de tarefas como enriquecimento de dados, transformação, validação, limpeza; processamento de PDF; normalização de áudio; processamento de imagem (rotação, ajuste de nitidez, redução de ruído, geração de miniatura); reconhecimento de caractere ótico (OCR); e transcodificação de vídeo. 