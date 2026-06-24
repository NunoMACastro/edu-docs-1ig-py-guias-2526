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

#### Exercício 2 - Dobro de um número

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md)

Cria uma função chamada `calcular_dobro(numero)` que recebe um número e devolve o seu dobro.

No programa principal, pede um número ao utilizador, chama a função e mostra o resultado.

#### Exercício 3 - Área de um retângulo

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md)

Cria uma função chamada `calcular_area_retangulo(largura, altura)` que recebe a largura e a altura de um retângulo e devolve a área.

No programa principal, pede os dois valores ao utilizador e mostra a área calculada.

#### Exercício 4 - Conversão de temperatura

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md)

Cria uma função chamada `converter_celsius_para_fahrenheit(celsius)` que recebe uma temperatura em graus Celsius e devolve a temperatura em Fahrenheit.

Usa a fórmula:

```text
F = C * 9 / 5 + 32
```

#### Exercício 5 - Número par

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `e_par(numero)` que recebe um número inteiro e devolve:

- `True`, se o número for par;
- `False`, se o número for ímpar.

No programa principal, pede um número ao utilizador e mostra uma mensagem adequada.

#### Exercício 6 - Maior de dois números

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `maior_de_dois(a, b)` que recebe dois números e devolve o maior.

Se os números forem iguais, a função deve devolver a mensagem:

```text
Os números são iguais.
```

#### Exercício 7 - Classificação de uma nota

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `classificar_nota(nota)` que recebe uma nota entre 0 e 20 e devolve uma classificação textual:

- menor que 10: `Negativa`;
- de 10 a 13: `Suficiente`;
- de 14 a 17: `Boa`;
- de 18 a 20: `Muito boa`;
- fora do intervalo 0-20: `Nota inválida`.

#### Exercício 8 - Contar de 1 até N

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `mostrar_contagem(n)` que recebe um número inteiro positivo e mostra todos os números de 1 até `n`.

No programa principal, pede o valor de `n` ao utilizador.

#### Exercício 9 - Somatório até N

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `calcular_somatorio(n)` que recebe um número inteiro positivo e devolve a soma de todos os números de 1 até `n`.

Exemplo do cálculo pretendido para `n = 5`:

```text
1 + 2 + 3 + 4 + 5
```

#### Exercício 10 - Tabuada

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `mostrar_tabuada(numero)` que recebe um número e mostra a tabuada desse número de 1 até 10.

No programa principal, pede o número ao utilizador e chama a função.

#### Exercício 11 - Contar vogais

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `contar_vogais(texto)` que recebe uma frase e devolve o número de vogais existentes nessa frase.

Deves considerar, pelo menos, as vogais:

```text
a e i o u
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

#### Exercício 13 - Palavra repetida

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `repetir_palavra(palavra, vezes)` que recebe uma palavra e um número inteiro.

A função deve mostrar a palavra o número de vezes indicado.

Se o número de vezes for menor ou igual a 0, deve mostrar:

```text
Número inválido.
```

#### Exercício 14 - Validar idade

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `validar_idade(idade)` que recebe uma idade e devolve:

- `Criança`, se a idade for menor que 13;
- `Adolescente`, se estiver entre 13 e 17;
- `Adulto`, se for 18 ou mais;
- `Idade inválida`, se for negativa.

### Funções com listas e dicionários

#### Exercício 15 - Soma dos números pares

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `somar_pares(numeros)` que recebe uma lista de números inteiros e devolve a soma apenas dos números pares.

Testa a função com uma lista criada por ti.

#### Exercício 16 - Contar negativas

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `contar_negativas(notas)` que recebe uma lista de notas e devolve quantas notas são negativas.

Considera negativa qualquer nota menor que 10.

#### Exercício 17 - Média de uma lista

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `calcular_media(numeros)` que recebe uma lista de números e devolve a média.

Se a lista estiver vazia, a função deve devolver:

```text
Lista vazia.
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

#### Exercício 19 - Procurar nome numa lista

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `procurar_nome(nomes, nome_procurado)` que recebe:

- uma lista de nomes;
- um nome a procurar.

A função deve devolver `True` se o nome existir na lista e `False` caso contrário.

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

### Funções com ficheiros JSON

#### Exercício 25 - Guardar aluno em JSON

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Ficheiros JSON](./07_ficheiros_texto_json_csv.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md)

Cria uma função chamada `guardar_aluno_json(aluno, caminho)` que recebe:

- um dicionário com os dados de um aluno;
- o caminho do ficheiro JSON.

A função deve guardar o dicionário no ficheiro indicado.

#### Exercício 26 - Ler aluno de JSON

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Ficheiros JSON](./07_ficheiros_texto_json_csv.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md)

Cria uma função chamada `ler_aluno_json(caminho)` que recebe o caminho de um ficheiro JSON e devolve o dicionário lido desse ficheiro.

No programa principal, mostra os dados do aluno de forma organizada.

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

#### Exercício 28 - Ler lista de contactos

**Matéria:** [Funções](./04_funcoes_do_basico_ao_avancado.md), [Ficheiros JSON](./07_ficheiros_texto_json_csv.md), [Listas e dicionários](./03_listas_dicionarios_estruturas_aninhadas.md), [Seleção e repetição](./02_operadores_e_controlo_de_fluxo_if_ciclos.md)

Cria uma função chamada `ler_contactos(caminho)` que lê uma lista de contactos a partir de um ficheiro JSON.

Depois, cria outra função chamada `mostrar_contactos(contactos)` que recebe a lista e mostra todos os contactos de forma organizada.

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

![Footer](../Images/Footer.png)
