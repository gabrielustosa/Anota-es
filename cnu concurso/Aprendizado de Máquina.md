É uma área da inteligência artificial que se concentra no desenvolvimento de algoritmos e modelos estatísticos capazes de aprender a partir de dados, sem serem explicitamente programados. Ele utiliza métodos estatísticos para permitir que sistemas computacionais possam melhorar sua performance em tarefas específicas, através da análise e interpretação de grandes quantidades de dados.
### Tarefas Descritivas
As tarefas descritivas são aquelas que se preocupam em descrever e entender os dados, sem necessariamente fazer previsões ou tomar decisões com base neles.
##### Agrupamento (não supervisionado)
O objetivo do agrupamento é explorar e entender a estrutura dos dados, identificando grupos naturais e padrões que possam existir. Nesse caso, o agrupamento pode ser visto como uma técnica de análise exploratória de dados que ajuda a extrair informações úteis e relevantes sobre o conjunto de dados.

- Suporte e confiança são métricas utilizadas.
- Exemplos de algoritmos: K-means, Hierarchical Clustering, DBSCAN, Mean-Shift, K-Prototype.
- Também conhecido como Clusterização.
### Tarefas Preditivas
Tarefas preditivas são aquelas em que o objetivo é prever um resultado futuro com base em dados históricos.
##### Regressão (supervisionada)
A regressão é uma tarefa de aprendizado supervisionado que consiste em prever um valor numérico de saída a partir de um conjunto de valores de entrada. Por exemplo, podemos construir um modelo de regressão que, com base nas características de uma casa (tamanho, número de quartos, etc.), preveja seu preço de venda. Outro exemplo seria a previsão da demanda de um produto em um determinado período com base em dados históricos.

- Exemplos de algoritmos: Regressão linear, Árvores de decisão, Random Forest, Support Vector Regression (SVR)
##### Classificação (supervisionado)
 A classificação é uma tarefa de aprendizado supervisionado que consiste em classificar uma determinada instância em uma das classes pré-definidas. Por exemplo, podemos construir um modelo de classificação que, a partir das características de um paciente, determine se ele tem ou não uma determinada doença. Outro exemplo seria a classificação de e-mails como spam ou não spam, com base em suas características.

- Exemplos de algoritmos: Naive bayes, Árvores de decisão, Random Forest, Support Vector Machines (SVM), Redes neurais, C4.5, K-NN
### Hierarquia de Aprendizado
![[am-hier-ap.png]]

```ad-note
**Aprendizado Indutivo**: Efetuados apartir de exemplos externos (coletados)
**Aprendizado Supervisionado**: Exemplos estão rotulados (classe é conhecida)
**Aprendizado Não Supervisionado**: Exemplos não estão rotulados (classe é desconhecida)
**Classificação**: Os rótulos assumem valores discretos.
**Regressão**: Os rótulos assumem valores contínuos.
```

```ad-tip
###### Valores Discretos
São valores que têm um número limitado e específico de resultados possíveis. Por exemplo, o número de filhos em uma família é um valor discreto, pois só pode ser um número inteiro e não pode ter um valor fracionário.

###### Valores Contínuos
valores que podem ter uma ampla gama de valores possíveis dentro de um intervalo. Por exemplo, a altura de uma pessoa é um valor contínuo, pois pode ter um valor fracionário dentro de uma determinada faixa de valores.

```
### Aprendizado Supervisionado
Replica a nossa forma de extrair padrões de exemplos conhecidos e usar esse conhecimento para extrair um resultado repetível. Este processo de compreensão de uma combinação conhecida de entrada-saída é replicado no aprendizado de máquina usando aprendizado supervisionado. O modelo analisa e decifra a relação entre os dados de entrada e saída para aprender os padrões subjacentes. Os dados de entrada são chamados de variável independente (“X” maiúsculo), enquanto os dados de saída são chamados de variável dependente (“y” minúsculo). Por exemplo, com acesso ao preço de venda de outros carros semelhantes ("X"), o modelo de aprendizagem supervisionada pode trabalhar de trás para frente para determinar a relação entre o valor de um carro ("y") e as suas características ("X").

![[am-ap-sup.png]]

Ao construir um modelo de aprendizagem supervisionada, cada item (ou seja, carro, produto, cliente) deve ter valores de entrada e saída rotulados – conhecidos na ciência de dados como “conjunto de dados rotulados”.

- Exemplos de modelos: Regressão, Árvores de Decisão, K-NN, Redes Neurais e Máquinas de Vetores de Suporte.
### Aprendizado Não Supervisionado
Aprendizagem não supervisionada No caso de aprendizagem não supervisionada, as variáveis de saída não são rotuladas e as combinações de variáveis de entrada e saída não são conhecidas. Em vez disso, a aprendizagem não supervisionada concentra-se na análise das relações entre variáveis de entrada e na descoberta de padrões ocultos que podem ser extraídos para criar novos rótulos em relação a possíveis resultados. A vantagem da aprendizagem não supervisionada é que ela permite descobrir padrões nos dados que você desconhecia e fornece um trampolim para conduzir análises adicionais assim que novos grupos forem identificados. A desvantagem, porém, de usar a aprendizagem não supervisionada é que, como o conjunto de dados não é rotulado, não há observações de saída conhecidas para verificar e validar o modelo, e as previsões são, portanto, mais subjetivas do que aquelas provenientes da aprendizagem supervisionada.

- Exemplos de modelos: K-Means
### Aprendizado por Reforço
Terceira e mais avançada categoria de aprendizado de máquina. Ao contrário da aprendizagem supervisionada e não supervisionada, a aprendizagem por reforço constrói seu modelo de previsão obtendo feedback de tentativa e erro aleatórios e aproveitando insights de iterações anteriores. O objetivo da aprendizagem por reforço é atingir um objetivo específico (saída), testando aleatoriamente um grande número de combinações possíveis de entradas e avaliando seu desempenho. O aprendizado por reforço é semelhante, onde algoritmos são configurados para treinar o modelo com base no aprendizado contínuo. Um modelo padrão de aprendizagem por reforço possui critérios de desempenho mensuráveis onde os resultados são avaliados. No caso de veículos autônomos, evitar um acidente recebe uma pontuação positiva e, no caso do xadrez, evitar a derrota também recebe uma avaliação positiva.
### Matriz de Confusão
É uma tabela que permite a visualização do desempenho de um algoritmo de classificação.

![[am-matriz.png]]
#### Formulas
- VP: Verdadeiro Positivo.
- VN: Verdadeira Negativo.
- FP: Falso Positivo.
- FN: Falso Negativo.
##### Acurácia 
Avalia o percentual de acertos. 
$$
acurácia = \frac{VP + VN}{VP+FN+VN+FP}
$$
##### Precisão
Indica quanto das classificações positivas do modelo foram acertadas.
$$
precisão = \frac{VP}{VP + FP}
$$
##### Sensibilidade (Recall)
Indica quanto das amostras positivas existentes o modelo conseguiu classificar corretamente.
$$
sensibilidade = \frac{VP}{VP + FN}
$$
##### Especificidade 
Avalia a capacidade do método de detectar resultados negativos.
$$
especificidade = \frac{VN}{VN + FP}
$$
##### F-meansure (F-score ou score F1)
Fornece uma pontuação única que equilibra as preocupações de precisão e sensibilidade.
$$
f1 = 2 * \frac{precisão * sensiblidade}{precisão + sensibilidade}
$$
# Algoritmos 
#### Regressão Linear: Previsão Linear
Técnica simples para prever uma variável desconhecida usando os resultados que você conhece. Embora a regressão linear não seja um método infalível para prever tendências, a linha de tendência oferece um ponto de referência básico para prever eventos contínuos desconhecidos ou futuros. Por exemplo, usando a série de sitcom da TV Seinfeld como nossos dados, vamos começar traçando as duas variáveis a seguir, com o número da temporada como a coordenada x e o número de espectadores por temporada (em milhões) como a coordenada y.

![[am-reg-lin.png]]

A partir destes dados plotados em um gráfico de dispersão, podemos perceber uma tendência ascendente de espectadores começando na 4ª temporada e com pico na 9ª temporada. Usando regressão linear simples, podemos inserir uma linha reta para descrever a tendência linear ascendente do nosso pequeno conjunto de dados.

![[am-reg-lin-disp.png]]

O objetivo da regressão linear é dividir os dados de forma que minimize a distância entre o hiperplano e os valores observados. Isso significa que se você desenhasse uma linha perpendicular (uma linha reta em um ângulo de 90 graus) do hiperplano para cada ponto de dados no gráfico, a distância agregada de cada ponto seria igual à menor distância possível até o hiperplano. A distância entre a linha de melhor ajuste e os valores observados é chamada de resíduo ou erro, e quanto mais próximos esses valores estiverem do hiperplano, mais precisas serão as previsões do modelo.

![[am-reg-lin-erro.png]]
##### Inclinação
Uma parte importante da regressão linear é a inclinação, que pode ser convenientemente calculada referenciando o hiperplano. À medida que uma variável aumenta, a outra variável aumentará pelo valor médio indicado pelo hiperplano. Portanto, a inclinação é útil para formular previsões, como prever o número de telespectadores da temporada para uma potencial décima temporada de Seinfeld. Usando a inclinação, podemos inserir 10 como a coordenada x e encontrar o valor y correspondente, que neste caso é aproximadamente 40 milhões de telespectadores.
#### Regressão Logística: Previsão de Variáveis Categóricas
A regressão linear é uma ferramenta valiosa para entender as relações entre variáveis e prever resultados contínuos, como o valor total da conta em um restaurante ou o número de convidados. No entanto, quando precisamos prever algo categoricamente, como se um cliente é novo ou recorrente, precisamos de uma abordagem diferente.

Ao contrário da regressão linear, onde a variável dependente (y) é contínua, como o total da conta, na regressão logística lidamos com variáveis categóricas discretas. Aqui, não estamos buscando uma relação linear entre variáveis, mas sim uma maneira de classificar dados em categorias. A regressão logística, portanto, se torna a escolha adequada.

Apesar de ainda ser uma técnica de aprendizado supervisionado, a regressão logística produz previsões qualitativas em vez de quantitativas. Ela é especialmente útil para prever duas classes discretas, como grávida ou não grávida, ou outras categorias binárias.

A força da regressão logística reside na sua capacidade de classificação binária, o que a torna amplamente utilizada em diversos campos. Por exemplo, é aplicada na detecção de fraudes, diagnósticos médicos, detecção de emergências e até mesmo na identificação de e-mails de spam, distinguindo entre classes específicas, como spam e não spam. 

Utilizando a função sigmoide, a regressão logística estima a probabilidade de as variáveis independentes (X) influenciarem a ocorrência de uma variável dependente discreta (y), como "spam" ou "não spam".
#### K-NN: Classificação
Algoritmo supervisionado para a classificação popular, classificando novos pontos de dados com base em sua posição em pontos de dados próximos. Em muitos aspectos, k -NN é semelhante a um sistema de votação ou concurso de popularidade. Imagine que você é o aluno novo na escola e precisa saber como se vestir para se encaixar no resto da turma. No seu primeiro dia de aula, você vê seis dos nove alunos sentados mais próximos de você, com as mangas arregaçadas. Com base na maioria numérica e na proximidade, no dia seguinte você também toma a decisão de arregaçar as mangas. 

![[am-knn.png]]

Os pontos de dados foram classificados em duas classes, e um novo ponto de dados, cuja classe é desconhecida, é adicionado ao gráfico. Usando K-NN, podemos prever a categoria do novo ponto de dados com base em sua posição em relação aos pontos de dados existentes. Porém, primeiro precisamos definir “k” para determinar quantos pontos de dados queremos usar para classificar o novo ponto de dados. Se definirmos k como 3, k -NN analisa a posição do novo ponto de dados em relação aos três pontos de dados mais próximos (vizinhos). O resultado da seleção dos três vizinhos mais próximos retorna dois pontos de dados de Classe B e um ponto de dados de Classe A. Definida por k (3), a previsão do modelo para determinar a categoria do novo ponto de dados é Classe B, pois retorna dois dos três vizinhos mais próximos.

O número escolhido de vizinhos identificados, definido por k é crucial na determinação dos resultados. Na Figura, você pode ver que o resultado da classificação muda ao alterar k de "3" para "7". Portanto, é útil testar várias combinações de k para encontrar o melhor ajuste e evitar definir k muito baixo ou muito alto. Definir k muito baixo aumentará o viés e levará a classificações erradas, enquanto definir k muito alto tornará o processo computacionalmente mais caro. Definir k como um número ímpar também ajudará a eliminar a possibilidade de um impasse estatístico e um resultado inválido. Cinco é o número padrão de vizinhos para este algoritmo usando o Scikit-learn.

No que diz respeito ao tipo de dados a usar com k -NN, este algoritmo funciona melhor com variáveis contínuas. Ainda é possível usar variáveis categóricas binárias representadas como 0 e 1, mas é mais provável que os resultados sejam informados pelas divisões binárias relativas à dispersão entre outras variáveis

Embora o k-NN seja geralmente preciso e fácil de compreender, armazenar um conjunto de dados completo e calcular a distância entre cada novo ponto de dados e todos os pontos de dados existentes coloca uma carga pesada nos recursos de computação. Isso significa que o número de pontos de dados no conjunto de dados é proporcional ao tempo necessário para executar uma única previsão, o que pode levar a tempos de processamento mais lentos. Por esse motivo, o k-NN geralmente não é recomendado para analisar conjuntos de dados grandes.

Outra desvantagem é que pode ser desafiador aplicar o k-NN a dados de alta dimensionalidade com um grande número de características. Medir múltiplas distâncias entre pontos de dados em um espaço de alta dimensionalidade também é exigente em recursos computacionais e torna-se mais difícil realizar uma classificação precisa.
#### K-Means: Clustering (Agrupação)
Esse método de análise envolve agrupar ou clusterizar pontos de dados que compartilham atributos semelhantes usando aprendizado não supervisionado. Por exemplo, um negócio online, deseja examinar um segmento de clientes que compram na mesma época do ano e discernir quais fatores influenciam seu comportamento de compra. Ao entender um determinado cluster de clientes, eles podem então tomar decisões sobre quais produtos recomendar aos grupos de clientes usando promoções e ofertas personalizadas. 

Além da pesquisa de mercado, a clusterização também pode ser aplicada a outros cenários, incluindo reconhecimento de padrões, detecção de fraudes e processamento de imagens. Sendo um algoritmo de aprendizado não supervisionado, a clusterização k-means tenta dividir os dados em k grupos discretos e é altamente eficaz em descobrir novos padrões. Exemplos de agrupamentos potenciais incluem espécies de animais, clientes com características semelhantes e segmentação do mercado imobiliário.

![[am-k-means.png]]

O algoritmo de cluster k -means funciona primeiro dividindo os dados em um número k de clusters, com k representando o número de clusters que você deseja criar. Na Figura, podemos ver que os dados originais foram transformados em três clusters (k = 3).

Como o cluster k -means separa os pontos de dados? A primeira etapa é examinar os dados não agrupados e selecionar manualmente um centroide para cada cluster. Esse centroide forma então o epicentro de um cluster individual. Os centroides podem ser escolhidos aleatoriamente, o que significa que você pode nomear qualquer ponto de dados no gráfico de dispersão para atuar como centroide. No entanto, você pode economizar tempo selecionando centroides dispersos no gráfico de dispersão e não diretamente adjacentes uns aos outros. Em outras palavras, comece adivinhando onde você acha que os centroides de cada cluster podem estar posicionados. Os pontos dedados restantes no gráfico de dispersão são então atribuídos ao centroide mais próximo medindo a distância euclidiana.

![[am-k-means-euclide.png]]

Depois que todos os pontos de dados foram alocados a um centroide, o próximo passo é agregar o valor médio dos pontos de dados em cada cluster, o que pode ser feito calculando os valores médios de x e y dos pontos de dados contidos em cada cluster. Em seguida, pegue o valor médio dos pontos de dados em cada cluster e insira esses valores de x e y para atualizar as coordenadas do centroide. Isso provavelmente resultará em uma ou mais alterações na localização do(s) centroide(s). O número total de clusters, no entanto, permanece o mesmo, pois você não está criando novos clusters, mas sim atualizando sua posição no gráfico de dispersão. Como em uma dança das cadeiras, os pontos de dados restantes correm para o centroide mais próximo para formar k clusters.

Depois de atingir um estágio em que os pontos de dados não trocam mais de cluster após uma atualização nas coordenadas centroides, o algoritmo está completo e você tem seu conjunto final de clusters.

![[am-k-means-1.png]]

![[am-k-means-2.png]]

![[am-k-means-3.png]]

![[am-k-means-4.png]]

![[am-k-means-5.png]]

Para este exemplo, foram necessárias duas iterações para criar com sucesso nossos dois clusters. No entanto, a clusterização k-means nem sempre é capaz de identificar de forma confiável uma combinação final de clusters. Em tais casos, você precisará mudar de tática e utilizar outro algoritmo para formular seu modelo de classificação.
#### Máquinas de Vetor Suporte (SVM)
O SVM é usado principalmente como uma técnica de classificação para prever resultados categóricos. Também pode ser usado como técnica de classificação, sendo semelhante à regressão logística, pois é usado para filtrar dados em uma variável de destino binária ou multiclasse. Mas, como pode ser visto na figura abaixo, o SVM dá uma ênfase diferente à localização da linha limite de classificação.

![[am-svm.png]]

O gráfico de dispersão da figura acima é composto por 17 pontos de dados que são linearmente separáveis. Podemos ver que a fronteira de decisão logística (A) divide os pontos de dados em duas classes de forma a minimizar a distância entre todos os pontos de dados e a fronteira de decisão. A segunda linha, a fronteira SVM (B), também separa as duas classes, mas o faz a partir de uma posição de distância máxima entre si e as duas classes de pontos de dados. Você também notará uma zona cinza que denota a margem, que é a distância entre a fronteira de decisão e o ponto de dados mais próximo, multiplicada por dois. A margem é uma parte importante do SVM e é importante porque oferece suporte adicional para lidar com novos pontos de dados que podem infringir a fronteira de decisão (como é o caso da regressão logística). Para ilustrar este cenário, vamos considerar o mesmo gráfico de dispersão com a inclusão de um novo ponto de dados.

![[am-svm-1.png]]

O novo ponto de dados é um círculo, mas está localizado incorretamente no lado esquerdo do limite de decisão logística (A) (designado para estrelas). Enquanto a linha de decisão logística busca minimizar a distância entre a linha e os pontos de dados, a linha de decisão SVM visa maximizar a margem, ou seja, a distância entre a linha e os pontos de dados mais próximos de cada classe. Isso proporciona uma maior robustez ao modelo, pois cria uma "zona de segurança" em torno da linha de decisão, tornando-o menos sensível a ruídos e valores discrepantes.

O SVM também é útil para desvendar relacionamentos complexos e mitigar valores discrepantes e anomalias. Uma limitação da regressão logística padrão é que ela se esforça para ajustar valores discrepantes e anomalias (como visto na figura acima). O SVM, no entanto, é menos sensível a esses pontos de dados e, na verdade, minimiza o seu impacto na localização final da linha limite. Na Figura podemos ver que a Linha B (SVM) é menos sensível à estrela anômala do lado direito. O SVM pode, portanto, ser usado como um método para gerenciar dados variantes.

Os limites do SVM também podem ser modificados para ignorar casos classificados incorretamente nos dados de treinamento usando um hiperparâmetro chamado **C**. No aprendizado de máquina, você geralmente deseja generalizar padrões em vez de decodificar precisamente os dados de treinamento (que estão sujeitos a conter algum grau de ruído), pois incorrer em alguns erros no treinamento do modelo pode levar a um modelo que generaliza melhor em dados reais. Portanto, existe um compromisso no SVM entre uma margem ampla/mais erros e uma margem estreita/menos erros. O objetivo principal do seu modelo é encontrar um equilíbrio entre "não muito restrito" e "não muito solto", e, ao modificar o hiperparâmetro **C**, você pode regular até que ponto os casos classificados incorretamente (no lado errado da margem) são ignorados. Esse alto ajuste do hiperparâmetro **C** pode forçar o modelo a ajustar demais os dados de treinamento e, assim, classificar incorretamente novos pontos de dados.

Você pode combater o overfitting — quando o modelo funciona bem nos dados de treinamento, mas não em novos dados — reduzindo o valor de C, pois isso adiciona regularização ao modelo. Encontrar um valor ótimo de C geralmente é escolhido experimentalmente com base em tentativa e erro.

![[am-svm-margin.png]]

Por último, o tempo de processamento para treinar um modelo relativo à regressão logística e outros algoritmos de classificação pode ser uma desvantagem no uso do SVM. Em particular, o SVM não é recomendado para conjuntos de dados com baixa proporção de recursos por linha (baixo número de recursos em relação às linhas) devido a restrições de velocidade e desempenho. No entanto, o SVM é excelente em desembaraçar valores discrepantes de conjuntos de dados complexos de pequeno e médio porte e no gerenciamento de dados de alta dimensão.
#### Redes Neurais 
As redes neurais artificiais (RNA) são a porta de entrada para o aprendizado por reforço. Redes neurais artificiais, também conhecidas como redes neurais, são uma técnica popular de aprendizado de máquina para analisar dados por meio de uma rede de camadas de decisão. A nomenclatura desta técnica foi inspirada na semelhança estrutural do algoritmo com o cérebro humano. 

O cérebro, por exemplo, contém neurônios interconectados com dendritos que recebem informações. A partir dessas entradas, o neurônio produz uma saída de sinal elétrico do axônio e emite esses sinais através dos terminais do axônio para outros neurônios. Da mesma forma, as redes neurais artificiais consistem em funções de decisão interconectadas, conhecidas como nós, que interagem entre si por meio de arestas semelhantes a axônios.

Os nós de uma rede neural são separados em camadas e geralmente começam com uma base ampla. Esta primeira camada consiste em dados de entrada brutos (como valores numéricos, texto, pixels de imagem ou som) divididos em nós. Cada nó de entrada envia informações para a próxima camada de nós através das bordas da rede.

![[am-red-neu.png]]

Cada borda da rede possui um peso numérico que pode ser alterado com base na experiência. Se a soma das arestas conectadas satisfizer um limite definido, conhecido como função de ativação , isso ativará um neurônio na próxima camada. Se a soma das arestas conectadas não atingir o limite definido, a função de ativação falha, o que resulta em um arranjo tudo ou nada. Além disso, os pesos atribuídos a cada aresta são únicos, o que significa que os nós disparam de forma diferente, impedindo-os de produzir a mesma solução.

Usando o aprendizado supervisionado, a saída prevista do modelo é comparada com a saída real (que é conhecida como correta), e a diferença entre esses dois resultados é medida como o custo ou valor do custo. O objetivo do treinamento é reduzir o valor do custo até que o modelo a previsão corresponde aproximadamente à saída correta. Isto é conseguido ajustando gradativamente os pesos da rede até que o menor valor de custo possível seja obtido. Este processo específico de treinamento da rede neural é chamado de retropropagação
##### Dilema da Caixa Preta
Uma das desvantagens de um modelo baseado em redes neurais é o dilema da caixa preta. Embora a rede possa aproximar saídas precisas, traçar sua estrutura de decisão revela pouca ou nenhuma visão sobre como variáveis específicas influenciam sua decisão. Por exemplo, se usarmos uma rede neural para prever o resultado de uma campanha do Kickstarter (uma plataforma de financiamento online para projetos criativos), a rede pode analisar numerosas variáveis independentes, incluindo categoria da campanha, moeda, prazo e valor mínimo de contribuição, etc. No entanto, o modelo é incapaz de especificar a relação dessas variáveis independentes com a variável dependente de a campanha atingir sua meta de financiamento. Algoritmos como árvores de decisão e regressão linear, por outro lado, são transparentes, pois mostram as relações das variáveis com uma saída específica. Além disso, é possível que duas redes neurais com topologias e pesos diferentes produzam a mesma saída, o que torna ainda mais desafiador rastrear o impacto de variáveis específicas na saída final.
##### Estrutura 
Uma rede neural pode ser dividida em camadas de entrada, ocultas e de saída. Os dados são primeiramente recebidos pela camada de entrada, onde as características são detectadas. As camadas ocultas então analisam e processam as características de entrada, e o resultado final é mostrado como a camada de saída.

![[am-red-neu-est.png]]

As camadas intermediárias são consideradas ocultas porque, assim como a visão humana, elas processam secretamente objetos entre as camadas de entrada e saída. Quando nos deparamos com quatro linhas conectadas na forma de um quadrado, nossos olhos reconhecem instantaneamente essas quatro linhas como um quadrado. Não percebemos o processamento mental envolvido para registrar as quatro polilinhas (entrada) como um quadrado (saída).

Redes neurais funcionam de maneira semelhante, pois dividem os dados em camadas e processam as camadas ocultas para produzir uma saída final. À medida que mais camadas ocultas são adicionadas à rede, a capacidade do modelo de analisar padrões complexos também melhora. É por isso que modelos com um grande número de camadas são frequentemente referidos como aprendizado profundo para distinguir suas capacidades de processamento mais profundas e superiores.

Embora existam muitas técnicas para montar os nós de uma rede neural, o método mais simples é a rede feed-forward, onde os sinais fluem apenas em uma direção e não há loop na rede. A forma mais básica de rede neural feed-forward é o perceptron , que foi desenvolvido na década de 1950 pelo professor Frank Rosenblatt.

![[am-red-neu-perc.png]]

O perceptron foi projetado como uma função de decisão para receber entradas e produzir uma saída binária. Sua estrutura consiste em uma ou mais entradas, um processador e uma única saída. As entradas são alimentadas no processador (neurônio), processadas e uma saída é gerada.

Um perceptron suporta um dos dois possíveis resultados, "0" ou "1". Uma saída de "1" aciona a função de ativação, enquanto "0" não. Ao trabalhar com uma rede neural maior com camadas adicionais, a saída "1" pode ser configurada para passar a saída para a próxima camada. Por outro lado, "0" é configurado para ser ignorado e não é passado para a próxima camada para processamento.

Como uma técnica de aprendizado supervisionado, o perceptron constrói um modelo de previsão com base nestes cinco passos:

1. As entradas são alimentadas no processador.
2. O perceptron aplica pesos para estimar o valor dessas entradas.
3. O perceptron calcula o erro entre a estimativa e o valor real.
4. O perceptron ajusta seus pesos de acordo com o erro.
5. Estes quatro passos são repetidos até que você esteja satisfeito com a precisão do modelo. O modelo treinado pode então ser aplicado aos dados de teste.

Para ilustrar este processo, vamos dizer que temos um perceptron composto por duas entradas: 

**Entrada 1**: x1 = 24
**Entrada 2**: x2 = 16

Em seguida, adicionamos um peso aleatório a essas duas entradas e elas são enviadas ao neurônio para processamento:

![[am-red-neu-perc-1.png]]

**Pesos**
**Entrada 1**: 0,5
**Entrada 2**: -1

Agora, cada peso é multiplicado pelo seu valor de entrada.
**Entrada 1**: 0,5 * 24 =  12
**Entrada 2**: -1 * 16 = -16

Embora o perceptron produza uma saída binária (0 ou 1), existem muitas maneiras de configurar a função de ativação. Para este exemplo, vamos definir a função de ativação como ≥ 0. Isso significa que se a soma for um número positivo ou igual a zero, a saída será 1. Enquanto isso, se a soma for um número negativo, a saída será 0.

![[am-red-neu-perc-2.png]]

Por isso:
**Soma (Σ)**: 12 + (-16) = -4

Por ser um valor numérico menor que zero, o resultado produz “0” e não aciona a função de ativação do perceptron. Dado este erro, o perceptron precisa ajustar seus pesos em resposta.

Pesos atualizados:
**Entrada 1**: 24 * 0,5 = 12
**Entrada 2**: 16 * -0,5 = -8
**Soma (Σ)**: 12 + -16 = 4

Como resultado positivo, o perceptron agora produz “1” que aciona a função de ativação e, se estiver em uma rede maior, isso acionaria a próxima camada de análise.

Uma alternativa ao perceptron é o neurônio sigmoidal. Um neurônio sigmoidal é semelhante a um perceptron, mas a presença de uma função sigmoide, em vez de um filtro binário, agora aceita qualquer valor entre 0 e 1. Isso permite mais flexibilidade para absorver pequenas mudanças nos pesos das arestas sem acionar resultados inversos, já que a saída não é mais binária. Em outras palavras, a saída não será invertida devido a uma mudança mínima nos pesos das arestas ou no valor de entrada.

Embora mais flexível que um perceptron, um neurônio sigmoidal não é capaz de gerar valores negativos. Portanto, uma terceira opção é a função tangente hiperbólica.

Até agora só foi discutido sobre redes neurais básicas; para desenvolver uma rede neural mais avançada, podemos vincular neurônios sigmoides e outros classificadores para criar uma rede com um número maior de camadas ou combinar vários perceptrons para formar um perceptron multicamadas.
##### Perceptron Multicamada
O perceptron de múltiplas camadas (MLP), assim como outras técnicas de RNA, é um algoritmo para prever uma variável de destino categórica (classificação) ou contínua (regressão). Os perceptrons de múltiplas camadas são poderosos porque agregam múltiplos modelos em um modelo de previsão unificado, como demonstrado pelo modelo de classificação mostrado na figura abaixo.

![[am-red-neu-perc-mul.png]]

Neste exemplo, o modelo MLP é dividido em três camadas. A camada de entrada consiste em quatro nós representando uma característica de entrada usada para prever a preferência política de um usuário de mídia social: Idade, Cidade, Educação e Gênero. Em seguida, uma função é aplicada a cada variável de entrada para criar uma nova camada de nós chamada de camada intermediária ou oculta. Cada nó na camada oculta representa uma função, como uma função sigmoide, mas com seus próprios pesos/hiperparâmetros exclusivos. Isso significa que cada variável de entrada, na prática, é exposta a cinco funções diferentes. Simultaneamente, os nós da camada oculta são expostos a todas as quatro características.

A camada de saída final para este modelo consiste em dois resultados discretos: Partido Conservador ou Partido Democrata, que classifica a provável preferência política do usuário amostral. Observe que o número de nós em cada camada variará de acordo com o número de características de entrada e as variáveis alvo.

Em geral, perceptrons de múltiplas camadas são ideais para interpretar conjuntos de dados grandes e complexos sem restrições de tempo ou computacionais. Algoritmos menos intensivos em computação, como árvores de decisão e regressão logística, por exemplo, são mais eficientes para trabalhar com conjuntos de dados menores. Dado o alto número de hiperparâmetros, os perceptrons de múltiplas camadas também exigem mais tempo e esforço para ajustar do que outros algoritmos. Em relação ao tempo de processamento, um perceptron de múltiplas camadas leva mais tempo para ser executado do que a maioria das técnicas de aprendizado superficial, incluindo a regressão logística, mas geralmente é mais rápido do que o SVM.
##### Deep Learning
Para analisar padrões menos complexos, um perceptron de múltiplas camadas básico ou um algoritmo de classificação alternativo, como regressão logística e k-NN, podem ser colocados em prática. No entanto, à medida que os padrões nos dados se tornam mais complicados - especialmente na forma de um modelo com um alto número de entradas, como pixels de imagem - um modelo raso não é mais confiável ou capaz de análises sofisticadas, porque o modelo se torna exponencialmente complicado à medida que o número de entradas aumenta. Uma rede neural, com um grande número de camadas, no entanto, pode ser usada para interpretar um grande número de características de entrada e decompor padrões complexos em padrões mais simples, como mostrado na abaixo.

![[am-red-neu-deep.png]]

Essa rede neural profunda usa bordas para detectar diferentes características físicas para reconhecer rostos, como uma linha diagonal. Como blocos de construção, a rede combina os resultados dos nós para classificar a entrada como, digamos, um rosto humano ou um rosto de gato e depois avança para reconhecer características individuais

Isso é conhecido como Deep Learning . O que torna o Deep Learning “profundo” é o empilhamento de pelo menos 5 a 10 camadas de nós. O reconhecimento de objetos, usado por carros autônomos para reconhecer objetos como pedestres e outros veículos, usa mais de 150 camadas e é uma aplicação popular de aprendizagem profunda.
#### Árvores de Decisão: Classificação
Existe a ideia de que redes neurais artificiais podem ser usadas para resolver um espectro mais amplo de tarefas de aprendizagem do que outras técnicas levou alguns especialistas a aclamar a RNA como o algoritmo definitivo de aprendizado de máquina. Embora haja fortes argumentos para esse argumento, isso não quer dizer que a RNA se enquadre como um algoritmo mágico. Em certos casos, as redes neurais são insuficientes e as árvores de decisão são apresentadas como um contra-argumento popular.

A enorme quantidade de dados de entrada e recursos computacionais necessários para treinar uma rede neural é a primeira desvantagem de qualquer tentativa de resolver todos os problemas de aprendizado de máquina usando esta técnica. Aplicativos baseados em redes neurais, como o mecanismo de reconhecimento de imagens do Google, dependem de milhões de exemplos marcados para reconhecer classes de objetos simples (como cães), e nem todas as organizações têm os recursos disponíveis para alimentar e alimentar um modelo desse tamanho. A outra grande desvantagem das redes neurais é o dilema da caixa preta, que oculta a estrutura de decisão do modelo

As árvores de decisão, por outro lado, são transparentes e fáceis de interpretar. Eles trabalham com menos dados e consomem menos recursos computacionais. Esses benefícios tornam as árvores de decisão uma alternativa popular à implantação de uma rede neural para casos de uso menos complexos.

As árvores de decisão são usadas principalmente para resolver problemas de classificação, mas também podem ser usadas como modelo de regressão para prever resultados numéricos.

Árvores de decisão são usadas principalmente para resolver problemas de classificação, mas também podem ser usadas como um modelo de regressão para prever resultados numéricos. Árvores de classificação preveem resultados categóricos usando variáveis numéricas e categóricas como entrada, enquanto árvores de regressão preveem resultados numéricos usando variáveis numéricas e categóricas como entrada. As árvores de decisão podem ser aplicadas a uma ampla variedade de casos de uso; desde escolher um bolsista até prever vendas de e-commerce e selecionar o candidato a emprego certo.

##### Árvore de Regressão

![[am-arv-reg.png]]
##### Árvore de Classificação

![[am-arv-clas.png]]

Parte do apelo das árvores de decisão é que elas podem ser exibidas graficamente e são fáceis de explicar para não especialistas. Quando um cliente questiona por que não foi selecionado para um empréstimo residencial, por exemplo, você pode compartilhar a decisão árvore para mostrar o processo de tomada de decisão, o que não é possível usando uma técnica de caixa preta.
##### Estrutura
As árvores de decisão começam com um nó raiz que atua como ponto de partida e é seguido por divisões que produzem ramos, também conhecidos como arestas. Os ramos então se ligam a folhas, também conhecidas como nós, que formam pontos de decisão. Esse processo é repetido usando os pontos de dados coletados em cada nova folha. Uma categorização final é produzida quando uma folha não gera mais novos ramos e resulta no que é chamado de nó terminal.

Começando pelo nó raiz, as árvores de decisão analisam dados dividindo-os em subconjuntos, com um nó para cada valor da variável (ou seja, ensolarado, nublado, chuvoso). O objetivo é manter a árvore o menor possível. Isso é alcançado selecionando uma variável que divide os dados de forma otimizada em grupos homogêneos, minimizando assim o nível de entropia dos dados no próximo ramo.

```ad-info
##### Entropia 
Conceito matemático que explica a medida de variância nos dados entre diferentes classes.
```

Para entender como funciona esse processo, considere o seguinte exemplo.  Em termos simples, queremos que os dados em cada camada sejam mais homogêneos do que a partição anterior. Portanto, queremos escolher um algoritmo "ganancioso" que possa reduzir a entropia em cada camada da árvore. Um exemplo de algoritmo ganancioso é o Iterative Dichotomizer (ID3), inventado por J.R. Quinlan. Este é um dos três métodos de implementação de árvores de decisão desenvolvidos por Quinlan, daí o "3." Em cada camada, o ID3 identifica uma variável (convertida em uma pergunta binária) que produz a menor entropia na próxima camada.

![[am-arv-exemplo.png]]

Nesta tabela temos dez funcionários, três variáveis de entrada (KPIs excedidos, capacidade de liderança, idade <30) e uma variável de saída (outcome). Nosso objetivo é classificar se um funcionário será promovido ou não promovido com base na avaliação das três variáveis de entrada.

Vamos primeiro dividir os dados pela variável 1 (KPIs Excedidos):

- Seis funcionários promovidos que excederam seus KPIs (Sim).
- Quatro funcionários que não excederam seus KPIs e que não foram promovidos (Não). 

Esta variável produz dois grupos homogêneos na próxima camada.

![[am-arv-exemplo-1.png]]

Agora vamos tentar a variável 2 (Capacidade de Liderança), que produz:

- Dois funcionários promovidos com capacidades de liderança (Sim).
- Quatro funcionários promovidos sem capacidades de liderança (Não).
- Dois funcionários com capacidades de liderança que não foram promovidos (Sim).
- Dois funcionários sem capacidades de liderança que não foram promovidos (Não).

Esta variável produz dois grupos de pontos de dados mistos.

![[am-arv-exemplo-2.png]]

Por último, temos a variável 3 (Idade Menor que 30), que produz:

- Três funcionários promovidos com menos de trinta anos (Sim).
- Três funcionários promovidos com mais de trinta anos (Não).
- Quatro funcionários com menos de trinta anos que não foram promovidos (Sim). 

Esta variável produz um grupo homogêneo e um grupo misto de pontos de dados.

![[am-arv-exemplo-3.png]]

Das três variáveis, a variável 1 (Excedeu os KPIs) produz a melhor divisão com dois grupos perfeitamente homogêneos. A variável 3 produz o segundo melhor resultado, pois uma folha é homogênea. A variável 2 produz duas folhas que são heterogêneas. Portanto, a variável 1 seria selecionada como a primeira pergunta binária para dividir este conjunto de dados.

Seja o ID3 ou outro algoritmo, esse processo de dividir os dados em subpartições, conhecido como particionamento recursivo, é repetido até que um critério de parada seja alcançado. Um ponto de parada pode ser baseado em uma variedade de critérios, como:

- Quando todas as folhas contêm menos de 3-5 itens.
- Quando um ramo produz um resultado que coloca todos os itens em uma única folha binária.
##### Overfitting
Um importante ponto a ser observado das árvores de decisão é a sua susceptibilidade ao overfitting do modelo aos dados de treinamento. Com base nos padrões extraídos dos dados de treinamento, uma árvore de decisão é precisa ao analisar e decodificar a primeira rodada de dados. No entanto, a mesma árvore de decisão pode falhar ao classificar os dados de teste, pois pode haver regras que ela ainda não encontrou ou porque a divisão dos dados de treinamento/teste não foi representativa do conjunto de dados completo. Além disso, como as árvores de decisão são formadas ao dividir repetidamente pontos de dados em partições, uma pequena alteração na forma como os dados são divididos no topo ou meio da árvore poderia alterar drasticamente a previsão final e produzir uma árvore completamente diferente. O culpado, neste caso, é o nosso algoritmo ganancioso.

Começando com a primeira divisão dos dados, o algoritmo ganancioso escolhe uma variável que melhor divide os dados em grupos homogêneos. Como uma criança sentada na frente de uma caixa de cupcakes, o algoritmo ganancioso é inconsciente das repercussões futuras de suas ações a curto prazo. A variável usada para dividir os dados inicialmente não garante o modelo mais preciso no final da produção. Em vez disso, uma divisão menos eficaz no topo da árvore pode produzir um modelo mais preciso. Portanto, embora as árvores de decisão sejam altamente visuais e eficazes na classificação de um único conjunto de dados, elas também são inflexíveis e vulneráveis ao overfitting, especialmente para conjuntos de dados com alta variância de padrões.
##### Bagging
Em vez de buscar a divisão mais eficiente em cada rodada de particionamento recursivo, uma técnica alternativa é construir múltiplas árvores e combinar suas previsões. Um exemplo popular dessa técnica é o bagging, que envolve o crescimento de múltiplas árvores de decisão usando uma seleção aleatória de dados de entrada para cada árvore e combinando os resultados calculando a média da saída (para regressão) ou votação (para classificação).

Uma característica chave do ensacamento é a amostragem bootstrap. Para que múltiplas árvores de decisão gerem insights únicos, é necessário que haja um elemento de variação e aleatoriedade em cada modelo. Não faz muito sentido compilar cinco ou dez modelos idênticos. A amostragem Bootstrap supera esse problema extraindo uma variação aleatória dos dados a cada rodada e, no caso do bagging, diferentes variações dos dados de treinamento são executadas em cada árvore. Embora isso não elimine o problema do overfitting, os padrões dominantes no conjunto de dados aparecerão em um número maior de árvores e emergirão na classe ou previsão final. Como resultado, o bagging é um algoritmo eficaz para lidar com valores discrepantes e reduzir o grau de variação normalmente encontrado em uma única árvore de decisão.
##### Random Forests 
Uma técnica intimamente relacionada ao bagging são as Random Forests. Embora ambas as técnicas desenvolvam múltiplas árvores e utilizem amostragem bootstrap para randomizar os dados, as Random Forests limitam artificialmente a escolha de variáveis, limitando o número de variáveis consideradas para cada divisão. Em outras palavras, o algoritmo não pode considerar todas as **n** variáveis em cada partição.

No caso do bagging, as árvores muitas vezes parecem semelhantes porque utilizam a mesma variável no início da sua estrutura de decisão, numa tentativa de reduzir a entropia.

Isto significa que as previsões das árvores são altamente correlacionadas e mais próximas de uma única árvore de decisão no que diz respeito à variância geral. As Random Forests contornam esse problema, forçando cada divisão a considerar um subconjunto limitado de variáveis, o que dá a outras variáveis uma maior chance de seleção, e ao calcular a média de árvores únicas e não correlacionadas, a estrutura de decisão final é menos variável e muitas vezes mais confiável. Como o modelo é treinado usando um subconjunto de variáveis menores do que as realmente disponíveis, as Random Forests são consideradas uma técnica de aprendizagem pouco supervisionada.

![[am-arv-random-forest.png]]

Em geral, as Random Forests favorecem um elevado número de árvores (ou seja, mais de 100) para suavizar o impacto potencial de valores discrepantes, mas há uma taxa decrescente de eficácia à medida que mais árvores são adicionadas. Em um certo nível, novas árvores podem não acrescentar nenhuma melhoria significativa ao modelo, a não ser estender o tempo de processamento do modelo. Embora dependa do seu conjunto de dados, 100-150 árvores de decisão são um ponto de partida recomendado.

Embora as Random Forests sejam versáteis e funcionem bem na interpretação de padrões de dados complexos, outras técnicas, incluindo o aumento de gradiente, tendem a retornar uma precisão de previsão superior. Random Forests, porém, são rápidas de treinar e funcionam bem para obter um modelo de referência rápido
##### Boosting 
Boosting é outra família de algoritmos que se concentra na agregação de um grande conjunto de árvores de decisão. A ênfase dos algoritmos de reforço está na combinação de modelos “fracos” em um modelo “forte”. O termo “fraco” significa que o modelo inicial é um preditor ruim e talvez um pouco melhor do que uma estimativa aleatória. Enquanto isso, um modelo “forte” é considerado um preditor confiável do verdadeiro resultado desejado

O conceito de desenvolver indutores fortes a partir de indutores fracos é alcançado adicionando pesos às árvores com base em casos mal classificados na árvore anterior. Isso é semelhante a um professor que melhora o desempenho de sua turma, oferecendo
aulas extras aos alunos que tiveram mau desempenho nos exame mais recente.

```ad-note
##### Indutor
Indutor é responsável por analisar um conjunto de dados de entrada, geralmente rotulados com suas respectivas saídas esperadas, e "aprender" como produzir as saídas corretas a partir de novos dados de entrada.
```

Um dos algoritmos de boosting mais populares é o gradient boosting. Em vez de selecionar combinações de variáveis aleatoriamente, o gradient boosting seleciona variáveis que melhoram a precisão da previsão a cada nova árvore. As árvores de decisão são, portanto, cultivadas sequencialmente, pois cada árvore é criada usando informações derivadas da árvore anterior, e não de forma independente.

Erros ocorridos nos dados de treinamento são registrados e então aplicados à próxima rodada de dados de treinamento. A cada iteração, pesos são adicionados aos dados de treinamento com base nos resultados da iteração anterior. Uma ponderação mais alta é aplicada às instâncias que foram previstas incorretamente a partir dos dados de treinamento, e as instâncias que foram previstas corretamente recebem menos atenção.

Iterações anteriores que não apresentam bom desempenho e que talvez tenham dados classificados incorretamente podem ser posteriormente melhoradas em iterações posteriores. Este processo é repetido até que haja um baixo nível de erro. O resultado final é então obtido a partir de uma média ponderada do total de previsões derivadas de cada árvore de decisão.

![[am-arv-boosting.png]]

O Boosting também mitiga o problema do overfitting e faz isso usando menos árvores do que Random Forest. Embora adicionar mais árvores a uma Random Forest geralmente ajude a compensar o sobreajuste, o mesmo processo pode causar sobreajuste no caso de reforço e deve-se ter cuidado à medida que novas árvores são adicionadas. A tendência de impulsionar algoritmos para overfitting pode ser explicada por seu foco altamente sintonizado de aprendizagem e reiteração de erros anteriores.

Embora isso normalmente se traduza em previsões mais precisas – superiores às da maioria dos algoritmos – pode levar a resultados mistos no caso de dados ampliados por um grande número de valores discrepantes. Em geral, os modelos de aprendizado de máquina não devem se ajustar muito perto de casos atípicos, mas isso pode ser difícil para os algoritmos de reforço obedecerem, pois eles reagem constantemente a erros observados e isolados durante a produção. Para conjuntos de dados complexos com um grande número de valores discrepantes, as Random Forests podem ser uma abordagem alternativa preferida para o reforço.

A outra desvantagem principal do boosting é a lenta velocidade de processamento que acompanha o treinamento de um modelo de decisão sequencial. Como as árvores são treinadas sequencialmente, cada árvore deve esperar pela árvore anterior, limitando assim o escalabilidade de produção do modelo e especialmente à medida que mais árvores são adicionadas. Enquanto isso, uma Random Forest é treinada em paralelo, tornando seu treinamento mais rápido.

A desvantagem final, que se aplica tanto ao boosting quanto às Random Forests e ao bagging, é a perda da simplicidade visual e da facilidade de interpretação que acompanha o uso de uma única árvore de decisão. Quando você tem centenas de árvores de decisão, fica mais difícil visualizar e interpretar a estrutura geral de decisão.

Se, no entanto, você tiver tempo e recursos para treinar um modelo de reforço e um conjunto de dados com padrões consistentes, o modelo final pode valer extremamente a pena. Uma vez implantadas, as previsões do modelo de decisão treinado podem ser geradas com rapidez e precisão usando esse algoritmo e, fora o deep learning, o boosting é um dos algoritmos mais populares no aprendizado de máquina atualmente.