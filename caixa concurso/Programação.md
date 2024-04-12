# Java
#TODO https://www.devmedia.com.br/entendendo-anotacoes-em-java/26772
#TODO https://www.youtube.com/watch?v=7udU24-VK0w
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
- Blocos de instância/anônimo 
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
``` 