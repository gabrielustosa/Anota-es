Conjunto de dados produzidos atualmente no mundo, cujo volume está além dos padrões e da capacidade das ferramentas utilizadas por bancos de dados para capturá-los, analisá-los e gerenciá-los.

- Decisões baseadas em tempo real.
- Foco na descoberta de tendências, correlações, aprender com os dados.
- Análise preditiva dos dados.
- Lida com dados estruturados (SQL), semiestruturados (JSON, XML) e não estruturados (Imagens, Vídeos).
- Necessidade de baixa latência (o tempo que um sistema demora para responder a um evento).
#### Diferença entre Big Data e Data Warehouse
A diferença de Data Warehouse e Big Data é a velocidade com que os dados precisam ser disponibilizados, uma vez que, em um projeto de Data Warehouse, o processo de ETL torna-se mais lento até que as informações estejam disponíveis.
#### 5 Vês: volume, velocidade, variedade, veracidade, valor.

 ### Velocidade
 A primeira característica é a velocidade de coleta, organização e análise dos dados, eliminar os ruídos e trazer ordem e lógica a esse caos de informação e aleatoriedade.
 ### Volume
 O volume de informações coletadas pode ser colossal, essas soluções se destacam por sua robustez e confiabilidade, justamente por serem capazes de ingerir tamanha quantidade de informação em tempo real.
 ### Variedade
 As informações podem ser coletadas em dois diferentes tipos: os dados estruturados e os não estruturados. Enquanto o primeiro é uma ingestão organizada, como planilhas e arquivos CSV ou XLSX, o segundo consiste em dados nos mais variados formatos, como conteúdos de mídia como áudios, imagens, vídeos, textos e afins.
 ### Veracidade
 O objetivo da Big Data é encontrar ordem e lógica em meio a aleatoriedade de um grande banco de dados, por isso é importante minimizar esses ruídos, identificando excessos, redundâncias e equívocos, e auxiliando na limpeza e na confiabilidade do dataset final.
 ### Valor
 A Big Data é uma tecnologia que estimula a descoberta de insights e abordagens para a sua operação, encontrando valores essenciais para sustentação e manutenção de um negócio.
# Data Lake
É um ambiente no qual os dados estruturados e não estruturados, coletados de diferentes fontes, são armazenados em uma única plataforma (por exemplo, um cluster com ecossistema Hadoop), permitindo a integração dos dados e a geração de análises por meio de tecnologias de Big Data.
# Data Mining 
Consiste em um processo analítico projetado para explorar grandes quantidades de dados (tipicamente relacionados a negócios, mercado ou pesquisas científicas), na busca de padrões consistentes e/ou relacionamentos sistemático entre variáveis para, então, validá-los aplicando os padrões detectados a novos subconjuntos de dados.

Data Mining pesquisa, automaticamente, nesse montante de dados, anomalias e prováveis relacionamentos, encontrando possíveis problemas que não foram identificados anteriormente pelos usuários. Usando técnicas de estatística e inteligência artificial, além de reconhecimento de padrões, técnicas de estatística e inteligência artificial, reconhecimento de padrões e recuperação de informações.
# Hadoop
Ferramenta de processamento de grandes volumes de dados, através do processamento em lotes (grupo de dados).

- baixo custo.
- escalabilidade horizontal através da execução em centenas de clusters.

	#### HDFS
	Sistema de armazenamento que permite um grande volume de dados com tolerância a falhas.
	- Sistema master-slave, na qual um servidor principal é responsável por fazer o gerenciamento de metadados do sistema.
# MapReduce 
Modelo de programação para processamento de dados, permitindo que grandes volumes de dados sejam processados por meio de uma divisão de tarefas independentes, executadas em paralelo nos servidores de cluster. Baseado na programação funciona, é composto por duas fases: map e reduce. 

- trabalha em cima do **HDFS** para oferecer um processamento paralelo em um ambiente distribuído
- trabalho de forma distribuído e processamento paralelo
- transformar dados maiores em dados menores

 #### MAP
 A primeira a ser executada, processa um conjunto de dados de entrada, que deve ser obtidos no formato chave-valor. Dessa forma, cada tarefa map processa um par chave-valor, gerando como resultado uma saída no formato chave-valor.
 #### REDUCE
 No MapReduce, cada tarefa de redução recebe uma lista de valores associados a uma chave de mapeamento. Depois, esses pares chave-valor são agrupados e ordenados, e uma operação é realizada sobre eles para gerar o resultado final no formato chave-valor.

![[bd-mapreduce.png]]
# Processamento em Tempo Real

Diferentemente do processamento em lotes, o processamento em tempo real, os dados são processados assim que são gerados, criando a oportunidade de extrair informações imediatas sobre eles. Por exemplo, do processamento de dados oriundos de um sensor de temperatura

- O fluxo de processamento é contínuo.
- É chamado um para um, pois a requisição do processamento é individual para cada item de dado.
- Necessita de baixa latência (o tempo que um sistema demora para responder a um evento).
- Necessita de consistência (é comum que ocorra alguns problemas, tais como atraso, inversão de sequência e, até mesmo, a perda de alguma parte do dado, assim, a aplicação deve ser capaz de lidar com inconsistências)
- Necessita de alto disponibilidade.

![[bd-temporeal.png]]

Como o processamento deve ocorrer rapidamente, com ausência de gargalos de latência I/O, realizam-se normalmente somente pequenos cálculos, como uma simples contagem. Além disso, uma estratégia muito adotada é manter esses dados em memória até que sejam processados, sendo persistidos em um banco somente após essa etapa.
# Análise de Dados
Está relacionada com identificação de padrões, modelagem dos dados, detecção de grupos, classificação de dados, que utilizam técnicas de estatísticas, matemáticas, de aprendizado de máquina e de mineração de dados.
#### Limpeza 
 ##### Dados Ausentes
- Substituir o dado ausente com alguma constante, especificada pelo analista;
- Substituir o dado ausente pela média ou moda do campo; 
- Substituir o dado ausente com um valor gerado aleatoriamente a partir de uma distribuição observada; 
- Substituir o dado ausente a partir de valores baseados em outras características do registro;
 ##### Identificação de anomalias (outliers)
 São pontos de dados que divergem significativamente do resto dos dados, podendo atrapalhar no processo de análise.
 Soluções:
- Método de Derivação Padrão: Mede a dispersão do dataset, criando pontos em certos limites, assim valores acima da média são considerados outliers.
- Fator de Anomalias Locais (LOF): Compara os dados com a dispersão variável de seus vizinhos.
 ##### Transformação de dados
 - Transformação linear: é o calculo feito a partir do atributo mínimo e máximo dos dados, atribuindo um novo campo normalizado onde o valor mínimo será 0 e o máximo 1. 
 - Transformação de dados numéricos para categóricos; 
 - Transformação de dados categóricos para numéricos; 
 - Agregação de dados, por meio da combinação de dados de diferentes conjuntos em uma única fonte, de forma coerente; 
 - Criação de novos atributos.
 ##### Redução e sintetização dos dados
 Gera uma representação reduzida do conjunto de dados, porém mantendo os mesmos (ou próximo a isso) resultados da análise. Para isso, essa prática requer uma fase de seleção de atributos, identificando quais são irrelevantes para a análise e podem ser removidos da base.
 - Análise de Componentes Principais (Principal Component Analysis — PCA): detecta a correlação entre as variáveis. E caso seja detectado uma forte correlação entre elas, cria-se um conjunto menor de combinações lineares dessas variáveis, reduzindo assim a dimensionalidade dos dados.
 
# Visualização de Dados
É considerada uma das etapas finais do projeto de Big Data. Ela é realizada durante e após a etapa de análise de dados, por meio da análise exploratória e explanatória.

1. Aquisição — Estágio em que os dados para análise são capturados. Processo realizado na etapa de coleta dos dados.
2. Estruturação — Uma vez que os dados podem ser coletados de diversos formatos, esse estágio é importante para definir uma estrutura padrão para esses dados.
3. Filtragem — Além da estruturação, deve-se aplicar o estágio de filtragem dos dados, para remover dados incorretos, incompletos ou que não são interessantes para a análise.
4. Mineração — Pertencente ao estágio de análise de dados, esse estágio tem como objetivo a aplicação de técnicas para extrair informações dos dados.
5. Representação — Refere-se às atividades iniciais da representação visual dos dados. O objetivo nesse estágio é gerar o modelo visual básico dos dados, como foco principal na análise exploratória dos dados.
6. Refinamento — Esse estágio é essencial para aperfeiçoar a visualização dos dados analisados. É nesse momento que as técnicas gráficas são utilizadas para tornar a visualização mais eficiente.
7. Interação — Além do refinamento, a interação também melhora a visualização dos dados, permitindo inserir funcionalidades que ofereçam uma melhor experiência ao leitor.

```
O enunciado propõe uma avaliação sobre o conhecimento das tecnologias Hadoop e Spark. Para responder corretamente, é necessário entender o que cada uma dessas tecnologias representa no contexto de Big Data.

Hadoop é um framework de software que permite o processamento distribuído de grandes conjuntos de dados através de clusters de computadores. O Hadoop utiliza um modelo de armazenamento conhecido como Hadoop Distributed File System (HDFS), que é, de fato, hierárquico e permite o armazenamento de grandes volumes de dados em um ambiente distribuído.

Por outro lado, Spark é uma plataforma de computação em cluster que fornece uma API para programação distribuída. Spark é projetado para ser rápido e generalista, sendo capaz de realizar processamento em batch e também processamento em tempo real. O Spark SQL é um módulo dentro do Spark que permite a execução de SQL e também a leitura de dados de diversas fontes de dados, incluindo, mas não se limitando a, arquivos hierárquicos.

O erro na afirmação do enunciado está em descrever o Spark como uma "arquitetura de sistema operacional", o que não é verdade. Spark é uma plataforma de processamento e análise de dados e não tem relação com sistemas operacionais. Além disso, o Spark SQL permite consultar dados de maneira estruturada, não necessariamente "arquivos organizados de forma hierárquica" como sugere o enunciado, e sim, estruturas de dados como DataFrames e datasets que podem ser originados de diversas fontes de dados, incluindo bancos de dados relacionais, NoSQL, HDFS e até mesmo formatos como parquet e JSON.

Entender essa distinção é crucial, pois as características do Spark são bastante distintas das de um sistema operacional. O Spark é uma ferramenta na camada de processamento de dados, e não na camada de sistemas operacionais, que gerencia recursos de hardware e fornece serviços essenciais para os programas de computador.

Para compreender a questão é necessário conhecer as características dos frameworks **Apache Spark** e **Apache Hadoop**, bem como suas diferenças fundamentais no contexto de processamento de **Big Data**.

O **Spark** é conhecido por sua capacidade de processar grandes volumes de dados de maneira extremamente rápida, devido à sua arquitetura que realiza operações **em memória**. Utilizando o conceito de **Resilient Distributed Datasets (RDDs)**, o Spark minimiza o acesso ao disco, que é mais lento, optando por manter os dados em memória sempre que possível, o que acelera as operações de leitura e escrita.

Por outro lado, o **Hadoop** é tradicional por usar o modelo de processamento **MapReduce**, que realiza leituras e escritas no disco entre as etapas de map e reduce. Isso resulta em uma velocidade de processamento tipicamente inferior à do Spark para a maioria das cargas de trabalho. Embora o Hadoop seja altamente escalável e adequado para processamento em lote de dados, ele não pode superar a rapidez proporcionada pela computação em memória do Spark.

As afirmações de que o Hadoop seria mais rápido (Alternativa B), que o Spark seria adequado para cargas mais pesadas e o Hadoop para cargas leves (Alternativa C), que ambos utilizam as mesmas técnicas de processamento (Alternativa D) ou que o Hadoop é uma tecnologia mais recente (Alternativa E) estão incorretas.

A **alternativa correta (A)** descreve acuradamente a principal diferença entre Spark e Hadoop: o Spark é mais rápido devido ao seu processamento baseado em memória e uso de RDDs, ao passo que o Hadoop, embora seja robusto e escalável, tem uma abordagem de processamento baseado em disco, utilizando MapReduce.

**Análise Descritiva**: compreende a descrição das características dos **acontecimentos em tempo real,** de maneira a visualizar e entender o comportamento dos dados, de modo a auxiliar na tomada de decisões.

**Análise Preditiva**: esse item tem como objetivo prever **comportamentos futuros**, bem como as **tendências** dos dados, através da análise de informações anteriores. Desse modo, os gestores podem tomar decisões baseadas nos cenários futuros previstos por essa análise.

**Análise Prescritiva**: essa análise descreve os possíveis **efeitos e consequências** de ações que possam ser tomadas. Assim, é possível que possa ser realizada a melhor escolha para determinado cenário.

**Análise Diagnóstica**: neste caso, a análise procura entender as **relações de causa e efeito** entre situações, de modo a compreender os resultados obtidos em decorrência das ações tomadas.
``` 