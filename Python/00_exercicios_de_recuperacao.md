# Python (10.º Ano) - 00 · Exercicios de recuperação

> **Objetivo deste ficheiro**  
> Preparar os alunos para a recuperação, através de exercícios que envolvem os conceitos básicos de Python.

Usa um IDE para escrever os teus programas.

Podes usar o [OnlineGDB](https://www.onlinegdb.com/online_python_compiler) inicialmente uma vez que é muito simples de usar.

# Exercícios Básicos

Exercícios sobre variáveis, tipos de dados, operações aritméticas e entrada e saída de dados.

## Exercício 1

Cria um programa que:

1. Guarda em variáveis o teu `nome`, `idade` e `curso` (em texto).
2. Mostra uma mensagem do tipo:

    ```
    Olá, eu sou a/o <nome>, tenho <idade> anos e estou no curso <curso>.
    ```

> Resolução:

```python
nome = "João"
idade = 16
curso = "10.º Ano"
print(f"Olá, eu sou {nome}, tenho {idade} anos e estou no curso {curso}.")
```

## Exercício 2

Cria um programa que:

1.  Guarda em variáveis o `preço` de um produto e a `quantidade` que queres comprar (em números).
2.  Calcula o `total` a pagar, multiplicando o preço pela quantidade.
3.  Mostra uma mensagem do tipo:

        ```
        O total a pagar é: <total>.
        ```

    > Resolução:

```python
preço = 9.99
quantidade = 3
total = preço * quantidade
print(f"O total a pagar é: {total}.")
```

## Exercício 3

Cria um programa que:

1. Pede ao utilizador para introduzir dois números (usa a função `input()` e converte os valores para números usando `int()` ou `float()`).
2. Calcula a `soma`, a `subtração`, a `multiplicação` e a `divisão` desses dois números.
3. Mostra os resultados de cada operação em mensagens do tipo:

    ```
    A soma é: <soma>.
    A subtração é: <subtração>.
    A multiplicação é: <multiplicação>.
    A divisão é: <divisão>.
    ```

> Resolução:

```python
num1 = float(input("Introduz o primeiro número: "))
num2 = float(input("Introduz o segundo número: "))

soma = num1 + num2
subtração = num1 - num2
multiplicação = num1 * num2
divisão = num1 / num2

print(f"A soma é: {soma}.")
print(f"A subtração é: {subtração}.")
print(f"A multiplicação é: {multiplicação}.")
print(f"A divisão é: {divisão}.")
```

## Exercício 4

Cria um programa que:

1. Peça ao utilizador para introduzir a altura e largura de um retângulo (em números).
2. Calcula a área do retângulo (altura x largura)
3. Mostra uma mensagem do tipo:

    ```
    A área do retângulo é: <área>.
    ```

> Resolução:

```python
altura = float(input("Introduz a altura do retângulo: "))
largura = float(input("Introduz a largura do retângulo: "))
área = altura * largura
print(f"A área do retângulo é: {área}.")
```

## Exercício 5

Cria um programa que:

1. Peça ao utilizador para introduzir a temperatura em graus Celsius (em número).
2. Converte a temperatura para Fahrenheit usando a fórmula: `F = (C * 9/5) + 32`
3. Mostra uma mensagem do tipo:

    ```
    A temperatura em Celsius é: <C>°C.
    A temperatura em Fahrenheit é: <F>°F.
    ```

> Resolução:

```python

C = float(input("Introduz a temperatura em graus Celsius: "))
F = (C * 9/5) + 32
print(f"A temperatura em Celsius é: {C}°C.")
print(f"A temperatura em Fahrenheit é: {F}°F.")
```

## Exercício 6

Cria um programa que:

1. Peça ao utilizador para introduzir a sua morada (em texto).
2. Mostra uma mensagem do tipo:

    ```
    A tua morada é: <morada>.
    ```

## Exercício 7

Cria um programa que:

1. Peça ao utilizador para introduzir o seu nome e idade (em texto e número).
2. Mostra uma mensagem do tipo:

    ```
    Olá, <nome>! Tens <idade> anos.
    ```

## Exercício 8

Cria um programa que:

1. Peça ao utilizador para introduzir o raio de um círculo (em número).
2. Calcula a área do círculo usando a fórmula: `A = π * r^2` (assume que o π = 3.14).
3. Mostra uma mensagem do tipo:

    ```
    A área do círculo é: <área>.
    ```

## Exercício 9

Cria um programa que:

1. Peça ao utilizador para introduzir a sua data de nascimento (em texto, formato: DD/MM/AAAA).
2. Mostra uma mensagem do tipo:

    ```
    A tua data de nascimento é: <data>.
    ```

# Exercícios Intermédios

Exercícios que envolvem estruturas de repetição, de controlo, funções, listas e dicionários.

## Exercício 10

Cria um programa que:

1. Peça ao utilizador para introduzir um número.
2. Verifica se o número é positivo, negativo ou zero e mostra uma mensagem do tipo:

    ```
    O número <n> é positivo.
    ```

    ou

    ```
    O número <n> é negativo.
    ```

    ou

    ```
    O número <n> é zero.
    ```

## Exercício 11

Cria um programa que:

1. Peça ao utilizador para introduzir um número inteiro.
2. Verifica se o número é par ou ímpar e mostra uma mensagem do tipo:

    ```
    O número <n> é par.
    ```

    ou

    ```
    O número <n> é ímpar.
    ```

> Nota: um número é par se o resto da divisão por 2 for igual a 0, ou seja, `n % 2 == 0`. Neste caso `if n % 2 == 0:` é a condição para verificar se o número é par.

## Exercício 12

Cria um programa que:

1. Peça um nome ao utilizador e diga se o nome tem mais de 5 letras ou não, mostrando uma mensagem do tipo:

    ```
    O nome <nome> tem mais de 5 letras.
    ```

    ou

    ```
    O nome <nome> tem 5 ou menos letras.
    ```

> Nota: para verificar o número de letras de um nome, podes usar a função `len(nome)`, que retorna o comprimento da string.

## Exercício 13

Cria um programa que:

1. Peça ao utilizador para introduzir dois números inteiros.
2. Diga se algum dos números é maior do que o outro, ou se são iguais, mostrando uma mensagem do tipo:

    ```
    O número <n1> é maior do que <n2>.
    ```

    ou

    ```
    O número <n2> é maior do que <n1>.
    ```

    ou

    ```
    Os números <n1> e <n2> são iguais.
    ```
