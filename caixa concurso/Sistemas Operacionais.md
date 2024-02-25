# Base do SO
#### Núcleo (Kernel)
Coração do SO, responsável pela gerenciamento recursos de memória, energia, arquivos, tarefas e proteção. Ele também implementa abstrações utilizada por aplicativos. 

```ad-info
O Software que opera em modo núcleo (supervisor)
```

```ad-info
Geralmente, na arquitetura monolítica ele é executado como único programa ativo no modelo núcleo.
```
#### Boot Code
Responsável pela inicialização do hardware, reconhece dispositivos, testa-os e configura. Carrega o **núcleo** do **SO** em memória para iniciar sua execução.
#### Drivers 
São módulos de código específicos para acessar dispositivos físicos. Compilados para ser acoplado ao **SO**.
# Estruturas de SO
#### Sistema Monolíticos 
É executado como um único programa em modo núcleo. O sistema operacional é escrito como uma coleção de rotinas, ligadas a um único grande programa binário executável. Essas rotinas podem chamar outras, no entanto, para evitar complicações é utilizada uma abordagem de compilação de todas as rotinas individuais e então junta-las em um único arquivo executável usando o ligador (linker) do sistema.

Estrutura básica:
1. Um programa principal que invoca a rotina de serviço requisitada. 
2. Um conjunto de rotinas de serviço que executam as chamadas de sistema. 
3. Um conjunto de rotinas utilitárias que ajudam as rotinas de serviço.
#### Sistema em Camadas
Divide o sistema operacional em sistemas sobrepostos. Cada módulo oferece um conjunto de funções que pode ser usado por outros módulos.

![[so-camadas.png]]
# Processo
Uma abstração de uma instância de um programa em execução. São úteis para a organização de um sistema de processo paralelo (pseudo-async).

 ## Estados de um processo
1. Execução (está sendo executado pela CPU naquele momento)
2. Pronto (executável ou parado temporariamente para deixar outro processo prioritário ser executado)
3. Bloqueado ou Wait (incapaz de ser executado, esperando outro evento acontecer)

 ## Dentro de um processo 
1. Conjunto de instruções (Programa)
2. Espaçamento de endereçamento.
3. Contexto do hardware (registradores, PC, ponteiros)
4. Contexto de software (lista de arquivos abertos, variáveis)
### Ciclo de execução de processos

![[so-estados.png]]

```ad-note
A transição 2 ocorre quando o escalonador decide que o processo em andamento foi executado por tempo suficiente, e é o momento de deixar outro processo ter algum tempo de CPU.

A transição 3 ocorre quando todos os outros processos tiveram sua parcela justa e está na hora de o primeiro processo chegar à CPU para ser executado novamente.

```
#### Finalização de Processos
 ##### Término normal (voluntário)
 A tarefa a ser executada é finalizada;
 ##### Término com erro (voluntário)
 O processo sendo executado não pode ser finalizado 
 - o arquivo "filename.c" não existe;
 ##### Término com erro fatal (involuntário)
 Erro causado por algum erro no programa (bug) 
  - Divisão por 0 (zero);
  - Referência à memória inexistente ou não pertencente ao processo; 
  - Execução de uma instrução ilegal;
 ##### Término causado por algum outro processo (involuntário):
  Kill (UNIX) e TerminateProcess (Windows);
#### Comunicação 
A comunicação entre processos (**IPC**) ocorre de diversas formas como: compartilhamento de memória, pipes e socket. Essa comunicação deve ocorrer de maneira independente. 

 ##### Race Conditions
 Quando 2 ou mais processos acessam ou modificam um recurso compartilhando causando falhas de sincronização.
 ##### Região Crítica 
 Parte do programa onde a memória compartilhada é acessada, uma região se torna crítica quando um processo, em seu momento de execução, está utilizando uma parte da memória.
 Quatro condições para regiões críticas para evitar condições de corrida:
 1. Dois processos jamais podem estar simultaneamente dentro de suas regiões críticas
 2. Nenhuma suposição pode ser feita a respeito de velocidades ou do número de CPUs.
 3. Nenhum processo executando fora de sua região crítica pode bloquear qualquer processo.
 4. Nenhum processo deve ser obrigado a esperar eternamente para entrar em sua região crítica.
 
 ##### Exclusão mútua
 Técnicas usada em programação  para evitar que  processos  tenham acesso simultaneamente a um recurso compartilhado.
  ## Busy Wait (Espera ocupada)
  Consiste na constante checagem por algum valor para saber se a região crítica está sendo utilizada. 
  - requer muito processamento da CPU
  ## Sleep/Wake up (Dormir/Acordar)
  utilizando funções de "acordar" ou "despertar" processos a depender se condições são atendidas.
  -  Surge como solução a processo **busy wait**, não utilizando um loop infinito para checagem de estado.
 ##  Semáforos 
  Controla o uso de acesso de determinado recurso, coordenados por uma ação ação atômica indivisível.
- Binário: incrementa valores para alterar o estado do processo, no qual é representado por **down (0)** ou **up (1)**.
- Geral (Contadores): São utilizado para controlar um número de acessos pré-definido.
 ##  Mutexes
  Uma versão simplificada de semáforos, utilizada para exclusão mútua.
 * é uma variável que pode estar definida com travada (1) e destravada (0). 
 * bastante utilizada em processos concorrentes 
 ##  Monitor
  Estruturas de sincronização de alto nível que garantem a exclusão mútua e a sincronização de processos. 
* Somente pode estar ativo um processo dentro do monitor em um mesmo instante

 ##### DeadLock
 Quando 2 ou mais programas estão tentando acessar um programa ao mesmo tempo resultando na bloqueamento dos 2 programas.
 **TODAS** as condições para o DeadLock ocorrer: 
	 - **Exclusão mútua**:  cada recurso só pode estar alocado a um único processo em um determinado instante;
	 - **Posse e Espera**: um processo, além dos recursos já alocado, pode estar esperando por outros recursos;
	 - **Não-Preempção**: um recurso não pode ser liberado de um processo só porque outros processos desejam o mesmo recurso;
	 - **Espera circular**: um processo pode ter de esperar por um recurso alocado a outro processo e vice-versa.
  #### Algoritmo do Banqueiro
  O algoritmo do banqueiro é um algoritmo usado para evitar impasses (deadlocks) em sistemas computacionais, requer que cada processo declare o máximo de recursos que pode precisar antecipadamente. 
  #### Algoritmo do Avestruz
  Uma estratégia de ignorar com base no fato de que eles podem ser extremamente raros.

```ad-info
#### Tempo de Turnaround
Conta o tempo total, desde a submissão do processo até a sua conclusão.
```
#### Escalonamento
Responsável por tomar as decisões sobre quais processos devem ser executados, dividindo tempo justo de CPU para diferentes processos de forma a maximizar a utilização da CPU, fornecendo um tempo de resposta razoável.

 ## Escalonador Preemptivo
 Escolhe um processo e o deixa executar por no máximo um certo tempo fixado. Se ele ainda estiver executando ao fim do intervalo de tempo, ele é suspenso e o escalonador escolhe outro processo para executar (se algum estiver disponível). 
 ## Escalonador Não-Preemptivo
 Escolhe um processo para ser executado e então o deixa ser executado até que ele seja bloqueado (seja em E/S ou esperando por outro processo), ou libera voluntariamente a CPU.

 ##### Escalonador de longo prazo 
 É o responsável de controlar o grau de multiprogramação do sistema.
 - Controla o número de processos que serão executados “ao mesmo tempo”. 
 - Admite novos trabalhos no sistema, convertendo estes em processos.
 ##### Escalonador de médio prazo (swapping)
 É o responsável de escolher os processos que serão removidos total ou parcialmente da memória para serem levados ao disco (suspensos). 
 ##### Escalonador de curto prazo (despachante)
 Responsável por alocar à CPU os processos alocados em memória.

![[so-escalonamento.png]]
 
```ad-info
#### Objetivos de escalonadores em diferentes sistemas
- **Lote**: Prioriza a vazão (throughput), utilização de **CPU** e tempo de retorno (o tempo médio do momento em que a tarefa em lote é submetida até o momento em que ela é concluída).
- **Iterativos**: Prioriza o tempo de resposta e a proporcionalidade (satisfazer às expectativas dos usuários).
- **Tempo Real**: Prioriza o cumprimento de prazos, evita a perda de dados e garante a previsibilidade.
```
##### Algoritmos de Escalonadores
 ## Primeiro a Chegar, Primeiro a Ser Servido (first-come, first-served)
 Algoritmo não-preemptivo, a CPU é atribuída aos processos na ordem em que a requisitam.
 ## Tarefa mais curta primeiro (shortest job first)
 Algoritmo não-preemptivo, presume que os tempos de execução são conhecidos antecipadamente.
 ## Chaveamento Circular (round-robin)
 Para cada processo é designado um intervalo, chamado de seu quantum, durante o qual ele é deixado executar. Se o processo ainda está executando ao fim do quantum, a CPU sofrerá uma preempção e receberá outro processo.
 - Estabelecer o quantum curto demais provoca muitos chaveamentos de processos e reduz a eficiência da CPU.
 - Estabelecer o quantum longo demais pode provocar uma resposta ruim a solicitações interativas curtas.
-  O termo **"chaveamento"**  refere-se à mudança ou troca de processamento por parte da **CPU**
 ## Por Prioridades
 A cada processo é designada uma prioridade, e o processo executável com a prioridade mais alta é autorizado a executar. Para evitar que processos de prioridade mais alta executem indefinidamente, o escalonador  talvez diminua a prioridade do processo que está sendo executado em cada tique do relógio
 ## Por Loteria
 Dar bilhetes de loteria aos processos para vários recursos do sistema, como o tempo da CPU. Sempre que uma decisão de escalonamento tiver de ser feita, um bilhete de loteria será escolhido ao acaso, e o processo com o bilhete fica com o recurso. Processos mais importantes podem receber bilhetes extras, para aumentar a chance de vencer

 ##### Inanição (starving)
 Devido a má gerência de escalonamento é possível que processos sofram de inanição, ou seja, mesmo estejam prontos para ser executados podem não tem acesso ao recurso desejado.
# Gerência de Memória
O principal objetivo é fornecer uma maneira eficiente e segura para que os processos em um sistema computacional acessem e compartilhem a memória.

```ad-tip
##### Multiprogramação
Técnica  onde vários programas são carregados na memória simultaneamente.
```
##### O DMA (Direct Memory Access) 
É uma técnica de transferência de dados que permite que dispositivos periféricos acessem diretamente a memória do sistema.
#### MMU (Memory Manager Unit)
O acesso do processador a memória é controlador pelo sistema operacional através do controlador denominado **MMU** que é o responsável por analisar cada endereço acessado pelo processador, validar e efetuar conversões necessárias entres os endereços lógicos e físicos garantindo o desempenho máximo.

![[so-mmu.png]]

 ##### Memória Lógica 
 É aquela que o processo enxerga, o processo é capaz de acessar.
 - Referências de um módulo ou programa em execução.
 ##### Memória Física
 É aquela implementada pelos circuitos integrados de memória, pela eletrônica do computador (memória real).
- Cache, Memória Principal, Memória Secundária.
```mermaid
flowchart LR

CPU --> |endereço lógico| G["GERENCIADOR DE MEMÓRIA"] --> |endereço físico| MEMÓRIA
```
 ##### Registrador Intermediário (buffer)
 Estrutura de dados assíncrona compartilhada que permite a comunicação entre processos; Ele armazena temporariamente dados de entrada ou saída na tentativa de ajustar melhor as velocidades de dois dispositivos
 - Leitura: recebe a palavra da memória 
 - Escrita: contém a informação a ser gravada na memória
```mermaid
flowchart LR

PRODUTOR --> BUFFER --> CONSUMIDOR
```
 ##### Pooling 
 A criação de um espaço de alocamento de memória temporário para o acesso de outros processos.   
#### Partições
O sistema de gestão de memória é baseado na divisão da memória em um certo número de regiões ou partições.

- Cada uma das partições pode conter um processo em execução.
- Quando um processo finaliza sua execução libera sua partição, a qual pode ser utilizada por outro processo da fila de trabalhos. 

 ##### Fixas
 A memória é divida em um número fixo de partições pelo gerenciador e o restante da memória é deixada livre para outros processos
- Pode existir um desperdício de memória na qual os processos não usaram toda a memória alocada (fragmentação interna).
 ##### Variáveis
 A memória é variável a depender da necessidade de cada processo. 
- Permite o uso mais eficiente da memória
- Pode gerar a fragmentação de disco, pequenos espaços de memória vazios que não podem ser realocados (fragmentação externa)
#### Realocação
##### Realocação Dinâmica
Mapeia o espaço de endereçamento de cada processo em uma parte diferente da memória física de uma maneira simples.
- o espaço de memória e reservado durante a **execução** do programa.
##### Relocação estática
 Se conhece/estabelece em que posição de memória se situará o processo, por tanto, o código gerado contém o endereço físico.
- Endereços lógicos se igualam com os físicos.
- o espaço de memória é definido durante o processo de **compilação**
#### Algoritmos de Alocação de Memória 
 ##### First-Fit
 O primeiro segmento livre com tamanho suficiente para alocar o arquivo é selecionado. A busca na lista é sequencial, sendo interrompida tão logo se encontre um segmento adequado.
 - Mais rápido e o melhor.
 - Ele gera no inicio da memória pequenas partições livres que necessitam ser pesquisadas a cada passo subsequente do First-Fit.
 ##### Next-Fit
 Parecido com o First-Fit, porém inicia a procura a partir do local onde foi feito a ultima locação e escolhe o bloco que é grande o suficiente para o processo a ser alocado;
 - Frequentemente aloca blocos livres no fim da memória.
 - Performance inferior ao First-Fit.
 ##### Best-Fit
 Seleciona o menor segmento livre disponível com tamanho suficiente para armazenar o arquivo. A busca em toda a lista se faz necessária para a seleção do segmento, a não ser que a lista esteja ordenada por tamanho.
 - Tem a pior performance.
 - Procura pelo menor bloco que satisfaça o requisito.
 ##### Worst-Fit
 Maior segmento é alocado e a busca por toda a lista se faz necessária, a menos que exista uma ordenação por tamanho.
 - Escolhe Maior espaço possível;
 - Tempo de busca grande;
 ##### Quick-Fit
 Mantém listas em separado para alguns dos tamanhos mais comuns solicitados. Ele pode ter uma tabela com n entradas, na qual a primeira é um ponteiro para o início de uma lista espaços livres.
 - Tem as mesmas desvantagens de todos os esquemas que ordenam por tamanho do espaço livre.
#### Memória virtual
Cada programa tem seu espaço de endereçamento, divido em blocos chamados de páginas. Cada página é uma série contígua de endereços. Estas são mapeadas na memória física, porém não necessitam estar carregadas na memória física, podem estar alocadas em um disco rígido, sendo trabalho do sistema operacional carrega-las na memória física se necessário.

A memória virtual pode ser implementada dividindo o espaço do endereço virtual em páginas e mapeando cada uma delas em algum quadro de página da memória física ou não as mapeando (temporariamente). Desse modo, ela diz respeito basicamente à abstração criada pelo sistema operacional e como essa abstração é gerenciada.

 ##### Swapping
 Técnica utilizada para poupar espaço na memória física (RAM), movendo processo temporariamente para um disco rígido. Quando o processo é movido ele é salvo em um arquivo chamado swap que depois é utilizado para mover o processo novamente para memória.
 ##### Paginação
 técnica de endereçamento de memória que utiliza o conceito de memória virtual, em que o espaço de endereçamento virtual é dividido em pequenos blocos iguais conhecidos como páginas virtuais.
 ##### Quadros
 As  páginas em memória virtual  correspondentes na memória física são chamadas de quadros de página, ou página física. As páginas e os quadros de página são geralmente do mesmo tamanho fixo.
 ##### Tabela de Páginas
 Registra em que bloco de memória cada página está carregada. As tabelas de páginas são mantidas pelo S.O. Se uma página é acessada mas não está na memória, o **S.O.** consulta a tabela de blocos livres, aloca a página no bloco selecionado e atualiza a tabela de páginas. Em uma implementação simples, o mapeamento de endereços virtuais em endereços físicos pode ser resumido como a seguir: o endereço virtual é dividido em um número de página virtual (bits mais significativos) e um deslocamento (bits menos significativos).
  ## Multinível
  O objetivo é evitar manter toda a tabela de páginas na memória durante todo o tempo. Divisão do processo em várias etapas.
  - Apresenta-se como uma solução para o dimensionamento da tabela de páginas.
  - Uso de dois apontadores e um deslocamento
  ## Invertidas
  Há apenas uma entrada por moldura de página na memória real, em vez de uma entrada por página do espaço de endereçamento virtual, isto é ter o tamanho da quantidade de molduras (memória real) e não da quantidade de páginas (memória virtual).
  - Solução muito lenta.
  - Pode-se utilizar TLB para melhoria das referências das páginas.
 ##### Segmentação
 A região do espaço de endereçamento alocada para a tabela de símbolos pode se esgotar, mas talvez haja muito espaço nas outras tabelas. A segmentação é uma solução direta para esse problema, visto que consiste em uma alocação contígua de memória, agindo como um tipo alocação em memoria virtual não física dependente da lógica do programa, tendo o tamanho variável durante o seu tempo de vida.
 - Existe um tamanho máximo para o segmento;
 - Elimina fragmentação interna (mas pode haver externa).
 ![[so-segmentacao.png]]
 ##### Algoritmos de Paginação
  ## O algoritmo de substituição de páginas não usadas recentemente (NRU)
  Cada página associada possui dois bits de estágio R (lida ou escrita) e M (modificada). Esses bits precisam ser atualizados em cada referência de memória, então é essencial que eles sejam atualizados pelo hardware. Assim que um bit tenha sido modificado para 1, ele fica em 1 até o sistema operacional reinicializá-lo em 0. Ao ocorrer uma **page fault** o sistema operacional separa todas as páginas em quatro categorias (classes) e então remove uma página aleatória da classe mais baixa que não esteja vazia.
 ## O algoritmo de substituição de páginas primeiro a entrar, primeiro a sair (first in, first out — FIFO)
  Este algoritmo de substituição de página funciona de forma semelhante a uma pilha. A página mais antiga é removida primeiro, e a nova página é adicionada ao final da lista.
  - Pode descartar páginas importantes
  ## O algoritmo de substituição de páginas segunda chance
  O algoritmo de substituição de páginas segunda chance é uma simples aprimoração do algoritmo FIFO. Neste algoritmo, ao invés de remover a página mais antiga sem considerar se ela está sendo utilizada, é verificado através do bit R se a página mais antiga foi recentemente referenciada antes de decidir substituí-la. Embora seja um algoritmo razoável, ele é desnecessariamente ineficiente, pois ele está sempre movendo páginas em torno de sua lista.
  ## O algoritmo de substituição de páginas do relógio 
  O funcionamento do algoritmo do relógio é baseado em uma lista circular de páginas, organizadas como se fossem os números em um relógio. Um ponteiro aponta para a página mais antiga. Quando ocorre uma falta de página, a página indicada pelo ponteiro é inspecionada.
  ![[so-alg-relogio.png]]
  ## Algoritmo de substituição de páginas usadas menos recentemente (LRU)
  A ideia por trás do LRU é que as páginas que foram menos utilizadas recentemente têm maior probabilidade de serem as próximas a serem substituídas. Um dos algoritmos mais eficazes em termos de desempenho para a substituição de páginas em sistemas operacionais. O funcionamento do LRU é baseado no histórico de referências às páginas. Quando ocorre uma falta de página, o algoritmo identifica a página que não foi usada há mais tempo e a substitui. É necessário que seja mantida uma lista encadeada de todas as páginas na memória, com a página mais recentemente usada na frente e a menos recentemente usada na parte de trás. A dificuldade é que a lista precisa ser atualizada a cada referência de memória
  - Excelente algoritmo, porém difícil de ser implementado de maneira exata.
  ## Algoritmo de envelhecimento (Aging)
  Substituição de páginas que simula o algoritmo LRU, no entanto, determina quais páginas devem ser substituídas com base em seu histórico de referências. No algoritmo de envelhecimento, cada página na memória é associada a um contador que é atualizado periodicamente. A cada intervalo de tempo, um bit de referência (R) é movido para a esquerda no contador. Uma vantagem do algoritmo de envelhecimento é sua capacidade de aproximar o comportamento do LRU sem a necessidade de manter uma lista encadeada de todas as páginas na memória.
  ## O algoritmo de substituição de páginas do conjunto de trabalho
  Visa encontrar e substituir páginas que não estão no conjunto de trabalho ativo de um processo. O algoritmo do conjunto de trabalho é baseado em informações como o tempo aproximado em que uma página foi usada pela última vez e o bit de referência (R) associado a cada página.
  - Implementação um tanto cara
  ## O algoritmo de substituição de página WSClock
  Variante aprimorada do algoritmo do relógio, que combina informações do conjunto de trabalho com a lógica do algoritmo de relógio para melhorar o desempenho na substituição de páginas em sistemas operacionais. O WSClock prioriza a substituição de páginas que não estão no conjunto de trabalho, garantindo que as páginas menos relevantes para a execução do processo sejam substituídas primeiro.
  - Algoritmo bom e eficiente
# Sistemas de Arquivos
Arquivos são unidades lógicas de informações criadas por processos. Um disco contém uma sequência linear de blocos de tamanho fixo e que apoiam a leitura e registro dos blocos. O sistema de arquivos reside permanentemente em memória secundária, que é projetada para manter uma grande quantidade de dados de maneira não volátil.

![[so-estrutura-sa.png]]
##### Sequência de Bytes 
Na sequencia desestruturada de bytes o SO não sabe o que o arquivo contém. Tudo o que ele vê são bytes. Qualquer significado deve ser imposto pelos programas em nível de usuário. 
- UNIX, MS-DOS e Windows utilizam essa estratégia.
- Oferece máxima flexibilidade.
##### Implementação de Caches
O acesso a disco é bastante lento ao comparado a memória principal. Desse modo, a maioria dos sistemas operacionais implementa a técnica de buffer cache onde o sistema reserva uma área na memória para que se tornem disponíveis caches utilizados em operações de acesso a disco.

1. Operação realizada é buscada no cache.
2. Caso não encontre, ela é buscada no disco.
3. Atualiza o buffer cache com a operação.
#### Diretórios
Modo como o sistema organiza os diferentes arquivos contidos num disco.
##### Nível Único (single-level directory)
É a implementação mais simples, existe apenas um único diretório contendo todos os arquivos do disco.
- É bastante limitado já que não permite que usuários criem arquivos com o mesmo nome o que ocasionaria um conflito no acesso aos arquivos.
##### User File Directory (UFD)
Para cada usuário existe um diretório particular e assim poderia criar arquivos com qualquer nome.
- Deve haver um nível de diretório adicional para controle chamado de Master File Directory (MFD) que é indexado pelo nome do usuário e cada entrada aponta para o diretório pessoal.
- É análoga a uma estrutura de dados em árvore onde o MFD é a raiz, os galhos são a UFD e os arquivos são as folhas.
- Quando se referencia a um arquivo é necessário especificar seu nome e seu diretório isto é chamado de path (caminho).
##### Estrutura de diretórios em Árvore
Adotado pela maioria dos sistemas operacionais e é logicamente melhor organizado.
- Cada arquivo possui um path único que descreve todos os diretórios da raiz (MFD) até o diretório onde o arquivo esta ligado e na maioria dos sistemas os diretórios são tratados como arquivos tendo atributos e identificação.

![[so-dr-arvore.png]]
##### Monitoramento de espaço no disco
A criação de arquivos exige que o sistema operacional tenha controle de quais áreas ou blocos no disco estão livres.
 #### Bit Map
 Tabela chamada mapa de bits (bit map) onde cada entrada da tabela é associada a um bloco e representado por um bit, que pode assumir valor igual a 0 (bloco livre) ou 1 (bloco alocado).
 - Esta estrutura gera um gasto excessivo de memória já que para cada bloco deve existir uma entrada na tabela.
 #### Fragmentação Interna
Arquivos são alocados em blocos, de tamanho físico.
- blocos pequenos: menor perda de fragmentação, maior custo de gerência.
- blocos grandes: maior perda de fragmentação, menor custo de gerência.
##### Lista de Controle de Acesso (ACL)
Consiste em uma lista associada a cada arquivo onde são especificados quais os usuários e os tipos de acesso permitidos.
- É possível encontrar tanto a proteção por grupos de usuários quanto pela lista de acesso oferecendo uma maior flexibilidade ao mecanismo de proteção.  
#### Alocação Contígua
Consiste em armazenar um arquivo em blocos sequencialmente dispostos. Neste tipo, o sistema localiza um arquivo através do endereço do primeiro bloco e da sua extensão em blocos. Deve ser feito a desfragmentação periodicamente (visando que este problema seja resolvido) para reorganizar os arquivos no disco a fim de que exista um único segmento de blocos livres. O principal problema é a alocação de novos arquivos nos espaços livres, pois para colocar n blocos é necessário que se tenha uma cadeia com n blocos dispostos sequencialmente no disco. 

- Realiza acesso sequencial ou direto.
- Geração de fragmentação externa.

![[so-contigua.png]]
#### Alocação Encadeada
O arquivo é organizado como um conjunto de blocos ligados no disco, independente de sua localização física e cada um deve possuir um ponteiro para o bloco seguinte. O que ocorre neste método é a fragmentação de arquivos (quebra do arquivo em diversos pedaços denominados extents) o que aumenta o tempo de acesso ao arquivo, pois o disco deve deslocar-se diversas vezes para acessar todas as extents.

- Necessário a desfragmentação periódica.
- Eliminação a fragmentação externa

```ad-important
##### Fragmentação Externa
Em um sistema operacional trabalhando com alocação contígua de memória, quando há memória suficiente para o atendimento de um pedido de alocação, mas esta memória não é contígua.
```

```ad-important
##### Fragmentação Interna
Em um sistema operacional trabalhando com alocação contígua de memória, quando a memória alocada por um processo não é completamente utilizada.
```

```ad-important
##### Desfragmentação 
Reorganiza os dados, movendo os arquivos fragmentados para locais contíguos no disco e consolidando o espaço livre em regiões também contíguas.
```

```ad-important
##### Compactação
Um processo demorado realizado pelo **S.O**. que combina todos os buracos formados na memória em um mesmo bloco contíguo.
- É raramente utilizada devido a grande utilização de UCP requerida.
```
#### Alocação Indexada
O princípio desta técnica é manter os ponteiros de todos os blocos de arquivos em uma única estrutura denominada bloco de índice. Além de permitir o acesso direto aos blocos do arquivo, não utiliza informações de controle nos blocos de dados como existe na alocação encadeada.

![[so-index-alocation.png]]
#### NTFS 
Sistema de arquivos padrão do Windows, oferece recursos como criptografia, permissões e suporte a arquivos grandes.

- Estruturação hierárquica no formato de árvore (nodes). 
- O NTFS usa abordagem de alocação indexada com ponteiros de 64 bits.
- sistema de arquivo otimizado para suportar arquivos e volumes muito grandes (8 Exabytes).
- Opera em um ambiente heterogêneo com diferentes computadores, sistemas operacionais e arquiteturas de rede.
- Jornalização é o processo que garante a integridade dos dados (como se fosse um diário, do que o sistema de arquivos vai fazer antes que ele o faça, guardando essas informações em caso de perda de dados).

```ad-info
##### Outros tipos de sistemas de arquivos
- Fat
- exFat - Sistema de arquivos compatível com outros dispositivos, solução para o Fat32
- Fat16
- Fat32 (4 GB)

```

#### EXT
Sistema de arquivos padrão do Linux.

- Estruturação em i-node.
- Alocação do tipo indexada.
- Conta com o sistema de Jornalização.
- Suporta arquivos com até 16 terabytes.
- Não possui recursos de alocação de espaço eficiente.
- Tem limitação em relação ao NTFS com arquivos grandes.

#### ReFS (Resilient File System)
É o sistema de arquivo mais recente desenvolvido pela Microsoft; foi introduzido no Windows 8. Sua arquitetura difere dos outros sistemas de arquivos do Windows por ser organizada na forma de árvore B+.
#### XFS (Extended File System)
Criado para ser usado nos servidores da empresa Silicon Graphics. Em 2001, foi integrado ao Kernel do Linux e, atualmente, é suportado pela maioria das distribuições Linux. Trata-se de um sistema de arquivo otimizado para suportar arquivos e volumes muito grandes (8 Exabytes).
#### FAT (File Allocation Table)
Foi desenvolvido para o MS-DOS e usado em versões do Windows até o Windows 95. A maioria dos sistemas operacionais suportam esse sistema de arquivos.
- Alocação do tipo encadeada.
#### VFS (Sistema de Arquivos Virtuais)
Camada de abstração do sistema de arquivos, fornecendo uma interface para o usuário para a interação com outros sistemas de arquivos como Fat32, ext3, ReiserFS, exFat.
#### Linux
- /var - logs, filas de impressão, filas de e-mail e outros arquivos mantidos dinamicamente pelo sistema.
- /proc - diretório virtual, arquivos servem como ponto de acesso para uma série de variáveis e recursos do sistema
- /usr - hierarquia de diretórios, comandos de usuário, código fonte, documentação
- /etc -  arquivos de configuração do sistema

 ##### Comandos
 fdisk, cfdisk: manipula ou mostra tabela de partição de um dispositivo.
 df: Mostra a informação de utilização do disco para sistema de arquivos montados e diretórios
 chmod: Modifica o modo de acesso à arquivos  ``$ chmod 644 -r afile`` 
- -c: como o modo verboso, mas só reporta as mudanças.
- -r: modo recursivo
- -v: modo verboso
- 0 = nenhuma permissão;
- 1 = apenas executar;
- 2 = apenas gravar;
- 3 = gravar e executar;
- 4 = apenas ler;
- 5 = ler e executar;
- 6 = ler e gravar; 
- 7 = ler, gravar e executar;
- O primeiro número refere-se às permissões do proprietário do arquivo.
- O segundo número refere-se às permissões do grupo ao qual o arquivo pertence.
- O terceiro número refere-se às permissões para todos os outros usuários que não se encaixam nas duas categorias anteriores.

```ad-attention
sistemas distribuídos: http://profs.ic.uff.br/~simone/sd/contaulas/
```