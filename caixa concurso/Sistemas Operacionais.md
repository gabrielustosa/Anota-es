# Conceitos base sobre SO
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
#### Sistemas micro-núcleo (microkernel)
A ideia básica por trás do projeto do micronúcleo é alcançar alta confiabilidade por meio da divisão do sistema operacional em módulos pequenos, bem defini dos, e  apenas um desses módulos – o micronúcleo – é executado no modo núcleo e o restante é executado como processos  de usuário.
#### Modelo Cliente Servidor
Uma variação da ideia do micronúcleo é distinguir entre duas classes de processos, os servidores, que prestam serviço, e os clientes, que usam serviços.
# Processo
Uma abstração de uma instância de um programa em execução. São úteis para a organização de um sistema de processo paralelo (pseudo-async).

 ## Estados de um processo
1. Execução (está sendo executado pela CPU naquele momento)
2. Pronto (executável ou parado temporariamente para deixar outro processo prioritário ser executado)
3. Bloqueado ou Wait (incapaz de ser executado, esperando outro evento acontecer)
 
 ## BCP  (Process Control Block – PCB)
 Estrutura onde o SO guarda todas as informações do processo, contendo sua identificação, prioridade, estado corrente, recursos alocados por ele e informações sobre o programa em execução.
 
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
 Técnicas usada em programação para evitar que processos tenham acesso simultaneamente a um recurso compartilhado.
  ## Busy Wait (Espera ocupada)
  Consiste na constante checagem por algum valor para saber se a região crítica está sendo utilizada. 
  - Requer muito processamento da CPU.
  ## Sleep/Wake up (Dormir/Acordar)
  utilizando funções de "acordar" ou "despertar" processos a depender se condições são atendidas.
  -  Surge como solução a processo **busy wait**, não utilizando um loop infinito para checagem de estado.
 ##  Semáforos 
  Controla o uso de acesso de determinado recurso, coordenados por uma ação ação atômica indivisível.
- Binário: incrementa valores para alterar o estado do processo, no qual é representado por **down (0)** ou **up (1)**.
- Geral (Contadores): São utilizado para controlar um número de acessos pré-definido.
 ##  Mutexes
  Uma versão simplificada de semáforos, utilizada para exclusão mútua.
 * É uma variável que pode estar definida com travada (1) e destravada (0). 
 * Bastante utilizada em processos concorrentes 
 ##  Monitor
  Estruturas de sincronização de alto nível que garantem a exclusão mútua e a sincronização de processos. 
* Somente pode estar ativo um processo dentro do monitor em um mesmo instante.
 ## Centralizado
 Geralmente, é utilizado em sistemas distribuídos. Se comunica através de mensagens, solicitando para entrar e avisando quando saem da região crítica.
 ## Lamport
 Geralmente, é utilizado em sistemas distribuídos. São baseados em relógios lógicos distribuídos, ou seja, cada processo possui seu próprio relógio lógico que é usado para determinar a ordem das operações que lidam com regiões críticas.
 ## Token Ring
 Gerenciada por um token que é passado de um processo para o próximo em uma estrutura de anel. Somente o processo que possui o token pode acessar a seção crítica.
 
```ad-summary
##### Solução de Peterson
É um método clássico para garantir a exclusão mútua em sistemas concorrentes. A ideia básica por trás da solução de Peterson é a utilização de **variáveis de turno** e **flags** para indicar a intenção de entrar na seção crítica. Sendo assim, a solução de Peterson utiliza a chamada de duas funções: `enter_region` (entrar na região crítica) e `leave_region` (sair da região crítica).

- **Variáveis de Turno**: Cada processo tem uma variável associada que indica quando é sua vez de entrar na seção crítica. Isso permite que os processos entrem na seção crítica de forma alternada.
- **Flags**: Cada processo tem uma flag associada que indica se ele deseja entrar na seção crítica. Isso permite que os processos expressem sua intenção de entrar na seção crítica.
```

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
 ## Garantido
 Assegura a execução dos processos, dando a todos eles a mesma quantidade de tempo de execução utilizando a CPU. Se um processo utilizar menos tempo de execução do que poderia, sua prioridade de execução é aumentada. Por outro lado, se um processo utilizou mais tempo do que deveria, sua prioridade é diminuída.
#### Impasses
##### DeadLock
 Quando 2 ou mais programas estão tentando acessar algo ao mesmo tempo resultando na bloqueamento dos 2 programas.
 **TODAS** as condições para o DeadLock ocorrer: 
	 - **Exclusão mútua**:  cada recurso só pode estar alocado a um único processo em um determinado instante;
	 - **Posse e Espera**: um processo, além dos recursos já alocado, pode estar esperando por outros recursos;
	 - **Não-Preempção**: um recurso não pode ser liberado de um processo só porque outros processos desejam o mesmo recurso;
	 - **Espera circular**: um processo pode ter de esperar por um recurso alocado a outro processo e vice-versa.
![[so-impasses.png]]
  
  ## Algoritmo do Banqueiro
  O algoritmo do banqueiro é um algoritmo usado para evitar impasses (deadlocks) em sistemas computacionais, requer que cada processo declare o máximo de recursos que pode precisar antecipadamente. 
  ## Algoritmo do Avestruz
  Uma estratégia de ignorar deadlocks. "Enfie a cabeça na areia e finja que não há um problema".
##### Livelock
Em algumas situações, um processo tenta ser educado abrindo mão dos bloqueios que ele já adquiriu sempre que nota que não pode obter o bloqueio seguinte de que precisa. Então ele espera um milissegundo, digamos, e tenta de novo. No entanto, se o outro processo faz a mesma coisa exatamente no mesmo momento, eles estarão na situação na qual nem um dois conseguira terminar sua execução.
##### Inanição (starving)
Devido a má gerência de escalonamento é possível que processos sofram de inanição, ou seja, mesmo estejam prontos para ser executados podem não tem acesso ao recurso desejado.

- Pode ser evitada com uma política de alocação de recursos primeiro a chegar, primeiro a ser servido
# Gerência de Memória
O principal objetivo é fornecer uma maneira eficiente e segura para que os processos em um sistema computacional acessem e compartilhem a memória.

```ad-tip
##### Multiprogramação
Denota um sistema operacional que provê gerenciamento da totalidade de recursos tais como CPU, memória, sistema de arquivos, em adição ao suporte da execução concorrente dos processos

- Integral: caso mais de um processo possa se encontrarem execução na memória em um dado instante.
- Serial: apenas um processo se encontra em execução a cada instante, sendo a CPU alocada aos processos de forma intercalada ao longo do tempo.
```
#### MMU (Memory Manager Unit)
O acesso do processador a memória é controlador pelo sistema operacional através do controlador denominado **MMU** que é o responsável por analisar cada endereço acessado pelo processador, validar e efetuar conversões necessárias entres os endereços lógicos e físicos garantindo o desempenho máximo. A MMU usa uma tabela de páginas para mapear endereços lógicos para endereços físicos, o que permite ao sistema operacional gerenciar a memória de maneira mais flexível e eficiente.

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
```ad-tip
##### Buffer
Região da memória física do computador utilizada para armazenar dados temporariamente, tendo como finalidade manter as informações salvas antes de serem efetivamente usadas.
- Um buffer armazena os dados na memória RAM devido ao tempo de acesso rápido
```
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
 ##### First-Fit (tamanho suficiente)
 O primeiro segmento livre com tamanho suficiente para alocar o arquivo é selecionado. A busca na lista é sequencial, sendo interrompida tão logo se encontre um segmento adequado.
 - Mais rápido e o melhor.
 - Ele gera no inicio da memória pequenas partições livres que necessitam ser pesquisadas a cada passo subsequente do First-Fit.
 ##### Next-Fit (grande,  próximo ao último segmento)
 Parecido com o First-Fit, porém inicia a procura a partir do local onde foi feito a ultima locação e escolhe o bloco que é grande o suficiente para o processo a ser alocado;
 - Frequentemente aloca blocos livres no fim da memória.
 - Performance inferior ao First-Fit.
 ##### Best-Fit (menor)
 Seleciona o menor segmento livre disponível com tamanho suficiente para armazenar o arquivo. A busca em toda a lista se faz necessária para a seleção do segmento, a não ser que a lista esteja ordenada por tamanho.
 - Tem a pior performance.
 - Procura pelo menor bloco que satisfaça o requisito.
 ##### Worst-Fit (maior)
 Maior segmento é alocado e a busca por toda a lista se faz necessária, a menos que exista uma ordenação por tamanho.
 - Escolhe Maior espaço possível;
 - Tempo de busca grande;
 ##### Quick-Fit (tabela)
 Mantém listas em separado para alguns dos tamanhos mais comuns solicitados. Ele pode ter uma tabela com n entradas, na qual a primeira é um ponteiro para o início de uma lista espaços livres.
 - Tem as mesmas desvantagens de todos os esquemas que ordenam por tamanho do espaço livre.
#### Memória virtual
Cada programa tem seu espaço de endereçamento, divido em blocos chamados de páginas. Cada página é uma série contígua de endereços. Estas são mapeadas na memória física, porém não necessitam estar carregadas na memória física, podem estar alocadas em um disco rígido, sendo trabalho do sistema operacional carrega-las na memória física se necessário.

A memória virtual pode ser implementada dividindo o espaço do endereço virtual em páginas e mapeando cada uma delas em algum quadro de página da memória física ou não as mapeando (temporariamente). Há quatro momentos em que o sistema operacional tem de se envolver com a paginação: na criação do processo, na execução do processo, em faltas de páginas e no término do processo.

 ##### Swapping
 Técnica utilizada para poupar espaço na memória física (RAM), movendo processo temporariamente para um disco rígido. Quando o processo é movido ele é salvo em um arquivo chamado swap que depois é utilizado para mover o processo novamente para memória.
 ##### Paginação
 Técnica de endereçamento de memória que utiliza o conceito de memória virtual, em que o espaço de endereçamento virtual é dividido em pequenos blocos iguais conhecidos como páginas virtuais.
 - Quando uma página não é encontrada ocorre um Page Interrupt, no qual a MMU realiza um desvio para a CPU, resultando em uma Page Fault, que é buscada utilizado o algoritmo de busca responsável.
 ##### Quadros
 As páginas em memória virtual correspondentes na memória física são chamadas de quadros de página, ou página física. Quando uma página de memória virtual é carregada na memória física, ela é colocada em um quadro disponível. As páginas e os quadros de página são geralmente do mesmo tamanho fixo.
 ##### Tabela de Páginas
 Registra em que bloco de memória cada página está carregada. As tabelas de páginas são mantidas pelo S.O. Se uma página é acessada mas não está na memória, o **S.O.** consulta a tabela de blocos livres, aloca a página no bloco selecionado e atualiza a tabela de páginas. Em uma implementação simples, o mapeamento de endereços virtuais em endereços físicos pode ser resumido como a seguir: o endereço virtual é dividido em um número de página virtual (bits mais significativos) e um deslocamento (bits menos significativos). 
 * Um **bit sujo** ou **bit** **modificado** é um bit associado a um bloco de memória de computador e indica se o bloco de memória correspondente foi modificado ou não.
  ## Multinível
  O objetivo é evitar manter toda a tabela de páginas na memória durante todo o tempo. Divisão do processo em várias etapas.
  - Apresenta-se como uma solução para o dimensionamento da tabela de páginas.
  - Uso de dois apontadores e um deslocamento
  ## Invertidas
  Há apenas uma entrada por moldura de página na memória real, em vez de uma entrada por página do espaço de endereçamento virtual, isto é ter o tamanho da quantidade de molduras (memória real) e não da quantidade de páginas (memória virtual).
  - Solução muito lenta.
  - Pode-se utilizar TLB para melhoria das referências das páginas.
 ##### Translation Lookaside Buffer (TLB)
 É um cache de memória que armazena as traduções recentes da memória virtual para a memória física. Ele é utilizado para reduzir o tempo necessário para acessar uma localização de memória do usuário.
 ##### Trashing
 nome dado à excessiva transferência de páginas/segmentos da memória principal para a secundária e vice-versa (elevado número de page-faults). Como resultado, o processo fica pouco tempo executando suas funções. Os principais motivos que levam ao thrashing são o mau dimensionamento, a não obediência ao princípio da localidade de referência 
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
  ## Algoritmo de substituição de páginas usadas menos recentemente (LRU)  - princípio da temporalidade
  A ideia por trás do LRU é que as páginas que foram menos utilizadas recentemente têm maior probabilidade de serem as próximas a serem substituídas. Um dos algoritmos mais eficazes em termos de desempenho para a substituição de páginas em sistemas operacionais. O funcionamento do LRU é baseado no histórico de referências às páginas. Quando ocorre uma falta de página, o algoritmo identifica a página que não foi usada há mais tempo e a substitui. É necessário que seja mantida uma lista encadeada de todas as páginas na memória, com a página mais recentemente usada na frente e a menos recentemente usada na parte de trás. A dificuldade é que a lista precisa ser atualizada a cada referência de memória
  - Excelente algoritmo, porém difícil de ser implementado de maneira exata.
  ## LFU (Least-Frequently-Used)
  Seleciona a pagina menos referenciada (é mantido contador de referências para cada página).
  ## Algoritmo de envelhecimento (Aging)
  Substituição de páginas que simula o algoritmo LRU, no entanto, determina quais páginas devem ser substituídas com base em seu histórico de referências. No algoritmo de envelhecimento, cada página na memória é associada a um contador que é atualizado periodicamente. A cada intervalo de tempo, um bit de referência (R) é movido para a esquerda no contador. Uma vantagem do algoritmo de envelhecimento é sua capacidade de aproximar o comportamento do LRU sem a necessidade de manter uma lista encadeada de todas as páginas na memória.
  ## O algoritmo de substituição de páginas do conjunto de trabalho
  Visa encontrar e substituir páginas que não estão no conjunto de trabalho ativo de um processo. O algoritmo do conjunto de trabalho é baseado em informações como o tempo aproximado em que uma página foi usada pela última vez e o bit de referência (R) associado a cada página.
  - Implementação um tanto cara
  ## O algoritmo de substituição de página WSClock
  Variante aprimorada do algoritmo do relógio, que combina informações do conjunto de trabalho com a lógica do algoritmo de relógio para melhorar o desempenho na substituição de páginas em sistemas operacionais. O WSClock prioriza a substituição de páginas que não estão no conjunto de trabalho, garantindo que as páginas menos relevantes para a execução do processo sejam substituídas primeiro.
  - Algoritmo bom e eficiente
# Sistemas de Arquivos
 Um disco contém uma sequência linear de blocos de tamanho fixo e que apoiam a leitura e registro dos blocos. O sistema de arquivos reside permanentemente em memória secundária, que é projetada para manter uma grande quantidade de dados de maneira não volátil.
#### Arquivos
Arquivos são unidades lógicas de informações criadas por processos. Embora tecnicamente o arquivo seja apenas uma sequência de bytes, ele só pode ser executado pelo **S.O.** se ele possuir a seguinte tiver o formato apropriado.
##### Estrutura de arquivos

![[so-estrutura-sa.png]]
 
 ## Sequência de Bytes 
 Na sequencia desestruturada de bytes o SO não sabe o que o arquivo contém. Tudo o que ele vê são bytes. Qualquer significado deve ser imposto pelos programas em nível de usuário. 
- UNIX, MS-DOS e Windows utilizam essa estratégia.
- Oferece máxima flexibilidade.
 ## Sequência de registros
 Nesse modelo, um arquivo é uma sequência de registros de tamanho fixo, cada um com alguma estrutura interna.
- A operação de leitura retorna um registro e a operação de escrita sobrepõe ou anexa um registro.
- Sistema anterior, usado em máquinas antigas.
 ## Árvore
 Nessa organização, um arquivo consiste em uma árvore de registros, não necessariamente todos do mesmo tamanho, cada um contendo um campo chave em uma posição fixa no registro. A árvore é ordenada no campo chave, a fim de permitir uma busca rápida por uma chave específica.
##### Composição de um arquivo
1. Cabeçalho - Número mágico (para evitar a execução acidental de um arquivo que não esteja em seu formato),  tamanhos  das várias partes do arquivo, o endereço no qual a execução começa e alguns bits de sinalização.
3. Texto, Dados -  Texto e os dados do próprio programa
4. Bits de realocação - são utilizados para realocar texto e dados do programa.
5. Tabela de símbolos - usada para correção de erros.
6. Metadados - Bits de proteção, tamanho do arquivo, data de modificação, flags. 
##### Operações com arquivos
1. **Create** - O arquivo é criado sem dados. A finalidade dessa chamada é anunciar que o arquivo está vindo e estabelecer alguns dos atributos.
2. **Delete** - Quando o arquivo não é mais necessário, ele tem de ser removido para liberar espaço para o disco.
3. **Open** - Antes de usar um arquivo, um processo precisa abri-lo. A finalidade da chamada open é permitir que o sistema busque os atributos e lista de endereços do disco para a memória principal a fim de tornar mais rápido o acesso em chama- das posteriores.
4. **Close** - Quando todos os acessos são concluídos, então o arquivo deve ser fechado para liberar espaço da tabela interna.  Um disco é escrito em blocos, e o fechamento de um arquivo força a escrita do último bloco dele, mesmo que não esteja inteiramente cheio ainda.
5. **Read** - Dados são lidos do arquivo. Em geral, os bytes vêm da posição atual. Quem fez a chamada deve especificar a quantidade de dados necessária e também fornecer um buffer para colocá-los.
6. **Write** - Dados são escritos para o arquivo de novo, normalmente na posição atual.
7. **Append** - Essa chamada é uma forma restrita de write. Ela pode acrescentar dados somente para o final do arquivo.
8. **Seek** - Para arquivos de acesso aleatório, é necessário um método para especificar de onde tirar os dados. Uma abordagem comum é uma chamada de sistema, seek, que reposiciona o ponteiro de arquivo para um local específico dele. Após essa chamada ter sido completa, os dados podem ser lidos da, ou escritos para, aquela posição.
9. **Get** **attributes** - Processos muitas vezes precisam ler atributos de arquivos para realizar seu trabalho. 
10. **Set** **attributes** - Alguns dos atributos podem ser alterados pelo usuário e modificados após o arquivo ter sido criado.
11. **Rename** - Acontece com frequência de um usuário precisar mudar o nome de um arquivo.
##### Lista de Controle de Acesso (ACL)
Consiste em uma lista associada a cada arquivo onde são especificados quais os usuários e os tipos de acesso permitidos.
- É possível encontrar tanto a proteção por grupos de usuários quanto pela lista de acesso oferecendo uma maior flexibilidade ao mecanismo de proteção.  
#### Diretórios
Modo como o sistema organiza os diferentes arquivos contidos num disco.
##### Nível Único (single-level directory)
É a implementação mais simples, existe apenas um único diretório contendo todos os arquivos do disco.
- É bastante limitado já que não permite que usuários criem arquivos com o mesmo nome o que ocasionaria um conflito no acesso aos arquivos.
##### Estrutura de diretórios em Árvore
Adotado pela maioria dos sistemas operacionais e é logicamente melhor organizado.
- Cada arquivo possui um path único que descreve todos os diretórios da raiz (MFD) até o diretório onde o arquivo esta ligado e na maioria dos sistemas os diretórios são tratados como arquivos tendo atributos e identificação.

 ## User File Directory (UFD)
 Para cada usuário existe um diretório particular e assim poderia criar arquivos com qualquer nome.
- Deve haver um nível de diretório adicional para controle chamado de Master File Directory (MFD) que é indexado pelo nome do usuário e cada entrada aponta para o diretório pessoal.
- É análoga a uma estrutura de dados em árvore onde o MFD é a raiz, os galhos são a UFD e os arquivos são as folhas.
- Quando se referencia a um arquivo é necessário especificar seu nome e seu diretório isto é chamado de path (caminho).

![[so-dr-arvore.png]]
##### Operações com diretórios
1. Create. Um diretório é criado.
2. Delete. Um diretório é removido.
3. Opendir. Diretórios podem ser lidos.
4. Closedir. Quando um diretório tiver sido lido, ele será fechado para liberar espaço de tabela interno.
5. Readdir. Essa chamada retorna a próxima entrada em um diretório aberto.
6. Rename. Em muitos aspectos, diretórios são como arquivos e podem ser renomeados da mesma maneira que eles
7. Link. A ligação (linking) é uma técnica que permite que um arquivo apareça em mais de um diretório. Essa chamada de sistema especifica um arquivo existente e um nome de caminho, e cria uma ligação do arquivo existente para o nome especificado pelo caminho, às vezes é chamada de ligação estrita (hard link).
8. Unlink. Uma entrada de diretório é removida.
#### Esquema de sistemas de arquivos
Sistemas de arquivos são armazenados em discos. A maioria dos discos pode ser dividida em uma ou mais partições, com sistemas de arquivos independentes em cada partição 
##### MBR (Master Boot Record )
É o setor 0 do disco, usado para inicializar o computador.
- No fim, possui uma tabela de partição (Ela dá os endereços de início e fim de cada partição).
- A primeira coisa que o programa MBR faz é localizar a partição ativa, ler seu primeiro bloco, que é chamado de bloco de inicialização, e executá-lo.

![[so-esquema-particao.png]]
#### Implementação de arquivos
##### Alocação Contígua
Consiste em armazenar um arquivo em blocos sequencialmente dispostos. Assim, em um disco com blocos de 1 KB, um
arquivo de 50 KB seria alocado em 50 blocos consecutivos. Neste tipo, o sistema localiza um arquivo através do endereço do primeiro bloco e da sua extensão em blocos. 

- Realiza acesso sequencial ou direto.
- Geração de fragmentação externa.

![[so-contigua.png]]
##### Alocação Encadeada
O arquivo é organizado como um conjunto de blocos ligados no disco, independente de sua localização física e cada um deve possuir um ponteiro para o bloco seguinte. O que ocorre neste método é a fragmentação de arquivos (quebra do arquivo em diversos pedaços denominados extents) o que aumenta o tempo de acesso ao arquivo, pois o disco deve deslocar-se diversas vezes para acessar todas as extents.

- Necessário a desfragmentação periódica, devido a fragmentação interna.
- Eliminação a fragmentação externa 

 ## Alocação encadeada usando uma tabela na memória
 Ambas as desvantagens da alocação por lista encadeada podem ser eliminadas colocando-se as palavras do ponteiro de cada bloco de disco em uma tabela na memória. Essa tabela na memória principal é chamada de FAT (File Allocation Table — tabela de alocação de arquivos).
##### Alocação Indexada (I-nodes)
O princípio desta técnica é manter os ponteiros de todos os blocos de arquivos em uma única estrutura denominada bloco de índice. Além de permitir o acesso direto aos blocos do arquivo, o i-node precisa estar na memória apenas quando o arquivo correspondente estiver aberto e não utiliza informações de controle nos blocos de dados como existe na alocação encadeada.

![[so-index-alocation.png]]
##### Sistemas de arquivos estruturados em diário (log)
A ideia que impeliu o design do LFS é de que à medida que as CPUs ficam mais rápidas e as memórias RAM maiores, caches em disco também estão aumentando rapidamente. Embora todas as leituras sejam impossíveis de serem realizadas sequencialmente (uma vez que qualquer arquivo pode ser acessado a qualquer momento), podemos explorar a eficiência das gravações sequenciais. O LFS mantém um pequeno buffer de todas as gravações em um segmento de memória.

- Um log é simplesmente uma estrutura de dados que é escrita apenas na cabeça (pode-se pensar em todo o disco como um log). 
- Cada gravação faz com que novos blocos sejam adicionados ao buffer de segmento atual na memória.
- Quando o segmento está cheio, ele é gravado no disco.
##### Sistemas de arquivos journaling 
A ideia básica aqui é manter um diário do que o sistema de arquivos vai fazer antes que ele o faça; então, se o sistema falhar antes que ele possa fazer seu trabalho planejado, ao ser reinicializado, ele pode procurar no diário para ver o que acontecia no momento da falha e concluir o trabalho. Após as operações terem sido concluídas de maneira bem-sucedida, a entrada no diário é apagada. 

1. Operação de arquivo/diretório
2. Liberar o i-node para o conjunto de i-nodes livres.
3. Retornar todos os blocos de disco para o conjunto de blocos de disco livres.
##### VFS (Virtual File System — sistema de arquivos virtuais)
Integra múltiplos sistemas de arquivos em uma estrutura ordeira. A ideia fundamental é abstrair a parte do sistema de arquivos que é comum a todos os sistemas de arquivos e colocar aquele código em uma camada separada que chama os sistemas de arquivos subjacentes para realmente gerenciar os dados.

- Todas as chamadas de sistemas relativas a arquivos são direcionadas ao sistema de arquivos virtual para processamento inicial.
- possui estruturas internas de dados como a tabela de montagem e um conjunto de descritores de arquivos.
- superbloco - descreve um sistema de arquivos.
- v-node - que descreve um arquivo.

![[so-vfs.png]]
#### Monitoramento dos blocos livres
A criação de arquivos exige que o sistema operacional tenha controle de quais áreas ou blocos no disco estão livres.
##### Bit Map
Onde cada entrada da tabela é associada a um bloco e representado por um bit, que pode assumir valor igual a 0 (bloco livre) ou 1 (bloco alocado).
 - Esta estrutura gera um gasto excessivo de memória já que para cada bloco deve existir uma entrada na tabela.
#### Desempenho do sistema de arquivos
##### Cache de blocos (cache de buffer)
A técnica mais comum usada para reduzir os acessos ao disco. Nesse contexto, uma cache é uma coleção de blocos que logicamente pertencem ao disco, mas estão sendo mantidas na memória por razões de segurança. A maneira usual é mapear o dispositivo e endereço de disco e olhar o resultado em uma tabela de espalhamento. Todos os blocos com o mesmo valor de espalhamento são encadeados em uma lista de maneira que a cadeia de colisão possa ser seguida.

Passos do funcionamento da cache: 
1. Confere para ver se o bloco requerido está na cache.
2. Se estiver, o pedido de leitura pode ser satisfeito sem acesso ao disco.
3. Se o bloco não estiver, primeiro ele é lido na cache e então copiado para onde quer que seja necessário

Todos os algoritmos de substituição de páginas também podem ser aplicados nesse contexto. Nesse sentido, o LRU é o mais utilizado, na qual há uma lista bidirecional ligando todos os blocos na ordem de uso. Quando um bloco é referenciado, ele pode ser removido da sua posição na lista bidirecional e colocado no fim. Dessa maneira, a ordem do LRU exata pode ser mantida.
##### Leitura antecipada de blocos
Uma segunda técnica para melhorar o desempenho percebido do sistema de arquivos é tentar transferir blocos para a cache antes que eles sejam necessários para aumentar a taxa de acertos. Quando se pede a um sistema de arquivos para obter o bloco k em um arquivo, ele o faz, mas quando termina, faz uma breve verificação na cache para ver se o bloco k + 1 já está ali. Se não estiver, ele programa uma leitura para o bloco k + 1 na esperança de que, quando ele for necessário, já terá chegado na cache. No mínimo, ele já estará a caminho.

- Funciona somente para arquivos que estão sendo lidos de forma sequencial.

Se os arquivos estiverem dispostos de forma aleatória a leitura antecipada pode acabar atrasando o processo, cabendo assim associar um bit a cada arquivo aberto para monitorar se o arquivo está em acesso sequencial ou aleatório. Dessa maneira, será possível saber quando utilizar a leitura antecipada.

```ad-important
##### Fragmentação Externa
Em um sistema operacional trabalhando com alocação contígua de memória, quando há memória suficiente para o atendimento de um pedido de alocação, mas esta memória não é contígua.

- os SSDs não sofrem de maneira alguma com a fragmentação.
```

```ad-important
##### Fragmentação Interna
É definida quando em um sistema operacional trabalhando com alocação contígua de memória, a memória alocada por um processo não é completamente utilizada.
```

```ad-important
##### Desfragmentação 
Reorganiza os dados, movendo os arquivos fragmentados para locais contíguos no disco e consolidando o espaço livre em regiões também contíguas.
```

```ad-important
##### Compactação
Um processo demorado realizado pelo **S.O**. que combina todos os buracos formados na memória em um mesmo bloco contíguo.
- É raramente utilizada devido a grande utilização de **CPU** requerida.
```
#### Exemplos de Sistemas de Arquivos
#### NTFS 
Sistema de arquivos padrão do Windows, oferece recursos como criptografia, journaling, permissões e suporte a partições e arquivos grandes. Cada volume do NTFS (por exemplo, a partição do disco) contém arquivos, diretórios, mapas de bits e outras estruturas de dados. Cada volume é organizado como uma sequência linear de blocos.

- Permite nomes de arquivos com até 255 caracteres (não permitidos: **\ / | < > * : ?**, CON, LPT1, AUX)
- Pode operar em um ambiente heterogêneo com diferentes computadores, sistemas operacionais e arquiteturas de rede.
##### MFT
A principal estrutura de dados, cada volume é a MFT (Master File Table — Tabela mestra de arquivos), que é uma sequência linear de registros com tamanho fixo de 1 KB.
- Cada registro da MFT descreve somente um arquivo ou um diretório. (O registro contém atributos do arquivo, como seu nome e sua estampa de tempo e a lista de endereços de disco onde seus blocos estão localizados)
- Podem existir vários para controle de arquivos extremamente grandes.
#### EXT
Sistema de arquivos padrão do Linux, com suporte a criptografia, journaling, permissões e suporte a partições e arquivos grandes. Sistema de arquivo baseada na estruturação do tipo indexada.
 ## EXT2
 Feito para superar a limitação do sistema de arquivos Ext, não possui um recurso de registro no diário, possui um limite máximo podendo ser de até 32TB, dependendo do tamanho do bloco, e é recomendado para unidades flash e USB 
 ## EXT3
 Melhora na confiabilidade, novo sistema de journaling, suporte a crescimento do sistema de arquivos online e indexação de grandes diretórios HTree.
 ## EXT4
 Foi introduzido inicialmente para estender os limites de armazenamento e melhorar o desempenho do sistema. É  suportado por outros sistemas operacionais, incluindo Windows, Free BSD, macOS e KolibriOS (somente leitura).
#### ReiserFS
Projetado para sistemas Linux e foi um dos primeiros sistemas de arquivos a oferecer suporte a jornalização (journaling) em Linux. Ele era conhecido por sua eficiência na manipulação de muitos pequenos arquivos e sua rápida recuperação após falhas do sistema, devido à sua estrutura de jornal.
#### ReFS (Resilient File System)
É o sistema de arquivo mais recente desenvolvido pela Microsoft; foi introduzido no Windows 8. Sua arquitetura difere dos outros sistemas de arquivos do Windows por ser organizada na forma de árvore B+, dimensionar de modo eficiente conjuntos de dados muito grandes em diversas cargas de trabalho e fornecer integridade dos dados com resiliência a danos.
#### XFS (Extended File System)
Criado para ser usado nos servidores da empresa Silicon Graphics. Em 2001, foi integrado ao Kernel do Linux e, atualmente, é suportado pela maioria das distribuições Linux. Trata-se de um sistema de arquivo otimizado para suportar arquivos e volumes muito grandes (8 Exabytes).
#### FAT (File Allocation Table)
Foi desenvolvido para o MS-DOS e usado em versões do Windows até o Windows 95. A maioria dos sistemas operacionais suportam esse sistema de arquivos. Utiliza alocação do tipo encadeada.
- exFat - extensão da Microsoft para o FAT-32 que é otimizado para flash drives e sistemas de arquivos **MUITO** grandes.
- Fat16 -  limita a partições de disco não maiores que 2 GB.
- Fat32 - Suporta partições de até 2TB e arquivos de até 4GB, não há segurança, utilizado somente para mídias portáteis. 

```ad-abstract
##### VFAT (Virtual File Allocation Table)
É uma extensão para os sistemas de arquivos FAT16 e FAT32 o incluída a partir do Windows 95 e suportado também no Linux e outros sistemas.
```
#### JFS (Journaladed File System)
Sistema de arquivos desenvolvido pela IBM, inicialmente para uso em sistemas AIX e posteriormente portado para outras plataformas, incluindo OS/2 e Linux. É conhecido por sua confiabilidade e desempenho, especialmente em ambientes de servidor, onde a integridade dos dados é crucial.
#### HPFS (High Performance File System)
Sistema de arquivos desenvolvido pela IBM especificamente para seu sistema operacional OS/2. Foi projetado para superar as limitações do sistema de arquivos FAT (File Allocation Table), oferecendo melhor desempenho e suporte a recursos avançados, como nomes de arquivos longos e tamanhos de arquivos maiores.
# Princípios de E/S (I/O)
Além de oferecer abstrações como processos, espaços de endereçamentos e arquivos, um sistema operacional também controla todos os dispositivos de E/S (entrada/saída) do computador. Fornecendo uma interface entre os dispositivos e o resto do sistema que seja simples e fácil de usar.
#### Dispositivos de E/S
##### Dispositivos de Blocos 
Armazena informações em blocos de tamanho fixo, cada um com seu próprio endereço. Todas as transferências são em unidades de um ou mais blocos inteiros (consecutivos).
- Discos rígidos, discos Blu-ray e pendrives são dispositivos de bloco comuns.
##### Dispositivos de Caractere
Um dispositivo de caractere envia ou aceita um fluxo de caracteres, desconsiderando qualquer estrutura de bloco. Ele não é endereçável e não tem qualquer operação de busca.
-  Impressoras, interfaces de rede, mouses (para apontar) e a maioria dos outros dispositivos que não são parecidos com discos podem ser vistos como dispositivos de caracteres.
#### Modos de Transferência
##### E/S Programada
Cada transferência de item de dados é iniciada por uma instrução no programa. Normalmente, a transferência é de um registro e memória da CPU. Neste caso, requer monitoramento constante pela CPU dos dispositivos periféricos.
- É responsabilidade do processador verificar periodicamente o estado do módulo, para ver se a operação foi completada. 
- É muito custoso para a CPU.
##### Interrupção
A interface emite um sinal de solicitação de interrupção sempre que houver dados disponíveis de qualquer dispositivo. Processador efetua a transferência de dados e depois retorna ao seu processamento original.

- É mais eficiente que a E/S programada, pois elimina ciclos de espera desnecessários.
- Elas precisam ser tratadas pelo sistema operacional (SO)
##### DMA (Direct Memory Access) 
É uma técnica de transferência de dados que permite que dispositivos periféricos acessem diretamente a memória do sistema. Ele tem acesso ao barramento do sistema. Ele contém vários registradores que podem ser escritos e lidos pela CPU. Esses incluem um registrador de endereço de memória, um registrador contador de bytes e um ou mais registradores de controle. 

- Independente da CPU.
- Imita o processador nas funções de E/S de dados.

![[so-dma.png]]

O controlador de DMA pode operar das seguintes maneiras:
1. Usando o barramento apenas quando o processador não o utiliza.
2. Forçando o processador a suspender temporariamente sua operação – técnica conhecida como roubo de ciclo.
#### Spooling 
técnica usada em sistemas operacionais para lidar com dispositivos de E/S dedicados em um ambiente de multiprogramação. Ele permite que processos de usuário enviem suas tarefas para uma fila, liberando assim os recursos e permitindo que outros processos continuem sem interrupções. O spooling envolve a criação de um processo especial chamado "daemon" para gerenciar a E/S dos dispositivos. Esse daemon é responsável por acessar os arquivos na fila de spooling e executar as operações necessárias nos dispositivos de E/S.
# Linux

![[so-linux.png]]
#### Sistemas de Arquivos
Por padrão, o Linux pode suportar diversos sistemas de arquivos em diversas partições de disco. Para gerenciar isso o Linux utiliza o VFS [[caixa concurso/Sistemas Operacionais#VFS (Virtual File System — sistema de arquivos virtuais)|(Sistema Virtual de Arquivos)]] para lidar com múltiplos sistemas de arquivos.
##### Estrutura de Arquivos
- /var - logs, filas de impressão, filas de e-mail e outros arquivos mantidos dinamicamente pelo sistema.
- /proc - diretório virtual, arquivos servem como ponto de acesso para uma série de variáveis e recursos do sistema
- /usr - hierarquia de diretórios, comandos de usuário, código fonte, documentação
- /etc -  arquivos de configuração do sistema
- /bin - Programas binários (executáveis)
- /dev - Arquivos especiais para dispositivos de E/S 
##### Principais sistemas de arquivos utilizados no Linux
- Ext4 (Sistema de arquivos Padrão)
- XFS (Lida com grandes volumes de dados)
- BTRFS (Usado em servidores de rede e backup)
- ZFS (Altamente resistente a falhas)
#### Comandos
fdisk, cfdisk: manipula ou mostra tabela de partição de um dispositivo.
df: Mostra a informação de utilização do disco para sistema de arquivos montados e diretórios
cat: Concatena vários arquivos para a saída-padrão
cp: Copia um ou mais arquivos
cut: Corta colunas de texto de um arquivo
grep: Procura um certo padrão dentro de um arquivo
head: Extrai as primeiras linhas de um arquivo
ls: Lista diretório
make: Compila arquivos e constrói um binário
mkdir: Cria um diretório
paste: Cola colunas de texto dentro de um arquivo
ps: Lista os processos em execução
rm: Remove um ou mais arquivos
rmdir: Remove um diretório
sort: Ordena um arquivo de linhas alfabeticamente
tail: Extrai as últimas linhas de um arquivo
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
# Windows
![[so-windows.png]]
#### Sistemas de Arquivos
[[caixa concurso/Sistemas Operacionais#Exemplos de Sistemas de Arquivos|NTFS]] é o sistema de arquivos padrão do Windows.

```ad-attention
sistemas distribuídos: http://profs.ic.uff.br/~simone/sd/contaulas/
```