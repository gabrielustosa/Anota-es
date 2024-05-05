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
#### Simples Racional ou Por Dentro
O desconto é calculado sobre o valor atual do produto ou serviço.
$$
Dr = A . i . t
$$
$$
A = \frac{N}{(1 + i.t)}
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