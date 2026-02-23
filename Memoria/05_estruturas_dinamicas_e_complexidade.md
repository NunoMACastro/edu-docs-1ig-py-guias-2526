# Memória (10.º Ano) - 05 · Estruturas Dinâmicas e Complexidade (Big-O)

> **Objetivo deste ficheiro**  
> Introduzir estruturas dinâmicas de dados e a noção de complexidade de forma conceptual, com foco em perceber "quando usar o quê" e "porque pode ficar lento".

---

**Pré-requisitos:** [`03_gestao_de_memoria_em_python_referencias_mutabilidade_gc.md`](03_gestao_de_memoria_em_python_referencias_mutabilidade_gc.md)

## Índice

- [0. Como usar este ficheiro](#0-como-usar-este-ficheiro)
- [1. Estruturas estáticas vs dinâmicas](#1-estruturas-estáticas-vs-dinâmicas)
- [2. Pilha (Stack)](#2-pilha-stack)
- [3. Fila (Queue)](#3-fila-queue)
- [4. Lista ligada (Linked List)](#4-lista-ligada-linked-list)
- [5. Árvore binária](#5-árvore-binária)
- [6. Dicionário (Hash Table, visão base)](#6-dicionário-hash-table-visão-base)
- [7. O que é complexidade?](#7-o-que-é-complexidade)
- [8. Big-O sem medo](#8-big-o-sem-medo)
- [9. Comparação simplificada de estruturas](#9-comparação-simplificada-de-estruturas)
- [10. Erros comuns (e correções)](#10-erros-comuns-e-correções)
- [11. Resumo final](#11-resumo-final)
- [12. Changelog](#12-changelog)

---

## 0. Como usar este ficheiro

Este ficheiro é teórico.  
O objetivo não é "decorar fórmulas", mas sim:

- perceber comportamento das estruturas;
- compreender impacto de escolhas no desempenho;
- desenvolver raciocínio para futuros exercícios/projetos.

---

## 1. Estruturas estáticas vs dinâmicas

### Estruturas estáticas (ideia)

Tamanho mais rígido/fixo no modelo clássico.

### Estruturas dinâmicas (ideia)

Podem crescer ou diminuir em execução, conforme necessidade.

### Porque usar dinâmicas?

- flexibilidade;
- melhor adaptação à quantidade de dados real;
- modelação mais natural de muitos problemas.

### Nota importante em Python

A `list` de Python já é uma estrutura dinâmica (implementada como array dinâmico).

Ou seja:

- pode crescer (`append`);
- pode diminuir (`pop`);
- mantém acesso por índice muito rápido em média.

Isto explica porque a `list` é tão usada.

---

## 2. Pilha (Stack)

Regra principal: **LIFO** (Last In, First Out).

> Nota: no Módulo 04 falámos de call stack/stack frames (execução). Aqui "pilha/stack" é a estrutura de dados. Mesma ideia LIFO, contextos diferentes.

Operações típicas:

- `push` (inserir no topo);
- `pop` (remover do topo);
- `peek/top` (ver topo sem remover).

### Exemplo do dia a dia

Pilha de pratos:

- último prato colocado é o primeiro a sair.

### Onde aparece em programação?

- chamada de funções (stack frames);
- operações de desfazer (undo);
- avaliação de expressões.

### Esquema (ASCII)

```text
Base                 Topo
[10] [20] [30] [40]
                 ^ push/pop/peek
```

### Exemplo de inserção (`push`)

```python
pilha = []
pilha.append("A")
pilha.append("B")
# Estado: ["A", "B"] (topo = "B")
```

### Exemplo de pesquisa

```python
pilha = ["A", "B", "C"]  # topo = "C"
alvo = "B"
encontrado = alvo in pilha  # pesquisa linear: O(n)
```

Nota: a pilha foi pensada para trabalhar no topo; pesquisar não é a operação principal.

---

## 3. Fila (Queue)

Regra principal: **FIFO** (First In, First Out).

Operações típicas:

- `enqueue` (entra no fim);
- `dequeue` (sai do início).

### Exemplo do dia a dia

Fila de supermercado:

- quem entra primeiro é atendido primeiro.

### Onde aparece em programação?

- agendamento de tarefas;
- sistemas de atendimento;
- algoritmos de pesquisa em largura (BFS).

### Esquema (ASCII)

```text
Frente                               Trás
  |                                    |
dequeue <- [A] <- [B] <- [C] <- enqueue
```

### Exemplo de inserção (`enqueue`)

```python
from collections import deque

fila = deque()
fila.append("Ana")
fila.append("Bruno")
# Estado: deque(["Ana", "Bruno"])
```

### Exemplo de pesquisa

```python
from collections import deque

fila = deque(["Ana", "Bruno", "Carla"])
alvo = "Bruno"
encontrado = alvo in fila  # pesquisa linear: O(n)
```

Nota: tal como na pilha, pesquisar não é a operação de foco da fila.

---

## 4. Lista ligada (Linked List)

Numa lista ligada, os elementos (nós) estão ligados por referências.

Cada nó costuma ter:

- valor;
- referência para próximo nó (`next`);
- (em lista dupla) referência para anterior (`prev`).

### Vantagem conceptual

Inserções/remoções em certos pontos podem ser eficientes sem mover todos os elementos.

### Desvantagem conceptual

Acesso direto por índice não é tão natural como em arrays/listas dinâmicas comuns.

### Esquema (ASCII)

```text
head
 |
 v
[10|*] -> [25|*] -> [40|None]
```

### Exemplo de inserção (no início)

```python
class No:
    def __init__(self, valor, next=None):
        self.valor = valor
        self.next = next

head = No(25, No(40))
head = No(10, head)  # inserção no início
```

### Exemplo de pesquisa

```python
alvo = 40
atual = head
encontrado = False

while atual is not None:
    if atual.valor == alvo:
        encontrado = True
        break
    atual = atual.next
```

---

## 5. Árvore binária

Estrutura hierárquica.

Cada nó (na versão binária):

- pode ter até dois filhos;
- normalmente chamados de filho esquerdo e filho direito.

### Vocabulário útil

- raiz (root);
- nó pai;
- nó filho;
- folha (nó sem filhos);
- subárvore.

### Aplicações

- organização hierárquica de dados;
- pesquisa;
- representação de expressões.

### Esquema (ASCII)

```text
        8
      /   \
     3    10
    / \     \
   1   6    14
```

### Exemplo de inserção de lista não ordenada (BST, step-by-step)

Regra da BST:

- valores menores vão para a esquerda;
- valores maiores vão para a direita.

Lista de entrada (não ordenada): `8, 3, 10, 1, 6, 14, 7`

**Passo 1: inserir 8 (raiz)**

```text
8
```

**Passo 2: inserir 3**

- 3 < 8 -> vai para a esquerda de 8.

```text
  8
 /
3
```

**Passo 3: inserir 10**

- 10 > 8 -> vai para a direita de 8.

```text
  8
 / \
3  10
```

**Passo 4: inserir 1**

- 1 < 8 -> ir para a esquerda;
- 1 < 3 -> fica à esquerda de 3.

```text
    8
   / \
  3  10
 /
1
```

**Passo 5: inserir 6**

- 6 < 8 -> ir para a esquerda;
- 6 > 3 -> fica à direita de 3.

```text
    8
   / \
  3  10
 / \
1   6
```

**Passo 6: inserir 14**

- 14 > 8 -> ir para a direita;
- 14 > 10 -> fica à direita de 10.

```text
    8
   / \
  3  10
 / \   \
1   6  14
```

**Passo 7: inserir 7**

- 7 < 8 -> ir para a esquerda;
- 7 > 3 -> ir para a direita;
- 7 > 6 -> fica à direita de 6.

```text
      8
    /   \
   3    10
  / \     \
 1   6    14
      \
       7
```

### Exemplo de pesquisa (em BST)

Pesquisar `14`:

- comparar com `8` -> ir para a direita;
- comparar com `10` -> ir para a direita;
- encontrar `14`.

---

## 6. Dicionário (Hash Table, visão base)

Em Python, o `dict` é uma estrutura chave -> valor.

Exemplo:

```python
aluno = {"nome": "Ana", "nota": 17}
```

### Porque é poderoso?

Permite acesso muito rápido por chave em média.

### Atenção pedagógica

"Muito rápido em média" não significa "milagroso em todos os casos", mas no uso normal é excelente.

### Esquema (ASCII)

```text
chave --hash--> índice

"nome" --hash--> [bucket 5] -> "Ana"
"nota" --hash--> [bucket 2] -> 17
```

### Exemplo de inserção

```python
aluno = {}
aluno["nome"] = "Ana"
aluno["nota"] = 17
```

### Exemplo de pesquisa

```python
tem_nota = "nota" in aluno   # True
nota = aluno.get("nota")     # 17
```

---

## 7. O que é complexidade?

Complexidade mede como o custo (tempo ou memória) cresce quando aumentamos o tamanho da entrada.

Pergunta mental:

"Se eu duplicar o tamanho dos dados, o trabalho cresce quanto?"

---

## 8. Big-O sem medo

Big-O descreve tendência de crescimento, não tempo exato em segundos.

### Formas comuns

- `O(1)` constante;
- `O(log n)` logarítmica;
- `O(n)` linear;
- `O(n log n)` quase linear;
- `O(n^2)` quadrática.

### Leitura intuitiva

- `O(1)`: custo praticamente fixo;
- `O(n)`: custo cresce proporcionalmente aos dados;
- `O(n^2)`: cresce muito rapidamente com dados grandes.

### Exemplo mental rápido

Se um algoritmo passa de 1 000 para 10 000 elementos:

- `O(n)` cresce cerca de 10x;
- `O(n^2)` cresce cerca de 100x.

É por isso que escolhas de estrutura importam muito em escalas maiores.

---

## 9. Comparação simplificada de estruturas

| Estrutura              | Ponto forte                                | Limitação típica                                |
| ---------------------- | ------------------------------------------ | ----------------------------------------------- |
| Lista (array dinâmico) | acesso por índice rápido                   | inserir/remover no meio pode ser caro           |
| Pilha                  | inserir/remover no topo é simples e rápido | acesso restrito ao topo                         |
| Fila                   | ordem FIFO natural                         | acesso aleatório não é foco                     |
| Lista ligada           | flexível em inserções/remoções             | pesquisa/acesso por posição pode ser mais lento |
| Árvore binária         | boa organização hierárquica                | pode degradar se ficar desequilibrada           |
| Dicionário             | acesso por chave rápido em média           | não substitui todas as estruturas               |

---

## 10. Erros comuns (e correções)

### Erro 1

"A estrutura mais rápida é sempre a melhor."

**Correção:** depende da operação principal (pesquisar? inserir? remover? manter ordem?).

### Erro 2

"Big-O dá o tempo exato."

**Correção:** Big-O dá tendência de crescimento, não segundos exatos.

### Erro 3

"Dicionário resolve qualquer problema."

**Correção:** excelente para chave-valor, mas não substitui pilhas, filas, árvores, etc.

---

## 11. Resumo final

- Estruturas dinâmicas adaptam-se ao crescimento dos dados.
- Pilha usa LIFO; fila usa FIFO.
- Lista ligada usa nós e referências.
- Árvores modelam hierarquia.
- Dicionários são muito úteis para acesso por chave.
- Big-O ajuda a antecipar desempenho quando os dados crescem.

---

**A seguir:** [Rota de estudo recomendada](README.md#rota-de-estudo-recomendada)

---

## 12. Changelog

- **2026-02-23**: adicionados esquemas (ASCII), exemplos de inserção/pesquisa e um passo a passo de inserção de lista não ordenada em BST.
- **2026-02-04**: versão inicial do módulo 05.
