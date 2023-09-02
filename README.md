# algoritimos
Algoritimos que todo programador deveria ter conhecimento

### Busca Linear
A busca linear é um algoritmo simples que percorre uma lista de elementos um por um até encontrar o elemento desejado ou determinar que ele não existe na lista.

```python
def busca_linear(lista, alvo):
    for i, elemento in enumerate(lista):
        if elemento == alvo:
            return i  # Retorna o índice do elemento se encontrado
    return -1  # Retorna -1 se o elemento não estiver na lista

# Exemplo de uso:
lista = [1, 2, 3, 4, 5, 6, 7, 8, 9]
alvo = 6
resultado = busca_linear(lista, alvo)
if resultado != -1:
    print(f'O elemento {alvo} foi encontrado no índice {resultado}.')
else:
    print(f'O elemento {alvo} não foi encontrado na lista.')
```

### Busca Binária
A busca binária é um algoritmo eficiente que funciona em listas ordenadas, dividindo a lista pela metade a cada iteração.

```python
def busca_binaria(lista, alvo):
    esquerda, direita = 0, len(lista) - 1
    while esquerda <= direita:
        meio = (esquerda + direita) // 2
        if lista[meio] == alvo:
            return meio  # Retorna o índice do elemento se encontrado
        elif lista[meio] < alvo:
            esquerda = meio + 1
        else:
            direita = meio - 1
    return -1  # Retorna -1 se o elemento não estiver na lista

# Exemplo de uso (a lista deve estar ordenada):
lista = [1, 2, 3, 4, 5, 6, 7, 8, 9]
alvo = 6
resultado = busca_binaria(lista, alvo)
if resultado != -1:
    print(f'O elemento {alvo} foi encontrado no índice {resultado}.')
else:
    print(f'O elemento {alvo} não foi encontrado na lista.')
```

### Bubble Sort
O Bubble Sort é um algoritmo de classificação simples que compara pares de elementos adjacentes e os troca se estiverem fora de ordem.

```python
def bubble_sort(lista):
    n = len(lista)
    for i in range(n):
        for j in range(0, n - i - 1):
            if lista[j] > lista[j + 1]:
                lista[j], lista[j + 1] = lista[j + 1], lista[j]

# Exemplo de uso:
lista = [64, 34, 25, 12, 22, 11, 90]
bubble_sort(lista)
print('Lista ordenada pelo Bubble Sort:', lista)
```

### Insertion Sort
O Insertion Sort é um algoritmo de classificação que constrói a lista ordenada um item de cada vez, movendo elementos não ordenados para sua posição correta.

```python
def insertion_sort(lista):
    for i in range(1, len(lista)):
        chave = lista[i]
        j = i - 1
        while j >= 0 and chave < lista[j]:
            lista[j + 1] = lista[j]
            j -= 1
        lista[j + 1] = chave

# Exemplo de uso:
lista = [64, 34, 25, 12, 22, 11, 90]
insertion_sort(lista)
print('Lista ordenada pelo Insertion Sort:', lista)
```

### Quick Sort
O Quick Sort é um algoritmo de classificação eficiente que divide a lista em partições menores e as ordena recursivamente.

```python
def quick_sort(lista):
    if len(lista) <= 1:
        return lista
    else:
        pivo = lista[0]
        menores = [x for x in lista[1:] if x <= pivo]
        maiores = [x for x in lista[1:] if x > pivo]
        return quick_sort(menores) + [pivo] + quick_sort(maiores)

# Exemplo de uso:
lista = [64, 34, 25, 12, 22, 11, 90]
lista_ordenada = quick_sort(lista)
print('Lista ordenada pelo Quick Sort:', lista_ordenada)
```

### Merge Sort
O Merge Sort é um algoritmo de classificação que divide a lista em duas metades, ordena cada metade e depois as mescla.

```python
def merge_sort(lista):
    if len(lista) <= 1:
        return lista

    meio = len(lista) // 2
    esquerda = lista[:meio]
    direita = lista[meio:]

    esquerda = merge_sort(esquerda)
    direita = merge_sort(direita)

    return merge(esquerda, direita)

def merge(esquerda, direita):
    resultado = []
    i = j = 0

    while i < len(esquerda) and j < len(direita):
        if esquerda[i] < direita[j]:
            resultado.append(esquerda[i])
            i += 1
        else:
            resultado.append(direita[j])
            j += 1

    resultado.extend(esquerda[i:])
    resultado.extend(direita[j:])
    return resultado

# Exemplo de uso:
lista = [64, 34, 25, 12, 22, 11, 90]
lista_ordenada = merge_sort(lista)
print('Lista ordenada pelo Merge Sort:', lista_ordenada)
```

### Heap Sort
O Heap Sort é um algoritmo de classificação que utiliza uma estrutura de dados chamada heap para ordenar elementos.

```python
def heapify(lista, n, i):
    maior = i
    esquerda = 2 * i + 1
    direita = 2 * i + 2

    if esquerda < n and lista[esquerda] > lista[maior]:
        maior = esquerda

    if direita < n and lista[direita] > lista[maior]:
        maior = direita

    if maior != i:
        lista[i], lista[maior] = lista[maior], lista[i]
        heapify(lista, n, maior)

def heap_sort(lista):
    n = len(lista)

    for i in range(n // 2 - 1, -1, -1):
        heapify(lista, n, i)

    for i in range(n - 1, 0, -1):
        lista[i], lista[0] = lista[0], lista[i]
        heapify(lista, i, 0)

# Exemplo de uso:
lista = [64, 34, 25, 12, 22, 11, 90]
heap_sort(lista)
print('Lista ordenada pelo Heap Sort:', lista)
```

