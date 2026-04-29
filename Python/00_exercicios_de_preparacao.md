# Python (10.º Ano) - 00 · Exercicios de preparação

> **Objetivo deste ficheiro**  
> Preparar os alunos para as avaliações, através de exercícios que envolvem os conceitos básicos de Python.

## Preparação para o teste de 30/04/2026

### Exercícios

**Fundamentos (variáveis, operadores, controlo de fluxo, listas e dicionários)**

1. Lê dois números inteiros com `input()`, converte para `int` e imprime a soma, a diferença, o produto, a divisão e o resto.

> Resolução:

```python
num1 = int(input("Introduz o primeiro número inteiro: "))
num2 = int(input("Introduz o segundo número inteiro: "))

print(f"Soma: {num1 + num2}")
print(f"Subtração: {num1 - num2}")
print(f"Produto: {num1 * num2}")
if num2 != 0:
    print(f"Divisão: {num1 / num2}")
    print(f"Resto: {num1 % num2}")
else:
    print("Divisão por zero não é permitida.")
```

2. Lê uma temperatura em Celsius (`float`) e converte para Fahrenheit. Usa a formula seguinte para a conversão: `F = C * 9/5 + 32`. Imprime o resultado.

> Resolução:

```python
celsius = float(input("Introduz a temperatura em Celsius: "))

fahrenheit = celsius * 9 / 5 + 32

print(f"Temperatura em Fahrenheit: {fahrenheit}")
```

3. Lê um número inteiro `N` e imprime todos os números pares entre 0 e `N` (inclusive), um por linha.

> Resolução:

```python
n = int(input("Introduz um número inteiro: "))

for numero in range(0, n + 1):
    if numero % 2 == 0:
        print(numero)
```

4. Lê 5 notas (0-20), guarda numa lista, calcula a média e indica quantas negativas existem.

> Resolução:

```python
notas = []
soma = 0
negativas = 0

for i in range(5):
    nota = float(input("Introduz uma nota: "))
    notas.append(nota)

    soma = soma + nota

    if nota < 10:
        negativas = negativas + 1

media = soma / 5

print(f"Notas: {notas}")
print(f"Média: {media}")
print(f"Número de negativas: {negativas}")
```

5. Cria um dicionário para representar um aluno com as chaves `nome`, `turma` e `notas` (lista com 3 valores). Calcula a média desse aluno.

Depois imprime tudo com o formato:

```
Aluno: [nome]
Turma: [turma]
Notas: [notas]
Média: [média]
```

> Resolução:

```python
aluno = {
    "nome": "Ana",
    "turma": "10.º A",
    "notas": [14, 16, 12]
}

soma = 0

for nota in aluno["notas"]:
    soma = soma + nota

media = soma / 3

print(f"Aluno: {aluno['nome']}")
print(f"Turma: {aluno['turma']}")
print(f"Notas: {aluno['notas']}")
print(f"Média: {media}")
```

6. Cria uma função que calcule a área de um retângulo. A função deve receber a largura e a altura como parâmetros e imprimir a área.

> Resolução:

```python
def calcular_area_retangulo(largura, altura):
    area = largura * altura
    print(f"Área do retângulo: {area}")


calcular_area_retangulo(5, 3)
```

7. Escreve uma função que receba uma lista de números e imprima cada número multiplicado por 2. Depois testa a função com uma lista de 5 números à tua escolha.

> Resolução:

```python
def mostrar_dobros(numeros):
    for numero in numeros:
        dobro = numero * 2
        print(dobro)


lista_numeros = [2, 4, 6, 8, 10]

mostrar_dobros(lista_numeros)
```

8. Cria uma função que receba uma lista de números e retorne a soma de todos os números pares na lista.

> Resolução:

```python
def somar_pares(numeros):
    soma = 0

    for numero in numeros:
        if numero % 2 == 0:
            soma = soma + numero

    return soma


lista_numeros = [1, 2, 3, 4, 5, 6]
resultado = somar_pares(lista_numeros)

print(f"Soma dos números pares: {resultado}")
```

9. Escreve uma função que receba uma string e retorne o número de vogais na string.

> Resolução:

```python
def contar_vogais(texto):
    vogais = "aeiouáéíóúàèìòùâêîôûãõ"
    contador = 0

    for letra in texto.lower():
        if letra in vogais:
            contador = contador + 1

    return contador


frase = input("Introduz uma frase: ")
resultado = contar_vogais(frase)

print(f"Número de vogais: {resultado}")
```

10. Escreve uma função que recebe dois parâmetros: uma lista de números e um número. A função deve retornar `True` se o número estiver na lista e `False` caso contrário.

> Resolução:

```python
def existe_numero(numeros, numero_procurado):
    for numero in numeros:
        if numero == numero_procurado:
            return True

    return False


lista_numeros = [3, 7, 10, 15, 20]
numero = int(input("Introduz o número a procurar: "))

resultado = existe_numero(lista_numeros, numero)

print(resultado)
```

11. Cria uma função que recebe um dicionário e o mostre de forma organizada.

> Resolução:

```python
def mostrar_dicionario(dados):
    for chave in dados:
        print(f"{chave}: {dados[chave]}")


pessoa = {
    "nome": "João",
    "idade": 16,
    "cidade": "Porto"
}

mostrar_dicionario(pessoa)
```

12. Cria uma função que receba uma lista de dicionários (cada dicionário representa uma pessoa com nome e idade) e retorne a média das idades.

> Resolução:

```python
def calcular_media_idades(pessoas):
    soma = 0

    for pessoa in pessoas:
        soma = soma + pessoa["idade"]

    media = soma / len(pessoas)

    return media


pessoas = [
    {"nome": "Ana", "idade": 15},
    {"nome": "Bruno", "idade": 16},
    {"nome": "Carla", "idade": 17}
]

resultado = calcular_media_idades(pessoas)

print(f"Média das idades: {resultado}")
```

13. Considera um dicionário com o seguinte formato:

```python
{
    1 : {
        "nome": "Ana",
        "notas": {
            "Matemática": 18,
            "Física": 16,
            "Química": 17
        },
        "faltas": {
            "Matemática": 2,
            "Física": 0,
            "Química": 1
        }
    }
}
```

Cria funções para:

- Calcular a média das notas de um aluno.
- Calcular o total de faltas de um aluno.
- Mostrar todos os alunos de forma organizada.

> Resolução:

```python
alunos = {
    1: {
        "nome": "Ana",
        "notas": {
            "Matemática": 18,
            "Física": 16,
            "Química": 17
        },
        "faltas": {
            "Matemática": 2,
            "Física": 0,
            "Química": 1
        }
    },
    2: {
        "nome": "Bruno",
        "notas": {
            "Matemática": 12,
            "Física": 14,
            "Química": 10
        },
        "faltas": {
            "Matemática": 1,
            "Física": 3,
            "Química": 0
        }
    }
}


def calcular_media_notas(aluno):
    soma = 0
    quantidade = 0

    for disciplina in aluno["notas"]:
        soma = soma + aluno["notas"][disciplina]
        quantidade = quantidade + 1

    media = soma / quantidade

    return media


def calcular_total_faltas(aluno):
    total = 0

    for disciplina in aluno["faltas"]:
        total = total + aluno["faltas"][disciplina]

    return total


def mostrar_alunos(alunos):
    for numero in alunos:
        aluno = alunos[numero]
        media = calcular_media_notas(aluno)
        total_faltas = calcular_total_faltas(aluno)

        print(f"Número: {numero}")
        print(f"Nome: {aluno['nome']}")
        print(f"Notas: {aluno['notas']}")
        print(f"Faltas: {aluno['faltas']}")
        print(f"Média: {media}")
        print(f"Total de faltas: {total_faltas}")
        print()


mostrar_alunos(alunos)
```

14. Pede ao utilizador para introduzir o nome, idade e cidade. Guarda estes dados num ficheiro JSON com o formato de um dicionário.

> Resolução:

```python
import json

dados = {
    "nome": input("Introduz o teu nome: "),
    "idade": int(input("Introduz a tua idade: ")),
    "cidade": input("Introduz a tua cidade: ")
}

with open("dados.json", "w", encoding="utf-8") as ficheiro:
    json.dump(dados, ficheiro, ensure_ascii=False, indent=4)

print("Dados guardados com sucesso.")
```

15. Lê o ficheiro JSON criado no exercício anterior e imprime os dados de forma organizada.

> Resolução:

```python
import json

with open("dados.json", "r", encoding="utf-8") as ficheiro:
    dados = json.load(ficheiro)

print(f"Nome: {dados['nome']}")
print(f"Idade: {dados['idade']}")
print(f"Cidade: {dados['cidade']}")
```

16. Cria um módulo `math_utils.py` com as funções `soma(a, b)`, `subtracao(a, b)`, `multiplicacao(a, b)` e `divisao(a, b)`.
    Usa-o no ficheiro `main.py` com `import math_utils` e números pedidos ao utilizador.

> Resolução:

`math_utils.py`

```python
def soma(a, b):
    return a + b


def subtracao(a, b):
    return a - b


def multiplicacao(a, b):
    return a * b


def divisao(a, b):
    if b != 0:
        return a / b

    return "Divisão por zero não é permitida."
```

`main.py`

```python
import math_utils

num1 = float(input("Introduz o primeiro número: "))
num2 = float(input("Introduz o segundo número: "))

print(f"Soma: {math_utils.soma(num1, num2)}")
print(f"Subtração: {math_utils.subtracao(num1, num2)}")
print(f"Multiplicação: {math_utils.multiplicacao(num1, num2)}")
print(f"Divisão: {math_utils.divisao(num1, num2)}")
```

17. Cria um módulo `texto_utils.py` com a função `contar_vogais(texto)` e usa `from texto_utils import contar_vogais` num ficheiro principal.

> Resolução:

`texto_utils.py`

```python
def contar_vogais(texto):
    vogais = "aeiouáéíóúàèìòùâêîôûãõAEIOUÁÉÍÓÚÀÈÌÒÙÂÊÎÔÛÃÕ"
    contador = 0

    for letra in texto.lower():
        if letra in vogais:
            contador = contador + 1

    return contador
```

`main.py`

```python
from texto_utils import contar_vogais

texto = input("Introduz um texto: ")
resultado = contar_vogais(texto)

print(f"Número de vogais: {resultado}")
```
