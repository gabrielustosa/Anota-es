# Lista encadeada

São estruturas de dados dinâmicas que contém um valor que apontam para o próximo valor presenta na lista permitindo a inserção e remoção de elementos em qualquer posição, incluindo início, meio e fim. Elas também permitem o acesso aos elementos em posições intermediárias.
# Busca Binária

Conquistar e dividir.

- Precisa de um vetor previamente ordenado.
- mid = (low + high) / 2; low = indicie 0; high = ultimo indicie;
- Sua complexidade é, onde n representa o número de elementos na array.
	- Melhor caso: 1, Médio caso: O(2 log n), Pior caso: O(n²)

```python
def binary_search(arr, target): 
	left = 0 
	right = len(arr) - 1 
	while left <= right: 
		mid = (left + right) // 2 
		if arr[mid] == target: 
			return mid 
		elif arr[mid] < target: 
			left = mid + 1 
		else: 
			right = mid - 1
	return -1

  
a = [1, 2, 3, 4, 5, 6]  
binary_search(a, 5) # passou pelos números 3, 5

a = [5, 18, 27, 33, 44, 49, 54, 67, 69, 72, 79, 86, 87, 92]  
binary_search(78) # passou pelos números 54, 79, 69, 72
```
# Ordenação por bolha

Comparações de elementos que estão em posições consecutivas até estarem ordenadas iterando até o **FINAL** da array.

- Sua complexidade é, onde n representa o número de elementos na array.
	- Melhor caso: O(n), Médio caso: O(n²), Pior caso: O(n²)

```python
def bubble_sort(alist):  
	for passnum in range(len(alist) - 1, 0, -1):  
		for i in range(passnum):  
			if alist[i] > alist[i + 1]:  
				temp = alist[i]  
				alist[i] = alist[i + 1]  
				alist[i + 1] = temp  
  
alist = [54, 26, 93, 17, 77, 31, 44, 55, 20]  
bubble_sort(alist) # [17, 20, 26, 31, 44, 54, 55, 77, 93]
```
# Ordenação por seleção

Percorre toda a lista até encontrar o menor elemento do vetor (ou maior) e **TROCA** para a posição do passo da estrutura de repetição.

- Sua complexidade é, onde n representa o número de elementos na array.
	- Melhor caso: O(n²), Médio caso: O(n²), Pior caso: O(n²)

```python 
def selection_sort(array):  
	size = len(array)  
	  
	for step in range(size):  
		min_idx = step  
		  
		for i in range(step + 1, size):  
			if array[i] < array[min_idx]:  
				min_idx = i  
		(array[step], array[min_idx]) = (array[min_idx], array[step])  
  
alist = [54, 26, 93, 17, 77, 31, 44, 55, 20]  
selection_sort(alist) # [17, 20, 26, 31, 44, 54, 55, 77, 93]
```
# Ordenação por inserção

Método que percorre um vetor de elementos da esquerda para a direita e à medida que avança vai **ORDENANDO** os elementos à esquerda

- Sua complexidade é, onde n representa o número de elementos na array.
	- Melhor caso: O(n), Médio caso: O(n²), Pior caso: O(n²)
# Ordenação Merge

Utiliza o principio dividir para conquistar.

1. Dividir em várias sub listas até sobrar um elemento 
2. De forma recursiva vai juntando as sub listas comparando os elementos que estão dentro e montando uma nova lista até se tornarem uma só lista.

- Sua complexidade é, onde n representa o número de elementos na array.
	- Melhor caso: O(n log n), Médio caso: O(n log n), Pior caso: O(n log n)
# Ordenação Quick

- Sua complexidade é, onde n representa o número de elementos na array.
	- Melhor caso: O(n log n), Médio caso: O(n log n), Pior caso: O(n²)
# Árvore Binária

Leitura em linha sempre começa pela direita

- Pré ordem: bolinha a esquerda
- Em ordem: bolinha em baixo
- Pós ordem: bolinha a direita