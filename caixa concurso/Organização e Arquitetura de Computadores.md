# Hierarquia de Memória
#### Princípios da localidade
1. Temporal: Refere-se à tendência de um processador acessar locais de memória que foram usados recentemente. Por exemplo, durante a execução de um laço de instruções
2. Espacial Refere-se à tendência de a execução de um programa envolver uma série de locais de memória que estão próximos; Os caches utilizam esse conceito para tirar salvar estados acessados recentemente.
3. Sequencial:  Técnica de referência à posição seguinte (listas encadeadas)
#### Níveis
```mermaid
--- 
title: Principais níveis de hierarquia
---

flowchart LR
cpu(Registradores)  --> cache(Cache) -->  ram(Memória RAM) -->  IO("Dispositivos I/O (HD/SSD)")
```

* Cache (ou S-RAM) são memórias de acesso rápido gerenciadas pelo hardware do processador (L1, L2, ...) L1 mais próxima da CPU, capacidade menor, invisíveis para programas e o sistema operacional.
* RAM (ou D-RAM) é uma memória de acesso aleatório para armazenar dados de processos ativos do sistema operacional.
#### Memória Cache
O objetivo da cache é armazenar dados e instruções que o processador provavelmente precisará em breve, baseando-se no princípio de localidade, que observa que programas tendem a acessar os mesmos dados ou instruções repetidamente em um curto período de tempo.

- O principal impacto da memória cache no desempenho do processador é a redução do retardo (latência).
#### Memória Flash
Tipo de memória não volátil usada para armazenamento e transferência de dados. Utiliza células de memória que podem ser eletricamente apagadas e reprogramadas.
##### Tipos 
- NAND: Alta capacidade e custo-benefício, usado em SSDs, cartões de memória.
- NOR: Acesso rápido e aleatório, usado em firmware.
- RAM: NÃO VOLÁTIL, de modo que, mesmo que o sistema perca a energia, a memória flash se lembrará do que foi gravado nela.
- FLASH ROM:  Similar a EEPROM, Apaga mais rapidamente, **NÍVEL BLOCO (Rápido).**

```ad-info
A memória Flash deve ser apagada antes que seja sobrescrita, e isso deve ser feito em blocos (em memórias Flash de alta densidade, chamadas NAND Flash) em vez de bytes ou palavras individuais. Isso significa que, quando dados precisam ser gravados em uma memória Flash, todo um bloco deve ser montado, seja como um bloco de dados novos, seja mesclando os dados a serem gravados e o resto do conteúdo do bloco.
```
# CPU
#### UC (Unidade de Controle)
Responsável pelo controle de operações da CPU, ela busca e decodifica instruções armazenadas na memória, controlando o fluxo de dados
de entra e saída e outros componentes. 

 ##### Controlador
 Lê a instrução que está em RI, decodifica e ativa sequencialmente os sinais de controle apropriados.
#### ULA (Unidade Lógica e Aritmética)
Realiza operações aritméticas e operações lógicas (AND, OR, NOT) com dados binários.

```ad-info
 Palavra representa um conjunto de Bytes. 
```
#### Registradores
Pequenas porções de memória volátil e de alta velocidade que estão dentro da própria CPU que armazenando n bits.

 ##### Registrador de Instrução (IR) - UC
 Responsável por armazenar a instrução que está sendo executada.
 ##### Contador de Programa (PC) - UC
 Armazena o endereço da próxima instrução a ser executada. Sendo incrementada pela **Unidade de Controle (UC)** após a execução de uma instrução.
 ##### MBR - ULA
 Armazena o conteúdo de uma palavra de memória que foi lida ou será gravada.
 ##### MAR - ULA
 Especifica o endereço, na memória, da palavra a ser escrita ou lida no **MBR**.
#### Barramento 
Vias de comunicação que facilita a transferência de dados entre diferentes componentes da CPU e outros dispositivos do sistema.

 ##### Barramento de endereços
 Indica a posição de memória (ou dispositivo) a acessa.
 ##### Barramento de controle
 Indica a operação a efetuar (leitura ou escrita).
 ##### Barramento de dados
 Transporta a informação a ser transferida entre o processador e a memória ou um controlador de dispositivo.
# Armazenamento e Representação de Instruções
 ##### Ciclo das instruções 
  1. Trará a Instrução da memória principal (**PC**) para o registrador de instrução (**IR**). (busca)
  2. Decodificará a instrução, obtendo os operandos da memória, e armazenando-os na memória cache. (decodificação)
  3. Gerará o endereço de memória, transfere para os registradores do **ULA** e utilizará o barramento de dados para obter os operandos da instrução.

```mermaid
flowchart LR
op[Recebe a operação] --> an["Análisa o operando"] ---> de["Destino do operando I/O"] ---> p[Recebe próxima instrução]
```

```ad-tip
**Paridade:** Método de verificação de erro que adiciona um bit adicional a um conjunto de bits para garantir que o número total de bits de valor "1" seja par ou ímpar, ajudando na detecção de erros de transmissão.
```
#### Armazenamento 
O armazenamento das instruções é inicialmente na memória RAM e depois é repassado para os registrados no processo de análise das instruções conforme necessário.
#### Representação
Instruções são representadas por mnemônicos como **ADD**, **SUB**, **LOAD**, **MOVE** 
# Modos de endereçamento
#### Imediato
Operador especificado na instrução: **ADD R1, #10** (adiciona o valor **10** no registrador **R1**)
 ##### OPERANDO LIMITADO, RÁPIDO E NÃO REQUER MEMÓRIA
#### Direto
O endereço do operando é dado na instrução, utilizando somente 1 endereço: **LOAD R1, 2000** (carregar o valor armazenado no endereço **200** no registrador **R1**)
 ##### SIMPLES, ESPAÇAMENTO DE MEMÓRIA LIMITADO
#### Indireto
O endereço efetivo é contido na memória referenciada no campo do operando: **MOV R2, (1)** (o conteúdo armazenado no endereço **1** é movido para o registrador **R2**, funciona como um ponteiro onde o registrador **R2** apontará para o endereço **1**)
 ##### ESPAÇO DE ENDEREÇAMENTO GRANDE, MULTIPLAS REFERÊNCIA DE MEMÓRIA
#### Registrador 
Semelhante ao direto porém é utilizado a referência de um registrador invés de um endereço de memória: **MOV R2, R1**  (o conteúdo de **R2** é movido e somado ao registrador **R1**)
 ##### NENHUMA REFERÊNCIA EM MEMÓRIA, ESPAÇO DE ENDEREÇAMENTO LIMITADO 
#### Registrador indireto
Semelhante ao indireto porém é utilizado a referência de um registrador.
 ##### ESPAÇO DE ENDEREÇAMENTO GRANDE, ALTA REFERÊNCIA DE MEMÓRIA
#### Deslocamento
Combina recursos do direto e registrador indireto, sendo eficiente pois não necessita de informar endereços de memória absolutos : **LOAD R1, 100(B)** 
 ##### FLEXÍVEL, COMPLEXO
#### Pilha
Funciona como a estrutura de dados Pilha. **PUSH**, **POP** 
 ##### NENHUMA REFERÊNCIA A MEMÓRIA, LIMITADA
##### Outros
1. Auto-Incremento (útil para estruturas de dados sequenciais)
2. Auto-Decremento (útil para pilhas ou lista de dados inversas)
3. Indexado (manipulação de arrays, vetores) - **MOV R1, A(R2)**
4. Relativo (relacionado ao PC, calculando sempre a próxima instrução)