# Java
#### Overload e Override
- Overload: Escrever vários métodos com o mesmo nome mas com parâmetros diferentes.  
- Override: Escrever o mesmo método, com os mesmos parâmetros. Ou seja, é uma anulação de um método herdado, para fazer o seu especifico.
#### POO
- **Encapsular**: Proteger os dados do acesso direto, controlando a forma como são acessados e modificados, **getter** e **setter**. 
- **Polimorfismo**: permite que objetos de diferentes classes respondam a uma mesma mensagem (ou método) de diferentes maneiras.
#### Ordem de acrescimento de variáveis
- ++i: O valor é acrescentado imediatamente 
- i++: O valor continua o mesmo e será incrementado na próxima linha de execução.
#### Ordem de execução de variáveis
- Atributos/Blocos estáticos (Tem ordem de prioridade máxima, executa-se do pai até o último filho antes dos outros passos)
- Atributos de instância (Atributos com o mesmo nome na classe pai e filho são sobrescritos agindo como nova variável em cada classe)
- Blocos anônimos 
- Construtor (Construtor vazio da classe pai é chamado mesmo sem a chamada super)

Para cada item, verificar a classe pai e depois a classe filha.

```java
class MnopA {
    static int x = 10, y = 10, z = 10; // Primeiro

    public MnopA() { // Quarto
        x *= 2;
    }

    { // Terceiro
        y += 5;
        z += 10;
    }
}

class MnopB extends MnopA {
    public MnopB(int c) { // Sexto
        y *= c;
    }

    { // Quinto
        z += y;
    }

    static { // Segundo
        x = y = z = 1;
    }
}

public class Main {
    public static void main(String[] args) {
        MnopB o = new MnopB(2);
        System.out.println(MnopB.x + MnopB.y + MnopB.z);
    }
}

```
#### Classes Abstratas 
Funcionam como uma espécie de contrato para a firmação de métodos ou variáveis.

- Métodos definidos como abstratos não podem possuir um corpo, apenas uma definição de contrato que será exigida.
#### Interfaces
Como no Java não é possível estender duas classes a interface é necessária caso haja a necessidade de firmar um contrato com mais de duas classes, dessa forma toda interface é por padrão abstract.

- Define apenas a assinatura de métodos.
- Todas as variáveis devem ser obrigatoriamente públicas e estarem inicializadas.
- Todas as variáveis definidas são final, não podendo ser alteradas.
- Apenas métodos default ou estáticos poderão ser definidos com corpo.
- Interfaces estendem e não implementam outras interfaces.
- Interfaces não podem ser finais.
#### Estruturas e Classes Padrão
Tipos de criação de arrays. 

```java
int[] array = {1, 2, 3};
int[] array = new int[]{1, 2, 3};
int[] array = new int[]{5}; // 5 será o tamanho máximo do array

for (int valor : array) {
	System.out.println(valor);
}

Arrays.stream(array).forEach(Sytem.out::println);
```

Random

``` java
Random r = new Random();
r.nextInt(5) // gera 5 valores de 0-5
```
# Python
#### Slicing
sintaxe `sequencia[inicio:fim:passo]`, onde:

- `inicio` é o índice onde o slice começa (inclusivo).
- `fim` é o índice onde o slice termina (exclusivo, ou seja irá até o número informado -1).
- `passo` é o número de índices a serem pulados.

```python
lista = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# Slice do índice 2 ao 5
print(lista[2:5])  # Saída: [2, 3, 4]

# Slice do início até o índice 5
print(lista[:5])  # Saída: [0, 1, 2, 3, 4]

# Slice do índice 5 até o final
print(lista[5:])  # Saída: [5, 6, 7, 8, 9]

# Slice completo da lista
print(lista[:])  # Saída: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

# Slice com passo 2
print(lista[::2])  # Saída: [0, 2, 4, 6, 8]

# Slice negativo para inverter a lista
print(lista[::-1])  # Saída: [9, 8, 7, 6, 5, 4, 3, 2, 1, 0]

```
#### Numpy
Biblioteca de gerenciamento de vetoriais com suporte algébricos utilizando um sistema conhecido como broadcast.

```python
import numpy as np
  
a = np.array([1, 2, 3])
a / 2 # array([0.5, 1, 1.5])
a * 3 # array([3, 6, 9])

# Os operadores de comparação ==, !=, >, >=, < e <=, ou operadores matemáticos.
# quando utilizados sobre arrays, são aplicados em cada posição dos mesmos.
a = np.array([1, 2, 3, 4, 5, 6, 7, 8, 9])
a[(a > 5) & (a <= 8)] # [6, 7, 8]
a[a % 2 == 0] # [2, 4, 6, 8]
# resultados boleanos a == 1, resultados literais a[a == 1]
a == 1 # [True False False False False False False False]
a[a == 1] # [1]

a = np.array([[10, 9, 8], [1, 2, 3]])  
# linha 1, index 2
a[0, 2] # 8

matriz = np.array([[  
[1, 2, 3],  
[4, 5, 6],  
[7, 8, 9],  
]])  
# linha 1, coluna 2, index 1 até o 2  
matriz[0, 1, 1:3] # [5, 6]

# valores dimensionais de uma array
a.shape # (3,)

a = array([[1, 2, 3], [4, 5, 6]])
a.shape # (3, 2) 3 lihas e 2 colunas

range_array = np.arange(12).reshape(3, 4) # [
#   [0, 1, 2, 3],
#   [4, 5, 6, 7],
#   [8, 9, 10, 11],
# ]

# de 2 a 10 com 5 elementos
a = np.linspace(2, 10, 5) # [2, 4, 6, 8, 10]

# Transposição de matrizes (inverter linhas pelas colunas)
matriz = np.array([
	[1, 2, 3],
	[4, 5, 6],
	[7, 8, 9],
])

matriz.T # array([
#	[1, 4, 7],
#	[2, 5, 8],
#	[3, 6, 9],
# ])

a = np.array([[1, 2], [3, 4]])
a.T # array([
#   [1, 3],
#   [2, 4],
# ])

# python: operações vetoriais, cada elemento é multiplicado.
# numpy: operações matricial, somente elementos relacionados por col/linha são multiplicados e somados.
a = np.array([1, 2, 3]) 
b = np.array([4, 5, 6]) 
a * b # [4, 10, 18] pois [1*4, 2*5, 3*6]

# vetor x vetor
a = np.array([1, 2, 3]) 
b = np.array([4, 5, 6]) 
np.dot(a, b) # 32 pois 1*4 + 2*5 + 3*6 = 32

# matriz x vetor
a = np.array([[1, 2], [3, 4]]) 
b = np.array([5, 6]) 
np.dot(a, b) # [17 39] pois [1*5 + 2*6, 3*5 + 4*6] = [17, 39]

# matriz x matriz
a = np.array([[1, 2], [3, 4]]) 
b = np.array([[5, 6], [7, 8]]) 
np.dot(a, b) # [[19 22], [43 50]] pois [[1*5 + 2*7, 1*6 + 2*8], [3*5 + 4*7, 3*6 + 4*8]]
# 1 2 . 5 6  
# 3 4 . 7 8

a = np.array([[1, 2], [3, 4]])
sum(a) # [4, 6]
a.sum() # 10
# soma as colunas
a.sum(axis=0) # [4, 6]
# soma as linhas 
a.sum(axis=1) # [3, 7]
```

#### Pandas
##### Tipos

![[pg-pandas-t.png]]

```python
import pandas as pd  
  
dados = [('Ana', 21), ('Bruno', 20), ('Carla', 22)]  
colunas = ['Nome', 'Idade']  
indicies = ['A', 'B', 'C']
df = pd.DataFrame(data=dados, columns=colunas, index=indicies)  
df #     Nome  Idade
#   A    Ana     21
#   B  Bruno     20
#   C  Carla     22
df.size # 6
df.T  # transposição (trocar linhas por colunas)
#      A      B     C
# Nome Ana Bruno Carla
# Idade 21  20   22

data = {'x': [1, 2, 3], 'y': [3, 7, 11], 'z': [False, True, False]}  
df = pd.DataFrame(data)
#    x   y      z
# 0  1   3  False
# 1  2   7   True
# 2  3  11  False

# dataframe[<coluna>][<linha>]
df['Nome'][1] # Bruno
# index 1, coluna Nome
df.at['A', 'Nome'] # Bruno
# linha 1, coluna 2
df.iat[0, 1] # 21

# indexes 1, 2
df.loc[[B, C]] 
#   Nome Idade 
# B Bruno 20 
# C Carla 22
		       
# somente o primeiro e último resultado da coluna Nome
# df.loc ou somente df[[True, False, True]]
df.loc[[True , False , True], 'Nome']
# A Ana
# C Carla

# linhas de index 1, 2
df.iloc[[1, 2]] 
#   Nome Idade 
# B Bruno 20 
# C Carla 22

# linhas de index 0, 2 somente a coluna 0 (Nome)
df.iloc[[0, 2], 0]
# A Ana 
# C Carla

# somente linhas -2 até o final e coluna 1 até o final
df.iloc[-2:,1:]
#    Idade
# B     20
# C     22

# df[<nova coluna>] = <valor padrão> ou [valor_pd_1, valor_pd_2, ...]
df['Sexo'] = ['F', 'M', 'F']
# Nome Idade Sexo
# A Ana   21 F 
# B Bruno 20 M
# C Carla 22 F

# também funciona com iloc
df.loc['A'] = ['Gabriel', 20, 'M'] 
# A  Gabriel     20    M
# B    Bruno     20    M
# C    Carla     22    F

# também funciona com iat
df.at['A', 'Idade'] = 32
#    Nome  Idade Sexo
# A    Ana     32    F
# B  Bruno     20    M
# C  Carla     22    F

# inplace determina se as mudanças devem ser aplicadas diretamente no DataFrame ou em uma cópia
df.drop(index=['A'], columns=['Sexo'], inplace=True) 
#    Nome  Idade
# B  Bruno     20
# C  Carla     22

# os operadores aritméticos serão aplicados em todas as colunas.
df['Idade'] * 2 
#    Nome  Idade Sexo
# A    Ana     42    F
# B  Bruno     40    M
# C  Carla     44    F

list(df['Idade'] >= 21) # [True, False, True]
resultado = list(df['Sexo'] == 'F') # [True, False, True]
df.loc[resultado]
#     Nome  Idade Sexo
# A    Ana     21    F
# C  Carla     22    F

df.sort_values(by='Idade', ascending=False, inplace=True)
#     Nome  Idade Sexo
# C  Carla     22    F
# A    Ana     21    F
# B  Bruno     20    M

df.Idade.count() # 4
df.Idade.sum() # 63
df.Idade.min() # 20
df.Idade.max() # 22

df.head() # primeiros elementos
df.tail() # últimos elementos
df.describe() # notações matemáticas e estastícas.

# Series (Vetores heterogêneos)
lst_matriculas = ['M02','M05','M13','M14','M19']
lst_nomes = ['Bob','Dayse','Bill','Cris','Jimi']

notas = pd.Series([7.6, 5.0, 8.5, 9.5, 6.4])
alunos = pd.Series(lst_nomes,index=lst_matriculas)
# M02      Bob
# M05    Dayse
# M13     Bill
# M14     Cris
# M19     Jimi
# dtype: object

alunos[[2,0,4]] # {M13:Bill, M02:Bob, M19:Jimi}
alunos[['M13','M02','M19']] # {M13:Bill, M02:Bob, M19:Jimi}

idx_aprovados = notas[notas >= 7].index # indícies das notas maiores ou iguais a 7
alunos[idx_aprovados]
# M02 Bob
# M13 Bill
# M14 Cris
# dtype: object

alunos.isin(['Bob'])
# M02 True
# M05 False
# M13 False
# M14 False
# M19 False
# dtype: bool

verde = pd.Series({'FR': 2, 'BR':1, 'IT':1, 'UK': 0})
azul = pd.Series({'AR':1, 'BR':1, 'FR': 1,  'IT':0, 'UK': 1})
soma = verde + azul
# AR NaN
# BR 2.0
# FR 3.0
# IT 1.0
# UK 1.0
# dtype: float64

# Índicies Hierarquicos 
moedas = ['Peso', 'Real', 'Euro', 'Euro', 'Libra']
paises = [['América','América','Europa','Europa','Europa'], ['AR','BR','FR','IT','UK']]
paises = pd.Series(moedas, index=paises)
paises['América'] # {AR: Peso, BR:Real}
paises[:,'IT'] # {Europa: Euro} (Isso é um filtro)
paises['Europa','IT'] # Euro
``` 
#### Matplotlib 

![[pg-matplot.png]]
##### Figure
O conjunto completo. Mantém o controle de todos os `Axis` filhos, um grupo de `Artist` (títulos, legendas de figuras, barras de cores, etc.), e até mesmo `subfigures` aninhadas.

A maneira mais fácil de criar uma nova Figura é com o `pyplot`:

```python
fig = plt.figure() # uma figura vazia sem Axes
```

``` python
fig, ax = plt.subplots() # uma figura com um único Axes
```

![[pg-matplot-ex-1.png]]

```python
fig, axs = plt.subplots(2, 2) # uma figura com uma grade 2x2 de Axes
```

![[pg-matplot-ex-2.png]]

```python
# uma figura com um Axis à esquerda e dois à direita: 
fig, axs = plt.subplot_mosaic([['esquerda', 'direita_topo'], ['esquerda', 'direita_fundo']])
```

![[pg-matplot-ex-3.png]]
##### Axes
Tipo de elemento visual conectado a uma `Figure` que contém uma área para plotar dados. Geralmente, ele inclui dois `Axis` (ou três no caso de gráficos 3D) que fornecem marcas e rótulos de marcação para escalar os dados no `Axis`. É importante diferenciar entre `Axis` e `Axes`. Cada `Axis` também possui um título (definido com `set_title()`), um rótulo para o `axis-x` (definido com `set_xlabel()`), e um rótulo para o `axis-y` (definido com `set_ylabel()`).

A classe `Axes` e suas funções membros são o ponto de entrada principal para trabalhar com a interface de programação orientada a objetos (OOP) e têm a maioria dos métodos de plotagem definidos nelas.
##### Axis
Esses objetos definem a escala e os limites e geram marcas (as marcas no `Axes`) e rótulos de marcação (strings rotulando as marcas). A localização das marcas é determinada por um objeto Locator e as strings dos rótulos das marcas são formatadas por um Formatador. A combinação correta do Locator e do Formatador proporciona um controle muito preciso sobre a localização e os rótulos das marcas.

Resumindo, enquanto um `Axis` é um único eixo (x, y ou z), um `Axes` é a área completa onde os gráficos são desenhados, que contém todos os eixos necessários para plotagem.
##### Artist
Basicamente, tudo visível na `Figure` é um `Artist` (até mesmo objetos `Figure`, `Axis` e `Axes`). Isso inclui objetos Texto, objetos Line2D, objetos de coleções, objetos Patch, etc. Quando a `Figure` é renderizada, todos os `Artists` são desenhados no canvas. A maioria dos `Artists` está associada a um `Axis`; tal `Artist` não pode ser compartilhado por vários `Axes` ou movido de um para outro.
##### Exemplos

```python 
x = np.linspace(0, 2, 100) # Amostragem linear

fig, ax = plt.subplots(figsize=(5, 2.7), layout='constrained')
ax.plot(x, x, label='linear') # Plotando os dados no axes atual
ax.plot(x, x**2, label='quadratic') # Plotando quadraticos..
ax.plot(x, x**3, label='cubic') # Plotando cubicos...
ax.set_xlabel('x label') # Adionando um x-label para o axes.
ax.set_ylabel('y label') # Adionando um y-label para o axes.
ax.set_title("Simple Plot") # Adicionando um título para o axes.
ax.legend() # Adicionando uma legenda
```

![[pg-matplot-ex-4.png]]
# Cobol
Linguagem orientada a negócios. 

Código Cobol é divido em 4 seções:
1. Divisão de identificação;
2. Divisão de ambiente; 
3. Divisão de data;
4. Divisão de procedimentos;

```ad-info
Não existem variáveis locais, apenas globais.
```
#### Divisão de Identificação
O único atributo obrigatório dessa divisão é o atributo ID.

```cobol
      IDENTIFICATION DIVISION.
      PROGRAM-ID.    APRENDENDO.
      AUTHOR.        GABRIEL.
      DATE-WRITTEN.  22/05/2003.
```

#### Divisão de Ambiente
As variáveis são declaradas em uma seção chamada `WORKING-STORAGE` dentro da **Divisão de data**. Toda variável precisa começar com um número representando seu nível, depois o nome, seguido por uma diretiva `PIC` descrevendo o tipo de dado que a variável irá conter.

**A** é para variáveis de texto, **X** é para textos numéricos e **9** é para números;

```cobol
	01 MYNAME PIC xxxxxxxxxx. *> Uma string de 10 caracteres. 
	01 MYNAME PIC X(10). *> Simplificação da linha de cima.
	
	01 AGE PIC 9(3). *> Um número de até 3 dígitos.
	01 LAST_NAME PIC X(10). *> Uma sequência de até 10 caracteres.
```
##### Exemplos
```cobol
      IDENTIFICATION DIVISION.
      PROGRAM-ID. HELLO.
      DATA DIVISION.
      WORKING-STORAGE SECTION.
      01 THE-MESSAGE PIC X(20).
	      PROCEDURE DIVISION.
	      DISPLAY "INICIANDO PROGRAMA".
	      MOVE "HELLO WORLD" TO THE-MESSAGE.
	      DISPLAY THE-MESSAGE.
	      STOP RUN.
```

```cobol
      IDENTIFICATION DIVISION.
      PROGRAM-ID. HELLOCOBOL.

      PROCEDURE DIVISION.
	      FIRST-PARA.
		      DISPLAY 'THIS IS IN FIRST-PARA'.
	      PERFORM THIRD-PARA THRU FOURTH-PARA. *>skip second-para and perform 3rd & 4th
	      *> then after performing third and fourth,
	      *> return here and continue the program until STOP RUN.

      SECOND-PARA.
	      DISPLAY 'THIS IS IN SECOND-PARA'.
      STOP RUN.

      THIRD-PARA.
	      DISPLAY 'THIS IS IN THIRD-PARA'.

      FOURTH-PARA.
	      DISPLAY 'THIS IS IN FOURTH-PARA'.

	  *> Isso produz o seguinte resultado:
	  *> THIS IS IN FIRST-PARA
      *> THIS IS IN THIRD-PARA
      *> THIS IS IN FOURTH-PARA
      *> THIS IS IN SECOND-PARA 
```

```cobol
      IDENTIFICATION DIVISION.
      PROGRAM-ID. LEARNING.
      ENVIRONMENT DIVISION.
      DATA DIVISION.
      WORKING-STORAGE SECTION.
      01 FULL-NAME PIC X(20).
      01 FIRST-NAME PIC X(13) VALUE "BOB GIBBERISH".
      01 LAST-NAME PIC X(5) VALUE "COBB".
      PROCEDURE DIVISION.
	      STRING FIRST-NAME DELIMITED BY SPACE
	            " "
	      LAST-NAME DELIMITED BY SIZE
	           INTO FULL-NAME
	      END-STRING.
	      DISPLAY "THE FULL NAME IS: "FULL-NAME.
      STOP RUN.

      *output:
      THE FULL NAME IS: BOB COBB
```

```ad-summary
#### Tipos de comandos
- `ACCEPT` - entrada de variáveis. 
- `COMPUTE` - operação com varíaveis. `COMPUTE N3 = N1 +  N2`.
- `IF` - operação condicional, necessita de END-IF.
```
# TypeScript
Tipos básicos: `boolean`, `number`, `string`, `bigint`, `symbol`;

```ad-info
**let** palavra reservada para informar que a variável será acessivel somente dentro do escopo do local, não de forma global.
```

O TypeScript pode receber declaração de variáveis tanto da forma explicita como implícita, no qual adivinhará o tipo como `Duck Typing` no python.

Variáveis já tipadas não podem receber um valor diferente do seu tipo.

```typescript
let u = true;  
u = "string"; // Error: Type 'string' is not assignable to type 'boolean'.  
Math.round(u); // Error: Argument of type 'boolean' is not assignable to parameter of type 'number'.
```

Criando tipo customizado:
```typescript
type CarYear = number  
type CarType = string

const carYear: CarYear = 2001  
const carType: CarType = "Toyota"
```

É possível fazer casting: 
```typescript
let x: unknown = 'hello';  
console.log((x as string).length);
// ou
let x: unknown = 'hello';  
console.log((<string>x).length);
```

Criando variáveis genéricas:
``` typescript
type Wrapped<T> = { value: T };  
  
const wrappedValue: Wrapped<number> = { value: 10 };
```
#### Arrays
```typescript
const names: string[] = [];  
names.push("Dylan"); // no error
```

```ad-info
o atributo readonly pode ser adicionado em `const names: readonly string[] = ["Dylan"];`
```
#### Tuplas
```typescript
// definindo o formato da tupla
let ourTuple: [number, boolean, string];  
  
// inicializando corretamente
ourTuple = [5, false, 'Gabriel'];

// tupla nomeada 
const graph: [x: number, y: number] = [55.2, 41.3];
```
#### Objeto
```typescript
// objeto tipado
const car: { type: string, model: string, year: number } = {  
  type: "Toyota",  
  model: "Corolla",  
  year: 2009  
};

// objeto com propriedade opcional
const car: { type: string, mileage?: number } = {
  type: "Toyota"  
};  
car.mileage = 2000;
```
#### Função
```typescript
function multiply(a: number, b: number): number {  
  return a * b;  
}
```
##### Genérica
```typescript
function createPair<S, T>(v1: S, v2: T): [S, T] {  
  return [v1, v2];  
}  
console.log(createPair<string, number>('hello', 42)); // ['hello', 42]

function createLoggedPair<S extends string | number, T extends string | number>(v1: S, v2: T): [S, T] {  
  console.log(`creating pair: v1='${v1}', v2='${v2}'`);  
  return [v1, v2];  
}
```
####  Classe
```typescript
class Person {  
  // name é uma varíavel privada de Person
  public constructor(private name: string) {}  
  
  public getName(): string {  
    return this.name;  
  }  
}  
  
const person = new Person("Jane");  
console.log(person.getName());
```
##### Abstrata
```typescript
abstract class Polygon {  
  public abstract getArea(): number;  
  
  public toString(): string {  
    return `Polygon[area=${this.getArea()}]`;  
  }  
}  
  
class Rectangle extends Polygon {  
  public constructor(protected readonly width: number, protected readonly height: number) {  
    super();  
  }  
  
  public getArea(): number {  
    return this.width * this.height;  
  }  
}
```
##### Genérica
```typescript
class NamedValue<T> {  
  private _value: T | undefined;  
  
  constructor(private name: string) {}  
  
  public setValue(value: T) {  
    this._value = value;  
  }  
  
  public getValue(): T | undefined {  
    return this._value;  
  }  
  
  public toString(): string {  
    return `${this.name}: ${this._value}`;  
  }  
}  
  
let value = new NamedValue<number>('myNumber');  
value.setValue(10);  
console.log(value.toString()); // myNumber: 10
```
# Kotlin
Os tipos **numéricos** são: Byte, Short, Int, Long; **boleanos**: Boolean; Character; String.

Da mesma forma que o python as variáveis podem ser tipadas explicitamente ou de forma implícita por `DuckTyping`
```kotlin
fun main(nome: String = "Gabriel") {
  println("Hello World ${nome}")
}

var name = "John"
val birthyear = 1975

name = "Gabriel"
println(name)          // pode ser alterada
println(birthyear)     // não pode ser alterada

val list = mutableListOf(1, 2, 3)
for (l in list) {
	println(l)
}
```

```ad-tip
#### Extendendo funções

``` kotlin
class Example {
    fun printFunctionType() { println("Class method") }
}

fun Example.printFunctionType(i: Int) { println("Extension function #$i") }

Example().printFunctionType(1) // Extension function #1
```
#### When
Para ser usado no lugar de multiplos if-else.

```kotlin
val day = 4

val result = when (day) {
  1 -> "Monday"
  2 -> "Tuesday"
  3 -> "Wednesday"
  4 -> "Thursday"
  5 -> "Friday"
  6 -> "Saturday"
  7 -> "Sunday"
  else -> "Invalid day."
}

println(result) // Thursday 

```
#### Array
```kotlin
val cars = arrayOf("Volvo", "BMW", "Ford", "Mazda")
if ("Volvo" in cars) {
  println("existe!")
} else {
  println("não foi encontrado!")
}

for (x in cars) {
  println(x)
}
```
#### Range
```kotlin
for (chars in 'a'..'x') {
  println(chars)
}

for (nums in 5..15) {
  println(nums)
} 
```
#### Classe
```kotlin
class Car {
  var brand = ""
  var model = ""
  var year = 0
} 

val c1 = Car()

c1.brand = "Ford"
c1.model = "Mustang"
c1.year = 1969
```
##### Abstract
```kotlin
abstract class Polygon {
    abstract fun draw()
}

class Rectangle : Polygon() {
    override fun draw() {
        // draw the rectangle
    }
}
```
##### Herança 
```ad-info
Por padrão, as classes, atributos e funções em Kotlin são finais - elas não podem ser herdadas. Para tornar uma classe herdável, marque-a com a palavra-chave open:
```

```ad-info
Para sobrescrever métodos ou variáveis é obrigatório que o método que será sobrescito seja marcado com override. 
```

```kotlin
open class Base(p: Int)

class Derived(p: Int) : Base(p)
```

Exemplo mais complexo:

```kotlin
open class Rectangle {
    open fun draw() { /* ... */ }
}

interface Polygon {
    fun draw() { /* ... */ } // membros de uma interface são 'open' por padrão
}

class Square() : Rectangle(), Polygon {
    // O compilador requer que draw() seja sobrescrito:
    override fun draw() {
        super<Rectangle>.draw() 
        super<Polygon>.draw() 
    }
}
```

Propriedade customizada

```kotlin
class Rectangle(val width: Int, val height: Int) {
    val area: Int 
        get() = this.width * this.height
    // ou
	val area get() = this.width * this.height
}
```

Setter customizado:

```kotlin
class Exemplo {
	// ou 
    var contador: Int = 0
        set(value) {
            if (value >= 0)
                field = value
        }
}
```
#### Modificadores de visibilidade
`Internal`: estará visível em todos os lugares do mesmo módulo.

```ad-summary
##### Módulos

O modificador de visibilidade internal significa que o membro é visível dentro do mesmo módulo. Mais especificamente, um módulo é um conjunto de arquivos Kotlin compilados juntos, por exemplo:

- Um módulo do IntelliJ IDEA.
- Um projeto Maven.
- Um conjunto de origens do Gradle (com a exceção de que o conjunto de origens de teste pode acessar as declarações internas do principal).
- Um conjunto de arquivos compilados com uma invocação da tarefa <kotlinc> do Ant.
```
# Angular
Tudo é definido dentro do `<app-root>`

```typescript
import { Component } from '@angular/core';

@Component({
  selector: 'app-meu-componente',
  templateUrl: './meu-componente.component.html',
  styleUrls: ['./meu-componente.component.css']
})
export class MeuComponenteComponent {
  // Lógica e dados do componente
  titulo: string = 'Olá, Angular!';
}
```

Para utilizar o componente é preciso declara-lo no módulo `NgModule`:

```typescript
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { AppComponent } from './app.component';
import { MeuComponenteComponent } from './meu-componente/meu-componente.component';

@NgModule({
  declarations: [
    AppComponent,
    MeuComponenteComponent
  ],
  imports: [
    BrowserModule
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

```typescript
<button (click)="navigateToAbout()">Ir para a página Sobre</button>

export class HomeComponent {
  constructor(private router: Router) {}

  navigateToAbout() {
    this.router.navigate(['/about']);
  }
}

const routes: Routes = [
  { path: '', component: HomeComponent },
  { path: 'about/:id', component: AboutComponent }
];
```
#### Vinculações 
- **[(ngModel)]**:
    - **Tipo**: Vinculação bidirecional.
    - **Propósito**: Sincroniza valores entre controles de formulário e propriedades do componente.
    - **Uso**: Atualiza o valor do controle de formulário e a propriedade do componente simultaneamente.
- **[src]**:
    - **Tipo**: Vinculação de propriedade.
    - **Propósito**: Define dinamicamente o valor do atributo `src` de um elemento `<img>`.
    - **Uso**: Atualiza a URL da imagem conforme os dados do componente.
#### For
```typescript
<app-housing-location
  *ngFor="let housingLocation of housingLocationList"
  [housingLocation]="housingLocation">
</app-housing-location>
```
# AngularJS
AngularJS estende o HTML com `ng-directives`. 
- A `directiva ng-app` define uma aplicação AngularJS. 
- A `directiva ng-model` vincula o valor dos controles HTML (`input`, `select`, `textarea`) aos dados da aplicação. 
- A `directiva ng-bind` vincula os dados da aplicação à visualização HTML.

```html
<html>
  <script src="http://ajax.googleapis.com/ajax/libs/angularjs/1.3.14/angular.min.js"></script>
  <body>
    <div ng-app=""> <!-- diz ao AngularJS que o elemento <div> é o "proprietário" -->
      <p>Name: <input ng-model="name"></p> <!-- vincula o valor do campo de entrada à variável name da aplicação. -->
      <p ng-bind="name"></p> <!-- vincula o innerHTML do elemento <p> à variável name da aplicação. -->
      <p>{{name}}</p> <!-- varíavel name disponível vinculada ao campo input --> 
    </div>
    <div ng-init="person={firstName: 'Gabriel', age: 11};year=2024"></div> <!-- iniciando variáveis -->
    <p>{{person}} {{year}}</p>
    <div ng-init="names=['gabriel', 'pedro']"></div>
    <ul>
	    <li ng-repeat="x in names">
		    {{x}}
	    </li>
    </ul>
  </body>
</html>
```

Utilizando controller para controlar ambiente.

```html
<div ng-app="myApp" ng-controller="myCtrl">
	First Name: <input type="text" ng-model="firstName"><br>
	Last Name: <input type="text" ng-model="lastName"><br>
	<br>
	Full Name: {{firstName + " " + lastName}}
</div>
<script>
	var app = angular.module('myApp', []);
	app.controller('myCtrl', function($scope) {
	    $scope.firstName = "John";
	    $scope.lastName = "Doe";
	});
</script>
```