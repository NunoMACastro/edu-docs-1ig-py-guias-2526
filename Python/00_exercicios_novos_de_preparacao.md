![Header](../Images/Header.png)

# Python (10.º Ano) - 00 · Exercícios de preparação para novo teste

> **Objetivo deste ficheiro**
> Preparar os alunos para um novo teste de Python, com foco principal em funções, listas, dicionários, ficheiros JSON e estruturas de seleção e repetição.

### Exercícios básicos e diretos com funções

#### Exercício 1 - Saudação personalizada

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md)

Cria uma função chamada `criar_saudacao(nome)` que recebe um nome e devolve uma frase no formato:

```text
Olá, <nome>!
```

No programa principal, pede o nome ao utilizador, chama a função e mostra a frase devolvida.

> Resolução:

```python
def criar_saudacao(nome):
    return f"Olá, {nome}!"

# Programa principal
nome_utilizador = input("Introduza o seu nome: ")
saudacao = criar_saudacao(nome_utilizador)
print(saudacao)
```

#### Exercício 2 - Dobro de um número

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md)

Cria uma função chamada `calcular_dobro(numero)` que recebe um número e devolve o seu dobro.

No programa principal, pede um número ao utilizador, chama a função e mostra o resultado.

> Resolução:

```python
def calcular_dobro(numero):
    return numero * 2

# Programa principal
numero_utilizador = float(input("Introduza um número: "))
dobro = calcular_dobro(numero_utilizador)
print(f"O dobro de {numero_utilizador} é {dobro}.")
```

#### Exercício 3 - Área de um retângulo

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md)

Cria uma função chamada `calcular_area_retangulo(largura, altura)` que recebe a largura e a altura de um retângulo e devolve a área.

No programa principal, pede os dois valores ao utilizador e mostra a área calculada.

> Resolução:

```python
def calcular_area_retangulo(largura, altura):
    return largura * altura

# Programa principal
largura = float(input("Introduza a largura do retângulo: "))
altura = float(input("Introduza a altura do retângulo: "))
area = calcular_area_retangulo(largura, altura)
print(f"A área do retângulo é {area}.")
```

#### Exercício 4 - Conversão de temperatura

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md)

Cria uma função chamada `converter_celsius_para_fahrenheit(celsius)` que recebe uma temperatura em graus Celsius e devolve a temperatura em Fahrenheit.

Usa a fórmula:

```text
F = C * 9 / 5 + 32
```

> Resolução:

```python
def converter_celsius_para_fahrenheit(celsius):
    return celsius * 9 / 5 + 32

# Programa principal
celsius = float(input("Introduza a temperatura em Celsius: "))
fahrenheit = converter_celsius_para_fahrenheit(celsius)
print(f"{celsius}°C é equivalente a {fahrenheit}°F.")
```

#### Exercício 5 - Número par

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `e_par(numero)` que recebe um número inteiro e devolve:

- `True`, se o número for par;
- `False`, se o número for ímpar.

No programa principal, pede um número ao utilizador e mostra uma mensagem adequada.

> Resolução:

```python
def e_par(numero):
    return numero % 2 == 0

# Programa principal
numero_utilizador = int(input("Introduza um número inteiro: "))
if e_par(numero_utilizador):
    print(f"{numero_utilizador} é par.")
else:
    print(f"{numero_utilizador} é ímpar.")
```

#### Exercício 6 - Maior de dois números

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `maior_de_dois(a, b)` que recebe dois números e devolve o maior.

Se os números forem iguais, a função deve devolver a mensagem:

```text
Os números são iguais.
```

> Resolução:

```python
def maior_de_dois(a, b):
    if a > b:
        return a
    elif b > a:
        return b
    else:
        return "Os números são iguais."

# Programa principal
num1 = float(input("Introduza o primeiro número: "))
num2 = float(input("Introduza o segundo número: "))
resultado = maior_de_dois(num1, num2)
print(f"O maior número é: {resultado}")
```

#### Exercício 7 - Classificação de uma nota

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `classificar_nota(nota)` que recebe uma nota entre 0 e 20 e devolve uma classificação textual:

- menor que 10: `Negativa`;
- de 10 a 13: `Suficiente`;
- de 14 a 17: `Boa`;
- de 18 a 20: `Muito boa`;
- fora do intervalo 0-20: `Nota inválida`.

> resolução:

```python
def classificar_nota(nota):
    if nota < 0 or nota > 20:
        return "Nota inválida."
    elif nota < 10:
        return "Negativa"
    elif nota <= 13:
        return "Suficiente"
    elif nota <= 17:
        return "Boa"
    else:
        return "Muito boa"

# Programa principal
nota_utilizador = float(input("Introduza a nota (0-20): "))
classificacao = classificar_nota(nota_utilizador)
print(f"A classificação da nota {nota_utilizador} é: {classificacao}")
```

#### Exercício 8 - Contar de 1 até N

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `mostrar_contagem(n)` que recebe um número inteiro positivo e mostra todos os números de 1 até `n`.

No programa principal, pede o valor de `n` ao utilizador.

> Resolução:

```python
def mostrar_contagem(n):
    for i in range(1, n + 1):
        print(i)

# Programa principal
n_utilizador = int(input("Introduza um número inteiro positivo: "))
if n_utilizador > 0:
    mostrar_contagem(n_utilizador)
else:
    print("Número inválido. Introduza um número inteiro positivo.")
```

#### Exercício 9 - Somatório até N

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `calcular_somatorio(n)` que recebe um número inteiro positivo e devolve a soma de todos os números de 1 até `n`.

Exemplo do cálculo pretendido para `n = 5`:

```text
1 + 2 + 3 + 4 + 5
```

> Resolução:

```python
def calcular_somatorio(n):
    return sum(range(1, n + 1))

# Programa principal
n_utilizador = int(input("Introduza um número inteiro positivo: "))
if n_utilizador > 0:
    somatorio = calcular_somatorio(n_utilizador)
    print(f"O somatório de 1 até {n_utilizador} é: {somatorio}")
else:
    print("Número inválido. Introduza um número inteiro positivo.")
```

#### Exercício 10 - Tabuada

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `mostrar_tabuada(numero)` que recebe um número e mostra a tabuada desse número de 1 até 10.

No programa principal, pede o número ao utilizador e chama a função.

> Resolução:

```python
def mostrar_tabuada(numero):
    for i in range(1, 11):
        print(f"{numero} x {i} = {numero * i}")

# Programa principal
numero_utilizador = int(input("Introduza um número para ver a tabuada: "))
mostrar_tabuada(numero_utilizador)
```

#### Exercício 11 - Contar vogais

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `contar_vogais(texto)` que recebe uma frase e devolve o número de vogais existentes nessa frase.

Deves considerar, pelo menos, as vogais:

```text
a e i o u
```

> Resolução:

```python
def contar_vogais(texto):
    vogais = "aeiouAEIOUáéíóúÁÉÍÓÚàèìòùÀÈÌÒÙâêîôûÂÊÎÔÛãõÃÕ"
    return sum(1 for char in texto if char in vogais)

# Programa principal
frase_utilizador = input("Introduza uma frase: ")
numero_vogais = contar_vogais(frase_utilizador)
print(f"A frase contém {numero_vogais} vogais.")
```

#### Exercício 12 - Preço final com desconto

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `calcular_preco_final(preco, desconto)` que recebe:

- o preço inicial de um produto;
- a percentagem de desconto.

A função deve devolver o preço final.

Se o desconto for menor que 0 ou maior que 100, a função deve devolver a mensagem:

```text
Desconto inválido.
```

> Resolução:

```python
def calcular_preco_final(preco, desconto):
    if desconto < 0 or desconto > 100:
        return "Desconto inválido."
    return preco * (1 - desconto / 100)

# Programa principal
preco_inicial = float(input("Introduza o preço inicial do produto: "))
percentagem_desconto = float(input("Introduza a percentagem de desconto: "))
preco_final = calcular_preco_final(preco_inicial, percentagem_desconto)
if isinstance(preco_final, str):
    print(preco_final)
else:
    print(f"O preço final do produto é: {preco_final:.2f}")
```

#### Exercício 13 - Palavra repetida

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `repetir_palavra(palavra, vezes)` que recebe uma palavra e um número inteiro.

A função deve mostrar a palavra o número de vezes indicado.

Se o número de vezes for menor ou igual a 0, deve mostrar:

```text
Número inválido.
```

> Resolução:

```python
def repetir_palavra(palavra, vezes):
    if vezes <= 0:
        print("Número inválido.")
    else:
        for _ in range(vezes):
            print(palavra)

# Programa principal
palavra_utilizador = input("Introduza uma palavra: ")
vezes_utilizador = int(input("Quantas vezes deseja repetir a palavra? "))
repetir_palavra(palavra_utilizador, vezes_utilizador)
```

#### Exercício 14 - Validar idade

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `validar_idade(idade)` que recebe uma idade e devolve:

- `Criança`, se a idade for menor que 13;
- `Adolescente`, se estiver entre 13 e 17;
- `Adulto`, se for 18 ou mais;
- `Idade inválida`, se for negativa.

> Resolução:

```python
def validar_idade(idade):
    if idade < 0:
        return "Idade inválida"
    elif idade < 13:
        return "Criança"
    elif idade <= 17:
        return "Adolescente"
    else:
        return "Adulto"

# Programa principal
idade_utilizador = int(input("Introduza a idade: "))
resultado = validar_idade(idade_utilizador)
print(resultado)
```

### Funções com listas e dicionários

#### Exercício 15 - Soma dos números pares

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `somar_pares(numeros)` que recebe uma lista de números inteiros e devolve a soma apenas dos números pares.

Testa a função com uma lista criada por ti.

> Resolução:

```python
def somar_pares(numeros):
    soma = 0

    for numero in numeros:
        if numero % 2 == 0:
            soma = soma + numero

    return soma

# Programa principal
lista_numeros = [3, 8, 12, 5, 7, 10]
resultado = somar_pares(lista_numeros)
print(f"A soma dos números pares é: {resultado}")
```

#### Exercício 16 - Contar negativas

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `contar_negativas(notas)` que recebe uma lista de notas e devolve quantas notas são negativas.

Considera negativa qualquer nota menor que 10.

> Resolução:

```python
def contar_negativas(notas):
    contador = 0

    for nota in notas:
        if nota < 10:
            contador = contador + 1

    return contador

# Programa principal
notas_alunos = [8, 12, 9.5, 15, 6, 18]
total_negativas = contar_negativas(notas_alunos)
print(f"Existem {total_negativas} notas negativas.")
```

#### Exercício 17 - Média de uma lista

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `calcular_media(numeros)` que recebe uma lista de números e devolve a média.

Se a lista estiver vazia, a função deve devolver:

```text
Lista vazia.
```

> Resolução:

```python
def calcular_media(numeros):
    if len(numeros) == 0:
        return "Lista vazia."

    soma = 0

    for numero in numeros:
        soma = soma + numero

    media = soma / len(numeros)
    return media

# Programa principal
lista_numeros = [10, 14, 16, 12]
resultado = calcular_media(lista_numeros)
print(f"Resultado: {resultado}")
```

#### Exercício 18 - Separar pares e ímpares

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `separar_pares_impares(numeros)` que recebe uma lista de números inteiros e devolve um dicionário com este formato:

```python
{
    "pares": [...],
    "impares": [...]
}
```

O dicionário não deve ter mais de 2 níveis.

> Resolução:

```python
def separar_pares_impares(numeros):
    resultado = {
        "pares": [],
        "impares": []
    }

    for numero in numeros:
        if numero % 2 == 0:
            resultado["pares"].append(numero)
        else:
            resultado["impares"].append(numero)

    return resultado

# Programa principal
lista_numeros = [1, 2, 3, 4, 5, 6, 7, 8]
resultado = separar_pares_impares(lista_numeros)
print(resultado)
```

#### Exercício 19 - Procurar nome numa lista

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `procurar_nome(nomes, nome_procurado)` que recebe:

- uma lista de nomes;
- um nome a procurar.

A função deve devolver `True` se o nome existir na lista e `False` caso contrário.

> Resolução:

```python
def procurar_nome(nomes, nome_procurado):
    for nome in nomes:
        if nome == nome_procurado:
            return True

    return False

# Programa principal
lista_nomes = ["Ana", "Bruno", "Carla", "Diogo"]
nome = input("Introduza o nome a procurar: ")

if procurar_nome(lista_nomes, nome):
    print("O nome existe na lista.")
else:
    print("O nome não existe na lista.")
```

#### Exercício 20 - Criar dicionário de aluno

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md)

Cria uma função chamada `criar_aluno(nome, idade, turma)` que recebe os dados de um aluno e devolve um dicionário com este formato:

```python
{
    "nome": "...",
    "idade": 0,
    "turma": "..."
}
```

No programa principal, pede os dados ao utilizador e mostra o dicionário criado.

> Resolução:

```python
def criar_aluno(nome, idade, turma):
    aluno = {
        "nome": nome,
        "idade": idade,
        "turma": turma
    }

    return aluno

# Programa principal
nome_aluno = input("Introduza o nome do aluno: ")
idade_aluno = int(input("Introduza a idade do aluno: "))
turma_aluno = input("Introduza a turma do aluno: ")

aluno_criado = criar_aluno(nome_aluno, idade_aluno, turma_aluno)
print(aluno_criado)
```

#### Exercício 21 - Verificar se um aluno está aprovado

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `aluno_aprovado(aluno)` que recebe um dicionário com este formato:

```python
{
    "nome": "Ana",
    "media": 14
}
```

A função deve devolver `True` se a média for maior ou igual a 10 e `False` caso contrário.

> Resolução:

```python
def aluno_aprovado(aluno):
    return aluno["media"] >= 10

# Programa principal
aluno = {
    "nome": "Ana",
    "media": 14
}

if aluno_aprovado(aluno):
    print(f"{aluno['nome']} está aprovado.")
else:
    print(f"{aluno['nome']} não está aprovado.")
```

#### Exercício 22 - Contar alunos por turma

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `contar_alunos_por_turma(alunos)` que recebe uma lista de dicionários com este formato:

```python
[
    {"nome": "Ana", "turma": "10A"},
    {"nome": "Bruno", "turma": "10B"},
    {"nome": "Carla", "turma": "10A"}
]
```

A função deve devolver um dicionário com o número de alunos por turma.

> Resolução:

```python
def contar_alunos_por_turma(alunos):
    contagem = {}

    for aluno in alunos:
        turma = aluno["turma"]

        if turma in contagem:
            contagem[turma] = contagem[turma] + 1
        else:
            contagem[turma] = 1

    return contagem

# Programa principal
alunos = [
    {"nome": "Ana", "turma": "10A"},
    {"nome": "Bruno", "turma": "10B"},
    {"nome": "Carla", "turma": "10A"},
    {"nome": "Diogo", "turma": "10C"},
    {"nome": "Eva", "turma": "10B"}
]

resultado = contar_alunos_por_turma(alunos)
print(resultado)
```

#### Exercício 23 - Média por turma

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `calcular_media_por_turma(turmas)` que recebe um dicionário de listas com este formato:

```python
{
    "10A": [12, 15, 18],
    "10B": [9, 11, 14]
}
```

A função deve devolver um dicionário com a média de cada turma.

> Resolução:

```python
def calcular_media_por_turma(turmas):
    medias = {}

    for turma in turmas:
        soma = 0

        for nota in turmas[turma]:
            soma = soma + nota

        media = soma / len(turmas[turma])
        medias[turma] = media

    return medias

# Programa principal
turmas = {
    "10A": [12, 15, 18],
    "10B": [9, 11, 14]
}

resultado = calcular_media_por_turma(turmas)
print(resultado)
```

#### Exercício 24 - Filtrar produtos baratos

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `filtrar_produtos_baratos(produtos, limite)` que recebe:

- uma lista de dicionários com produtos;
- um preço limite.

Cada produto deve ter este formato:

```python
{
    "nome": "Caderno",
    "preco": 2.5
}
```

A função deve devolver uma lista apenas com os produtos cujo preço seja menor ou igual ao limite.

> Resolução:

```python
def filtrar_produtos_baratos(produtos, limite):
    produtos_baratos = []

    for produto in produtos:
        if produto["preco"] <= limite:
            produtos_baratos.append(produto)

    return produtos_baratos

# Programa principal
produtos = [
    {"nome": "Caderno", "preco": 2.5},
    {"nome": "Mochila", "preco": 24.99},
    {"nome": "Caneta", "preco": 1.2},
    {"nome": "Calculadora", "preco": 18.5}
]

limite_preco = float(input("Introduza o preço limite: "))
resultado = filtrar_produtos_baratos(produtos, limite_preco)
print(resultado)
```

### Funções com ficheiros JSON

#### Exercício 25 - Guardar aluno em JSON

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Ficheiros JSON](./07_ficheiros_texto_json_csv.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md)

Cria uma função chamada `guardar_aluno_json(aluno, caminho)` que recebe:

- um dicionário com os dados de um aluno;
- o caminho do ficheiro JSON.

A função deve guardar o dicionário no ficheiro indicado.

> Resolução:

```python
import json

def guardar_aluno_json(aluno, caminho):
    with open(caminho, "w", encoding="utf-8") as ficheiro:
        json.dump(aluno, ficheiro, ensure_ascii=False, indent=4)

# Programa principal
aluno = {
    "nome": "Ana",
    "idade": 16,
    "turma": "10A"
}

guardar_aluno_json(aluno, "aluno.json")
print("Aluno guardado com sucesso.")
```

#### Exercício 26 - Ler aluno de JSON

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Ficheiros JSON](./07_ficheiros_texto_json_csv.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md)

Cria uma função chamada `ler_aluno_json(caminho)` que recebe o caminho de um ficheiro JSON e devolve o dicionário lido desse ficheiro.

No programa principal, mostra os dados do aluno de forma organizada.

> Resolução:

```python
import json

def ler_aluno_json(caminho):
    with open(caminho, "r", encoding="utf-8") as ficheiro:
        aluno = json.load(ficheiro)

    return aluno

# Programa principal
aluno = ler_aluno_json("aluno.json")

print(f"Nome: {aluno['nome']}")
print(f"Idade: {aluno['idade']}")
print(f"Turma: {aluno['turma']}")
```

#### Exercício 27 - Guardar lista de contactos

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Ficheiros JSON](./07_ficheiros_texto_json_csv.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md)

Cria uma função chamada `guardar_contactos(contactos, caminho)` que recebe uma lista de contactos e guarda essa lista num ficheiro JSON.

Cada contacto deve ter este formato:

```python
{
    "nome": "Ana",
    "telefone": "912345678"
}
```

> Resolução:

```python
import json

def guardar_contactos(contactos, caminho):
    with open(caminho, "w", encoding="utf-8") as ficheiro:
        json.dump(contactos, ficheiro, ensure_ascii=False, indent=4)

# Programa principal
contactos = [
    {"nome": "Ana", "telefone": "912345678"},
    {"nome": "Bruno", "telefone": "923456789"},
    {"nome": "Carla", "telefone": "934567890"}
]

guardar_contactos(contactos, "contactos.json")
print("Contactos guardados com sucesso.")
```

#### Exercício 28 - Ler lista de contactos

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Ficheiros JSON](./07_ficheiros_texto_json_csv.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `ler_contactos(caminho)` que lê uma lista de contactos a partir de um ficheiro JSON.

Depois, cria outra função chamada `mostrar_contactos(contactos)` que recebe a lista e mostra todos os contactos de forma organizada.

> Resolução:

```python
import json

def ler_contactos(caminho):
    with open(caminho, "r", encoding="utf-8") as ficheiro:
        contactos = json.load(ficheiro)

    return contactos

def mostrar_contactos(contactos):
    for contacto in contactos:
        print(f"Nome: {contacto['nome']}")
        print(f"Telefone: {contacto['telefone']}")
        print()

# Programa principal
contactos = ler_contactos("contactos.json")
mostrar_contactos(contactos)
```

### Exercícios de dificuldade média e alta

#### Exercício 29 - Pesquisa de contacto

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Ficheiros JSON](./07_ficheiros_texto_json_csv.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria um pequeno programa para pesquisar contactos.

O programa deve ter, pelo menos, estas funções:

- `ler_contactos(caminho)`;
- `procurar_contacto(contactos, nome)`;
- `mostrar_resultado(contacto)`.

Os contactos devem estar guardados num ficheiro JSON como uma lista de dicionários.

Se o contacto existir, mostra o nome e o telefone. Se não existir, mostra uma mensagem adequada.

> Resolução:

```python
import json

def ler_contactos(caminho):
    with open(caminho, "r", encoding="utf-8") as ficheiro:
        contactos = json.load(ficheiro)

    return contactos

def procurar_contacto(contactos, nome):
    for contacto in contactos:
        if contacto["nome"].lower() == nome.lower():
            return contacto

    return None

def mostrar_resultado(contacto):
    if contacto is None:
        print("Contacto não encontrado.")
    else:
        print(f"Nome: {contacto['nome']}")
        print(f"Telefone: {contacto['telefone']}")

# Programa principal
contactos = ler_contactos("contactos.json")
nome_procurado = input("Introduza o nome do contacto a procurar: ")
contacto_encontrado = procurar_contacto(contactos, nome_procurado)
mostrar_resultado(contacto_encontrado)
```

#### Exercício 30 - Atualizar stock de produtos

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Ficheiros JSON](./07_ficheiros_texto_json_csv.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria um programa que gere uma lista de produtos guardada em JSON.

Cada produto deve ter este formato:

```python
{
    "codigo": "P001",
    "nome": "Caneta",
    "stock": 20
}
```

O programa deve ter, pelo menos, estas funções:

- `ler_produtos(caminho)`;
- `guardar_produtos(produtos, caminho)`;
- `procurar_produto(produtos, codigo)`;
- `atualizar_stock(produtos, codigo, nova_quantidade)`.

Se o código existir, atualiza o stock. Se não existir, mostra uma mensagem adequada.

> Resolução:

```python
import json

def ler_produtos(caminho):
    with open(caminho, "r", encoding="utf-8") as ficheiro:
        produtos = json.load(ficheiro)

    return produtos

def guardar_produtos(produtos, caminho):
    with open(caminho, "w", encoding="utf-8") as ficheiro:
        json.dump(produtos, ficheiro, ensure_ascii=False, indent=4)

def procurar_produto(produtos, codigo):
    for produto in produtos:
        if produto["codigo"] == codigo:
            return produto

    return None

def atualizar_stock(produtos, codigo, nova_quantidade):
    produto = procurar_produto(produtos, codigo)

    if produto is None:
        return False

    produto["stock"] = nova_quantidade
    return True

# Programa principal
caminho_ficheiro = "produtos.json"
produtos = ler_produtos(caminho_ficheiro)

codigo = input("Introduza o código do produto: ")
nova_quantidade = int(input("Introduza a nova quantidade em stock: "))

if atualizar_stock(produtos, codigo, nova_quantidade):
    guardar_produtos(produtos, caminho_ficheiro)
    print("Stock atualizado com sucesso.")
else:
    print("Produto não encontrado.")
```

#### Exercício 31 - Gestor simples de tarefas

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Ficheiros JSON](./07_ficheiros_texto_json_csv.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria um programa com menu para gerir tarefas guardadas num ficheiro JSON.

Cada tarefa deve ter este formato:

```python
{
    "titulo": "Estudar funções",
    "concluida": False
}
```

O menu deve permitir:

1. Listar tarefas.
2. Adicionar tarefa.
3. Marcar tarefa como concluída.
4. Guardar e sair.

O programa deve estar organizado em funções. Usa `while` para manter o menu ativo até o utilizador escolher sair.

> Resolução:

```python
import json

def ler_tarefas(caminho):
    try:
        with open(caminho, "r", encoding="utf-8") as ficheiro:
            tarefas = json.load(ficheiro)

        return tarefas
    except FileNotFoundError:
        return []

def guardar_tarefas(tarefas, caminho):
    with open(caminho, "w", encoding="utf-8") as ficheiro:
        json.dump(tarefas, ficheiro, ensure_ascii=False, indent=4)

def listar_tarefas(tarefas):
    if len(tarefas) == 0:
        print("Não existem tarefas.")
    else:
        for indice in range(len(tarefas)):
            tarefa = tarefas[indice]

            if tarefa["concluida"]:
                estado = "concluída"
            else:
                estado = "por concluir"

            print(f"{indice + 1}. {tarefa['titulo']} - {estado}")

def adicionar_tarefa(tarefas, titulo):
    nova_tarefa = {
        "titulo": titulo,
        "concluida": False
    }

    tarefas.append(nova_tarefa)

def marcar_tarefa_concluida(tarefas, numero):
    indice = numero - 1

    if indice >= 0 and indice < len(tarefas):
        tarefas[indice]["concluida"] = True
        return True

    return False

def mostrar_menu():
    print()
    print("1. Listar tarefas")
    print("2. Adicionar tarefa")
    print("3. Marcar tarefa como concluída")
    print("4. Guardar e sair")

# Programa principal
caminho_ficheiro = "tarefas.json"
tarefas = ler_tarefas(caminho_ficheiro)
opcao = ""

while opcao != "4":
    mostrar_menu()
    opcao = input("Escolha uma opção: ")

    if opcao == "1":
        listar_tarefas(tarefas)
    elif opcao == "2":
        titulo = input("Introduza o título da tarefa: ")
        adicionar_tarefa(tarefas, titulo)
        print("Tarefa adicionada.")
    elif opcao == "3":
        listar_tarefas(tarefas)
        numero = int(input("Introduza o número da tarefa: "))

        if marcar_tarefa_concluida(tarefas, numero):
            print("Tarefa marcada como concluída.")
        else:
            print("Número de tarefa inválido.")
    elif opcao == "4":
        guardar_tarefas(tarefas, caminho_ficheiro)
        print("Tarefas guardadas. Programa terminado.")
    else:
        print("Opção inválida.")
```

#### Exercício 32 - Relatório de notas por turma

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Ficheiros JSON](./07_ficheiros_texto_json_csv.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria um programa que lê de um ficheiro JSON um dicionário de listas com notas por turma:

```python
{
    "10A": [12, 15, 18, 9],
    "10B": [10, 11, 14, 16]
}
```

O programa deve ter, pelo menos, estas funções:

- `ler_notas(caminho)`;
- `calcular_media(notas)`;
- `contar_negativas(notas)`;
- `criar_relatorio(turmas)`;
- `guardar_relatorio_json(relatorio, caminho)`.

O relatório final deve ser um dicionário com a média e o número de negativas de cada turma.

> Resolução:

```python
import json

def ler_notas(caminho):
    with open(caminho, "r", encoding="utf-8") as ficheiro:
        turmas = json.load(ficheiro)

    return turmas

def calcular_media(notas):
    soma = 0

    for nota in notas:
        soma = soma + nota

    media = soma / len(notas)
    return media

def contar_negativas(notas):
    contador = 0

    for nota in notas:
        if nota < 10:
            contador = contador + 1

    return contador

def criar_relatorio(turmas):
    relatorio = {}

    for turma in turmas:
        notas = turmas[turma]

        relatorio[turma] = {
            "media": calcular_media(notas),
            "negativas": contar_negativas(notas)
        }

    return relatorio

def guardar_relatorio_json(relatorio, caminho):
    with open(caminho, "w", encoding="utf-8") as ficheiro:
        json.dump(relatorio, ficheiro, ensure_ascii=False, indent=4)

# Programa principal
turmas = ler_notas("notas_turmas.json")
relatorio = criar_relatorio(turmas)
guardar_relatorio_json(relatorio, "relatorio_turmas.json")

print("Relatório criado com sucesso.")
print(relatorio)
```

![Footer](../Images/Footer.png)

#### Exercício 33 - Gestor de despesas pessoais

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Ficheiros JSON](./07_ficheiros_texto_json_csv.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Vamos criar um programa para gerir as despesas pessoais que são guardadas num ficheiro json.

As despesas devem ter o formato de lista de dicionários, em que cada elemento da lista é um dicionário com o seguinte formato:

```json
{
    "descricao": "Almoço",
    "categoria": "Alimentação",
    "valor": 8.5
}
```

O programa deve executar as seguintes funções:

- Listar despesas
- Adicionar despesas
- Calcular o gasto total das despesas
- Os dados devem ficar guardados.

O programa deve ter um menu com as opções do género:

```bash
****** Despesas Pro Max ******

1 - Listar todas as despesas
2 - Adicionar nova despesa
3 - Ver o total das despesas
4 - Sair
```

> Resolução:

```python

import json

def ler_despesas(caminho):
    with open(caminho, "r", encoding="utf-8") as ficheiro:
        despesas = json.load(ficheiro)
    return despesas

def guardar_despesas(despesas, caminho):
    with open(caminho, "w", encoding="utf-8") as ficheiro
        json.dump(despesas, ficheiro, ensure_ascii=False, indent=4)

def listar_despesas(despesas):
    if len(despesas) == 0:
        print("Não existem despesas registadas.")
    else:
        for despesa in despesas:
            print(f"Descrição: {despesa['descricao']}")
            print(f"Categoria: {despesa['categoria']}")
            print(f"Valor: {despesa['valor']}€")
            print("-" * 30)

def adicionar_despesa(despesas, descricao, categoria, valor):
    nova_despesa = {
        "descricao": descricao,
        "categoria": categoria,
        "valor": valor
    }
    despesas.append(nova_despesa)

def calcular_total(despesas):
    total = 0
    for despesa in despesas:
        total += despesa["valor"]
    return total

def mostrar_menu():
    print("\n****** Despesas Pro Max ******")
    print("1 - Listar todas as despesas")
    print("2 - Adicionar nova despesa")
    print("3 - Ver o total das despesas")
    print("4 - Sair")

# Programa principal
caminho_ficheiro = "despesas.json"
despesas = ler_despesas(caminho_ficheiro)
opcao = ""

while opcao != "4":
    mostrar_menu()
    opcao = input("Escolha uma opção: ")

    if opcao == "1":
        listar_despesas(despesas)
    elif opcao == "2":
        descricao = input("Introduza a descrição da despesa: ")
        categoria = input("Introduza a categoria da despesa: ")
        valor = float(input("Introduza o valor da despesa: "))
        adicionar_despesa(despesas, descricao, categoria, valor)
        print("Despesa adicionada com sucesso.")
    elif opcao == "3":
        total = calcular_total(despesas)
        print(f"O total das despesas é: {total:.2f}€")
    elif opcao == "4":
        guardar_despesas(despesas, caminho_ficheiro)
        print("Despesas guardadas. Programa terminado.")
    else:
        print("Opção inválida.")
```
