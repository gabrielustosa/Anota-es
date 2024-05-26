# Fluxo de caixa de operações
O fluxo de caixa de uma operação é uma representação esquemática muito útil na resolução de problemas. Basicamente, consta de um eixo horizontal em que é marcado o tempo, a partir de um instante inicial 0 (origem). As entradas de dinheiro em um determinado instante são indicadas por setas perpendiculares ao eixo horizontal, no instante considerado, e orientadas para cima; as saídas de dinheiro são indicadas da mesmo forma, só que a orientação das setas é para baixo;

![[matf-fluxo-dc.png]]

```ad-info
**VP** - **Valor presente** é o primeiro valor aplicado no gráfico (definido como despeza).
**VF** - **Valor futuro** é o último valor somando a receita aplicada mais os ganhos entre o eixo.
```

```ad-info
**Ano civil**, que tem 365 (ou 366) dias, e cada mês tem seu número real de dia é o **juros exato**.
**Ano comercial**, que tem 360 dias, e o mês comercial tem 30 dias é o **juros comercial**.
```

```ad-summary 
#### Formula de juros acumulados
$$
[(i + 1) * (2i * 1)...] - 1 * 100
$$
```

```ad-tip
##### Fórmula de equivalência de juros compostos
$$
(1 + i)^\frac{q}{t} - 1
$$
q = juros que eu quero transformar 
t = juros que eu tenho

Exemplo: transforme uma taxa de 2% mensal para trimensal:

$$
(1 + 0,02)^\frac{3}{1} - 1 = 1,02^3 - 1 = 0,0612
$$
```
# Descontos
#### Simples Comercial ou Por Fora
O desconto é calculado sobre o valor nominal do produto ou serviço.
$$
DC = N . i . t
$$
$$
 A = N . (1 – i.t)
$$
**DC** = desconto comercial
**N** = valor nominal
**i** = taxa
**t** = tempo
**A** = valor atual
#### Racional Composto ou Por Dentro
O desconto é calculado sobre o valor atual do produto ou serviço.
$$
Dr = A . i . t
$$
$$
A = \frac{N}{(1 + i)^t}
$$
**Dr** = desconto racional
**N** = valor nominal
**i** = taxa
**t** = tempo
**A** = valor atual

```ad-summary
 ##### Desconto composto
 Praticamente as mesmas fórmulas, trocando somente a formula do juros simples para o juros composto.
```

```ad-summary
##### Juros embutido
$$
\frac{VF - VP}{VP}
$$
```
### Taxa Variável
A taxa variável muda com o mercado. Se o índice que ela segue, como a SELIC, sobe, a taxa também sobe
##### Exemplo
Imagine que você pegou um empréstimo de R$ 1.000 com uma taxa nominal de 12% ao ano, capitalizada mensalmente. Usando a fórmula acima, a taxa efetiva mensal seria de 1%. Agora, se a taxa fosse variável e atrelada a um índice que subisse para 15% ao ano, sua taxa efetiva mensal seria ajustada para refletir essa mudança, podendo aumentar para algo em torno de 1,25% ao mês.

```ad-summary
##### Cálculo da Taxa sob a Inflação
$$
[\frac{1 + i}{1 + j} - 1]
$$
i = taxa nominal
j = taxa de inflação
##### Cálculo da Taxa sob a Deflação
$$
[(1 + i).(1 + d) - 1]
$$
i = taxa nominal
d = taxa de deflação
```
### SAC
Amortização é o valor da parcela menos o valor do juros do empréstimo, esse valor deverá ser constante.

$$
Jt = \frac{VP}{n}.(n-t+1).i
$$
$$
P(t) = am . [1+(n-t+1).i]
$$
### SAF (Tabela Price)
Similar ao SAC no entanto as prestações (amortização + juros) serão iguais e constates.

$$
P = \frac{VP.i.(1+i)^n}{(1+i)^n-1}
$$

O valor futuro aplica a fórmula:
$$
VF=\frac{P.(1+i)^n-1}{i}
$$

```ad-tip
armotização = ^t-1 em cima
```