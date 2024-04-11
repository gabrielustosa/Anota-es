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
 - Deduplicação: redução de dados, que remove duplicatas de um conjunto de dados, mantendo apenas uma única instância de cada dado. 
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

# Computação em Nuvem
