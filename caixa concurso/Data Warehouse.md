---
---
São grandes armazéns que oferecem capacidade de armazenamento de dados sumarizados sobretudo históricos que, quando acessados, fornecem informações de suporte à decisão, usando ferramentas adequadas de business inteligência (inteligência de negócio).

- É formado de uma grande diversidade de fontes.
- Construído para usuários finais para que possam compreendê-lo e usá-lo no contexto do seu negócio.
- É considerado um banco de dados baseado em assuntos ou negócios da aplicação.
- Não volátil (significa que os dados permanecem inalterados entre as cargas de dados).
- Variável em relação ao tempo, através da exclusão de dados que não são importantes no suporte ao processo de decisão.
- Integrado: os dados a serem carregados no data warehouse devem ser consistentes, ou seja, devem ser atribuídas convenções para a padronização de dados. 
- Data Warehouses podem ser implementados tanto em bancos de dados multidimensionais quanto em bancos de dados relacionais.
#### Estrutura 
A estrutura de um DW é composta por Metadados, sistema de origem (fonte dos dados), detalhes antigos ou dados históricos, detalhes correntes (onde ocorre a transformação operacional), dados levemente resumidos (aí se situam os data marts), dados altamente resumidos e um sistema de FrontEnd de visualização para o usuário final.

Passos para criação:
1. **Levantamento das necessidades**: devemos antes de tudo fazer o levantamento de todas as informações desejadas pelo usuário.
2. **Mapeamento dos dados**: nessa etapa fazemos o mapeamento dos dados, identificando a fonte e como chegar até eles.
3. **Construção da Área de Encenação**: após o mapeamento, construímos a estrutura chamada Área de Encenação, que se trata da área de transição dos dados do DW. Nessa área os dados são copiados e desacoplados dos sistemas de operação (OLTP) e recebem o devido tratamento para as futuras cargas nas tabelas de Fatos e Dimensões.
4. **Construção das Dimensões**: construímos nessa etapa a estrutura das Dimensões que farão parte do DW. Definimos também a historicidade que os dados irão possuir nas Dimensões.
5. **Construção do(s) Fato(s)**: construímos nessa etapa (após a construção das Dimensões) a(s) estrutura(s) da(s) Fato(s). Aqui é avaliado e definido a granularidade da informação que será armazenada em cada Fato.
6. **Definição do processo geral de carga**: após concluirmos as etapas anteriores, precisamos criar o motor para que tudo seja carregado, atualizado, orquestrado e processado de forma automática e ordenada.
7. **Criação dos metadados**: por fim, precisamos desenvolver toda a documentação dos metadados, que incluem o processo de construção e o dicionário de dados.

```ad-summary
##### Tipos de Dados
- **Dados de destino**: são os dados que são armazenados no data warehouse ou data mart.
- **Dados transacionais**: são os dados gerados pelas atividades de negócios, como vendas, compras e operações.
- **Dados de análise**: são os dados que são usados para fins analíticos, como relatórios, inteligência de negócios e machine learning.
- **Dados de staging**: são os dados intermediários entre o início e o fim do processo em big data. Eles são armazenados em um repositório separado, chamado de staging area, onde são submetidos a processos de limpeza, transformação e integração antes de serem carregados no data warehouse ou data mart.
- **Dados de origem**: são os dados que são coletados a partir de diferentes fontes, como sistemas legados, sensores e mídias sociais.
```
##### Arquitetura Controlada pela Fonte
Para a coleta de dados, onde as fontes de dados transmitem novas informações, seja **continuamente** (quando ocorre o processamento da transação), **periodicamente** (à noite, por exemplo).
##### Arquitetura Controlada pelo Destino
Onde o depósito de dados envia periodicamente solicitações para novos dados às fontes."
#### Modelagem 
 O processo de Modelagem Dimensional de Dados possui 4 passos/decisões:
1. Selecionar o processo de negócio (atividades operacionais executadas pela organização);
2. Declarar o grão (determina o que cada registro (linha na tabela) representa);
3. Identificar as dimensões (atributos descritivos (o que, quem, onde, quando, por que e como);
4. Identificar os fatos (medições resultantes da execução do processo de negócio).

 ### Tabela Fato
 É a tabela dominante, que fica no centro do modelo, é responsável por armazenar as medidas numéricas referentes à situação de negócio, devendo possuir a menor granularidade possível para permitir a maior flexibilização nas consultas. Cada uma das medidas é obtida a partir da união de todas as dimensões. Ela também armazena as chaves de junções para as tabelas de dimensões. Essas tabelas geralmente tem FKs que conectam as tabelas de dimensões, as métricas, também conhecidas como fatos, que são os valores a serem analisados.
   ##### Fatos (informações numéricas ou quantitativas da tabela)
   - Aditivos: Métricas que permitem operações matemáticas Exemplo: Número de carros vendidos.
   - Semi Aditivos: Só podem ser agregados com dimensões específicas. Exemplo: Média de temperatura.
   - Não aditivos: Não podem ser agregados com nenhuma dimensão. Exemplo: percentuais/margem de lucro de venda.
   - Derivada: Métrica calculada a partir de outros campos na fato. Exemplo: Valor da venda por quantidade.
   ##### Factless Fact Table
   Não possui nenhuma medida ela contém apenas chaves estrangeiras para tabelas dimensionais, sendo suficiente para responder a questões relevantes.
 ### Tabela Dimensão
 São conectadas a tabela fato. Nelas ficam armazenadas as descrições textuais descritivas das dimensões, fornecendo um maior nível de detalhamento para o negócio. Seu relacionamento é de um para muitos, o que possibilita um melhor aproveitamento do processamento das informações para as tabelas fato. Possuem diversos atributos de todos os tipos de dados, podendo armazenar as mais variadas informações.
   ##### Hierarquia Pai-Filho
   A mais comumente utilizada. Exemplo: ano, mês e dia; categoria, subcategoria e produto;
   ##### Dimensão Degenerada
   É uma dimensão que não mereceu ser uma dimensão e foi inserida como coluna na fato. 
   ##### Slowly Change Dimension (SCD)
   Retrata as dimensões que sofrem atualizações em seus campos e os classifica pelo tipo de mudança existente em cada uma delas.
   - SCD Tipo 0: Retenção do valor original, onde nenhuma alteração é feita no histórico, e os dados permanecem intactos.
   - SCD Tipo 1: Alteração que não armazena histórico na dimensão, ou seja, não é feito o versionamento do registro modificado. Tipo de atualização mais simples.
   - SCD Tipo 2: Técnica mais utilizada para atualizações de dimensões. Nesse tipo de SCD é adicionado um novo registro com as mudanças, preservando sempre os dados anteriores. 
   - SCD Tipo 3: Permite manter as modificações no mesmo registro. Essa técnica funciona com a adição de uma nova coluna na tabela de dimensão, onde é armazenada a atualização, mantendo na antiga coluna o valor anterior.
 ## Modelo Estrela
 Estrutura básica de um modelo de dados multidimensional, organizada por assuntos. Ele é composto por uma tabela central denominada fato e um conjunto de tabelas menores denominadas dimensões, as quais ficam dispostas ao redor desta tabela central formando uma estrela. O centro da estrela é o fato e ao seu redor estão dispostas as dimensões que participam deste fato. O relacionamento entre a tabela central e as tabelas dimensões é uma simples ligação entre as entidades em um relacionamento de um para muitos (ONE TO MANY). Não é a melhor alternativa para lidar com hierarquias.
 
![[dw-star.jpeg]]
 
```ad-tip
###### Medida
No design de esquema em estrela uma medida é uma coluna de tabela de fatos que armazena valores a serem resumidos.
```

 ## Modelo Floco de Neve
 Tem dimensões separadas em hierarquias, uma tabela para cada nível. A hierarquia é o resultado da decomposição de uma ou mais dimensões que possuem hierarquia entre seus membros, ou seja relacionamentos muitos para um entre os membros de uma dimensão, formando relacionamentos entre tabelas dimensões. Sua utilização preserva os meios de armazenamento, como ocorre em um modelo normalizado, desta forma, ele evita a redundância de valores textuais em uma tabela.
 ![[dw-snow.png]]
O Modelo Estrela e Modelo Floco de Neve, ambos possuem uma tabela central, denominada fato e disposta ao seu redor as tabelas dimensões. É possível notar uma grande semelhança entre ambos, porém no modelo Estrela não ocorre a normalização dos dados contidos nas tabelas dimensões ao contrário do que ocorre no modelo Floco de Neve, onde as tabelas fatos são normalizadas e possuem hierarquia entre suas tabelas.

```ad-warning
- Floco de Neves -> Normalizado
- Estrela -> Não Normalizado
```
#### Granularidade
Processo de definição do nível de detalhamento das informações a serem armazenadas e recuperadas no data warehouse. Quanto mais detalhe, mais baixo o nível de granularidade (mais “grãos” de dados); quanto menos detalhe, mais alto o nível de granularidade (menos “grãos” de dados)

![](dw-granularidade.png)
##### Nível Duplo de Granularidade 
Existem basicamente duas camadas no data warehouse:
- Na camada de dados resumidos ficam os dados que fluem do armazenamento operacional e são resumidos na forma de campos apropriados para a utilização de analistas e gerentes. 
- Na segunda camada, nível de dados históricos, ficam todos os detalhes vindos do ambiente operacional. Há uma verdadeira montanha de dados nesse nível e, portanto, faz sentido armazenar dados em meios alternativos (fitas magnéticas, por exemplo).
#### Processo ETL
 ##### Extração
 As fontes de extração podem vir de várias origens, de diversos formatos e fontes, que são extraídos para uma área de preparação temporária.
 ##### Transformação
 É a padronização dos dados para um formato uniforme, normalmente sugerido pelo próprio usuário para que possam ser “Carregados” no repositório de dados. Pode envolver os seguintes tipos de alterações de dados: 
  ## Simples
   ## Limpeza de dados
   A limpeza de dados remove erros e mapeia os dados de origem para o formato de dados de destino unificado.
   ## Eliminação de duplicação de dados
   A eliminação de duplicação de dados na limpeza de dados identifica e remove registros duplicados.
   ## Revisão de formato de dados
   A revisão de formato converte dados, como conjuntos de caracteres, unidades de medida e valores de data e horário, para um formato consistente.
  ### Avançada
   ### Derivação
   A derivação aplica regras de negócios aos seus dados para calcular novos valores com base em valores existentes.
   ### Junção
   Na preparação de dados, a junção vincula dados semelhantes de diferentes fontes de dados.
   ### Separação
   Divide uma coluna ou um atributo de dados em diversas colunas no sistema de destino.
   ### Resumo
   O resumo melhora a qualidade dos dados ao reduzir um grande número de valores de dados em um conjunto de dados menor.
   ### Encriptação
   Protege dados confidenciais para cumprir as leis de dados ou a privacidade de dados adicionando encriptação antes que os dados sejam transmitidos para o banco de dados de destino.
   ### Discretização 
   Transforma dados contínuos em um número finito de intervalos, o que facilita a análise em determinados casos.
 ##### Carga
 Ferramentas de extração, transformação e carregamento (ETL) movem os dados transformados da área de preparação para o data warehouse de destino. Esse processo deve ser automatizado, bem definido, contínuo e orientado por lotes.

![[dw-etl.png]]

```ad-tip
##### Surrogate Key
É a chave utilizadas nas dimensões para se ligar a tabela fato. Em resumo, a “Surrogate Key” é uma “Primary Key” localizada na dimensão.
- chave artificial
- auto incremental
```
#### OLTP
Realizado em operações diárias, lidando com transações individuais em tempo real, como inserções, atualizações e exclusões.

- orientado por aplicação, 
- simples e rápido.
- baixo nível de granularidade.
- aliados com SPT (Sistemas de Processamento de Transações)
#### OLAP
Tecnologia de suporta a decisões de diferentes pontos de vista, tal como a vista de um cubo, que são utilizadas no conceito chamado ad hoc.

Por exemplo: Ele arrasta a coluna do valor da venda. Depois, ele quer ver essas vendas cruzadas com produto, depois com a forma de pagamento, com região, com mês, e com o que mais ele precisar para obter o insight essencial para o negócio.

- leituras rápidas
- acesso demasiado  ao histórico
- dados sumarizados que vão direto ao ponto
- envolve consultas complexas

 ##### Roll-Up
 Os dados são resumidos com uma generalização crescente. (dia, mês, ano) - maior granularidade.
 ##### Drill-Down
 Níveis crescentes de detalhes são revelados, processo de desagregação. (ano, mês, dia) - menor granularidade.
 ##### Drill Across
 Pula de um nível intermediário dentro da dimensão; Por exemplo em uma dimensão formada por ano, semestre, mês e dia, ocorre o Drill Across quando se passa de ano direto para mês.
 ##### Drill Through 
 Quando se passa de uma informação contida em uma dimensão para outra dimensão; Por exemplo quando se analisa uma dimensão denominada tempo e passa a analisar uma chamada região.
 ##### Pìvot
 Rotação do cubo.
 ##### Slice
 Seleciona dados de uma única dimensão; Por exemplo: para visualizar os dados apenas de janeiro de 2013, realiza-se um slice na dimensão tempo.
 ##### Dice
 Extrair um subcubo do cubo original executando uma operação de seleção de uma ou mais dimensões.  
# Data Mart
É uma escala menor, que abrange um setor de uma determinada unidade de negócio, utilizando o modelo dimensional, assim como outros elementos do data warehouse.

Pode ser construído independentemente do data warehouse, segundo uma necessidade departamental da organização, ou seja, reunindo dados que geram informações específicas de um setor da empresa, essa arquitetura é conhecida como "bottom-up", constroem primeiro os data marts que posteriormente alimentarão os data warehouses. 

Por ser um data warehouse “departamental” o data mart, por princípio, não deve possuir um volume de dados muito grande, portanto é preciso assumir que o nível de granularidade alta.
