# Python (10.º Ano) - 10 · Estruturas e Algoritmos Clássicos

> **Objetivo deste ficheiro**  
> Introduzir pesquisa linear, ordenação básica (bubble e selection) e uma noção simples de eficiência.

---

## 1) O que são algoritmos e porquê estudar?

Um **algoritmo** é um conjunto de passos claros para resolver um problema.  
Exemplos do dia a dia:

- receita de um bolo (passos na ordem certa);
- instrucoes para montar um movel;
- lista de regras para decidir algo.

Na programação, um algoritmo diz **como** encontrar uma resposta, não apenas **qual** é a resposta.

---

## 2) Pesquisa linear (linear search)

### 2.1 Ideia principal

A **pesquisa linear** percorre uma lista do inicio ao fim, item a item, até encontrar o valor desejado.

- se encontrar, termina;
- se não encontrar, chega ao fim.

### 2.2 Exemplo simples

```python
def pesquisa_linear(valores, alvo):
    for item in valores:
        if item == alvo:
            return True
    return False

nums = [4, 7, 1, 9, 3]
print(pesquisa_linear(nums, 9))   # True
print(pesquisa_linear(nums, 10))  # False
```

### 2.3 Exemplo com índice

```python
def pesquisa_linear_indice(valores, alvo):
    for i in range(len(valores)):
        if valores[i] == alvo:
            return i
    return -1

nomes = ["Ana", "Bruno", "Carla"]
print(pesquisa_linear_indice(nomes, "Carla"))  # 2
print(pesquisa_linear_indice(nomes, "Duarte")) # -1
```

---

## 3) Ordenação básica

Ordenar uma lista significa colocar os elementos numa **ordem** (crescente ou decrescente).

Aqui vamos ver duas ordenacoes clássicas:

- **Bubble Sort**
- **Selection Sort**

Estas ordenacoes não são as mais rápidas, mas são **simples** e boas para aprender.

---

## 4) Bubble Sort (ordenação por bolha)

### 4.1 Ideia principal

Percorremos a lista varias vezes e, em cada passagem, **trocamos** elementos adjacentes se estiverem fora de ordem.

A cada passagem, o maior elemento "sobe" para o fim.

### 4.2 Exemplo passo a passo (lista pequena)

Lista inicial: `[5, 2, 4]`

- Compara 5 e 2 -> troca: `[2, 5, 4]`
- Compara 5 e 4 -> troca: `[2, 4, 5]`

Agora o maior (5) ja esta no fim.  
Fazemos outra passagem para confirmar a ordem.

### 4.3 Implementacao

```python
def bubble_sort(valores):
    n = len(valores)
    for i in range(n):
        for j in range(0, n - 1 - i):
            if valores[j] > valores[j + 1]:
                valores[j], valores[j + 1] = valores[j + 1], valores[j]

nums = [5, 1, 4, 2, 8]
bubble_sort(nums)
print(nums)  # [1, 2, 4, 5, 8]
```

### 4.4 Versao com deteção de trocas

Se numa passagem não houver trocas, a lista ja esta ordenada e podemos parar.

```python
def bubble_sort_otimizado(valores):
    n = len(valores)
    for i in range(n):
        houve_troca = False
        for j in range(0, n - 1 - i):
            if valores[j] > valores[j + 1]:
                valores[j], valores[j + 1] = valores[j + 1], valores[j]
                houve_troca = True
        if not houve_troca:
            break
```

Explicação do código:

- Começamos por definir o tamanho da lista `n`.
- O primeiro loop `for i in range(n):` percorre a lista `n` vezes.
- Dentro deste loop, inicializamos a variável `houve_troca` como `False` para monitorizar se houve alguma troca durante a passagem.
- O segundo loop `for j in range(0, n - 1 - i):` percorre os elementos da lista até o penúltimo elemento não ordenado.
- Se o elemento atual `valores[j]` for maior que o próximo `valores[j + 1]`, trocamos os dois elementos e definimos `houve_troca` como `True`.
- Após o segundo loop, verificamos se `houve_troca` é `False`. Se for, significa que a lista já está ordenada, e podemos sair do loop principal com `break`, otimizando o processo de ordenação.

---

## 5) Selection Sort (ordenação por seleção)

### 5.1 Ideia principal

Em cada passo, encontramos o **menor** elemento da parte não ordenada e colocamo-lo na posição certa.

### 5.2 Exemplo passo a passo (lista pequena)

Lista inicial: `[4, 2, 7, 1]`

- menor = 1 -> troca com o primeiro elemento  
  lista fica `[1, 2, 7, 4]`
- agora olhamos para o resto `[2, 7, 4]`  
  menor = 2 -> ja esta na posição certa
- ultimo passo: entre `[7, 4]`, menor = 4 -> troca  
  lista final `[1, 2, 4, 7]`

### 5.3 Implementacao

```python
def selection_sort(valores):
    n = len(valores)
    for i in range(n):
        indice_min = i
        for j in range(i + 1, n):
            if valores[j] < valores[indice_min]:
                indice_min = j
        valores[i], valores[indice_min] = valores[indice_min], valores[i]

nums = [4, 2, 7, 1]
selection_sort(nums)
print(nums)  # [1, 2, 4, 7]
```

Explicação do código:

- Definimos o tamanho da lista `n`.
- O primeiro loop `for i in range(n):` percorre cada posição da lista.
- Inicializamos `indice_min` com o índice atual `i`, assumindo que o menor elemento está nessa posição.
- O segundo loop `for j in range(i + 1, n):` percorre os elementos restantes da lista para encontrar o índice do menor elemento.
- Se encontrarmos um elemento menor que o atual `valores[indice_min]`, atualizamos `indice_min` com o índice desse elemento.
- Após encontrar o menor elemento na parte não ordenada, trocamos o elemento na posição `i` com o elemento na posição `indice_min`, colocando o menor elemento na posição correta.

---

## 6) Comparar pesquisa linear e ordenação

### Pesquisa linear

- passa pela lista uma vez;
- se o alvo estiver no fim, ve todos os elementos;
- se estiver no inicio, termina logo.

### Ordenação

- faz muitas comparações e trocas;
- mesmo com listas pequenas, ja e um pouco mais pesado.

---

## 7) Noção simples de eficiência

Quando temos **poucos dados**, quase tudo funciona bem.  
Quando temos **muitos dados**, a escolha do algoritmo faz muita diferença.

### Ideia simples:

- pesquisar 1 elemento em 10 itens -> rapido
- pesquisar 1 elemento em 1 000 000 itens -> pode demorar

Se um algoritmo faz 100 000 passos e outro faz 10 000, o segundo e mais eficiente.

Nao precisamos de formulas complicadas agora, basta perceber que:

- **mais passos = mais tempo**;
- ordenar uma lista costuma ser mais pesado do que apenas procurar um valor.

---

## 8) Quando usar cada coisa

- **Pesquisa linear**: quando a lista não esta ordenada e e pequena ou media.
- **Ordenação básica**: boa para aprender e para listas pequenas.
- Para listas grandes, existem algoritmos mais rapidos (veremos mais tarde).

---

## 8.1) Porque aprender isto se existe `sort()`?

Exemplo do sort:

```python
numeros = [5, 2, 9, 1]
numeros.sort()
print(numeros)  # [1, 2, 5, 9]
```

E uma pergunta excelente e muito comum. A resposta curta e: **para perceberes o que acontece por tras do `sort()` e para ganhares ferramentas de raciocinio**. Aqui vai a explicação por partes:

### 1) `sort()` existe, mas não e magico

O `sort()` ordena porque **usa um algoritmo de ordenação por dentro**. Esse algoritmo foi criado, testado e escolhido por ser eficiente na maioria dos casos. Se não souberes o que e um algoritmo de ordenação, vais tratar o `sort()` como uma \"caixa preta\".

Saber o basico permite:

- entender porque ordenar custa tempo;
- perceber porque listas grandes demoram mais;
- distinguir quando faz sentido ordenar e quando não.

### 2) Aprender algoritmos treina o raciocinio

Bubble sort e selection sort não são ensinados por serem os melhores.  
Sao ensinados porque são **simples** e mostram ideias fundamentais:

- comparar valores;
- decidir quando trocar;
- repetir passos até estar ordenado;
- medir quantos passos foram precisos.

Esse raciocinio vai ser usado em muitos problemas diferentes, mesmo que nunca mais uses bubble sort numa aplicacao real.

### 3) Nem sempre podes usar `sort()`

Em alguns exercícios e projetos, o objetivo **é aprender** e não apenas chegar ao resultado.  
Se usares `sort()` sem perceber, estas a \"saltar\" a aprendizagem.

Tambem ha situacoes em que tens de:

- ordenar por regras especiais (por exemplo, mais novo primeiro, depois alfabetico);
- ordenar partes especificas de uma lista;
- explicar o processo passo a passo.

Sem conhecer o algoritmo, fica dificil adaptar.

### 4) O algoritmo certo faz diferença

Imagina duas formas de ordenar 10 000 números:

- uma faz cerca de 1 000 000 comparações;
- outra faz apenas 100 000.

A segunda e muito mais rapida.  
Saber que existem algoritmos diferentes ajuda-te a perceber **porque algumas solucoes são lentas**.

### 5) No futuro vais estudar algoritmos melhores

Mais tarde, vais conhecer algoritmos como **merge sort** ou **quick sort**.  
Para compreender esses algoritmos, precisas destas bases:

- comparacao e troca;
- percorrer a lista;
- dividir problemas;
- analisar eficiência.

### Em resumo

- `sort()` e excelente e vais usa-lo muitas vezes.
- Aprender algoritmos classicos serve para entender **como** o `sort()` funciona.
- Isto melhora o teu raciocinio e prepara-te para problemas mais complexos.

---

## 9) Exercicios

### Exercício 1 - Pesquisa linear simples

Cria uma função `existe(lista, alvo)` que devolve `True` se o alvo estiver na lista.

---

### Exercício 2 - Pesquisa com índice

Cria uma função `indice(lista, alvo)` que devolve o índice do alvo ou `-1` se não existir.

---

### Exercício 3 - Bubble Sort

Cria uma função `ordenar_bubble(lista)` que ordena a lista de forma crescente.

---

### Exercício 4 - Selection Sort

Cria uma função `ordenar_selection(lista)` que ordena a lista de forma crescente.

---

### Exercício 5 - Comparar métodos

Dada a lista:

```
[9, 1, 7, 3, 5]
```

1. Ordena com **bubble sort**.
2. Ordena com **selection sort**.
3. Confirma que o resultado e igual.

---

### Exercício 6 - Pesquisa antes e depois da ordenação

1. Procura o número 7 numa lista não ordenada com pesquisa linear.
2. Ordena a lista.
3. Procura de novo e compara o número de passos (podes usar um contador).

---

### Exercício 7 - Ordenação decrescente

Adapta o **bubble sort** para ordenar de forma decrescente.

---

### Exercício 8 - Ordenar nomes

Cria uma lista de nomes e ordena-a usando **selection sort**.

---

### Exercício 9 - Pesquisa por nome (ignorar maiusculas)

1. Cria uma lista com nomes.
2. Pede um nome ao utilizador.
3. Pesquisa na lista ignorando maiusculas/minusculas.

Dica: usa `nome.lower()`.

---

### Exercício 10 - Desafio simples

Cria um programa que:

- pede 5 números ao utilizador e guarda numa lista;
- ordena a lista com **bubble sort**;
- mostra a lista ordenada.

---

## 10) Changelog

- `Data a definir` · Criação inicial do ficheiro com pesquisa linear, bubble/selection sort e eficiência básica.
