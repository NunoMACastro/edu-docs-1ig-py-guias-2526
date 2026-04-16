# Formulário de Apoio às Avaliações

## Variáveis

```python
x = 10  # Variável com valor inteiro
y = 5.5  # Variável com valor float
nome = "João"  # Variável com valor string
booleano = True  # Variável com valor booleano
```

## Operadores

```python
+ # Operador de adição
- # Operador de subtração
* # Operador de multiplicação
/ # Operador de divisão
% # Operador de módulo
** # Operador de potência
// # Operador de divisão inteira
< # Operador de comparação menor que
> # Operador de comparação maior que
== # Operador de comparação de igualdade
!= # Operador de comparação de desigualdade
and # Operador lógico AND
or # Operador lógico OR
not # Operador lógico NOT
```

## Entradas e Saídas

```python
# Entrada de dados
nome = input("Digite seu nome: ")  # Recebe uma string do utilizador
idade = int(input("Digite sua idade: "))  # Recebe um inteiro do utilizador
# Saída de dados
print("Olá, " + nome + "! Você tem " + str(idade) + " anos.")  # Exibe uma mensagem formatada
# Usando f-strings para formatação
print(f"Olá, {nome}! Você tem {idade} anos.")  # Exibe a mesma mensagem usando f-strings
```

## Estruturas de Controle

```python
# Estrutura condicional
if idade < 18:
    print("Você é menor de idade.")
elif idade >= 18 and idade < 65:
    print("Você é adulto.")
else:
    print("Você é idoso.")

# Estrutura de repetição

# While loop
contador = 0
while contador < 5:
    print(contador)
    contador += 1

# Range e for loop
range(5)  # Gera uma sequência de números de 0 a 4
range(1, 5)  # Gera uma sequência de números de 1 a 4
range(1, 10, 2)  # Gera uma sequência de números de 1 a 9, indo de 2 em 2

for i in range(5):
    print(i)  # Imprime os números de 0 a 4
```

## Listas

```python
# Criar uma lista
frutas = ["maçã", "banana", "laranja"]
# Aceder a elementos da lista
print(frutas[0])  # Imprime "maçã"
print(frutas[1])  # Imprime "banana"
print(frutas[2])  # Imprime "laranja"
# Modificar elementos da lista
frutas[1] = "uva"  # Substitui "banana" por "uva"
print(frutas)  # Imprime ["maçã", "uva", "laranja"]
# Adicionar elementos à lista
frutas.append("ananás")  # Adiciona "ananás" ao final da lista
print(frutas)  # Imprime ["maçã", "uva", "laranja", "ananás"]
# Remover elementos da lista
frutas.remove("maçã")  # Remove "maçã" da lista
print(frutas)  # Imprime ["uva", "laranja", "ananás"]
```

- Percorrer uma lista com um loop

```python
for fruta in frutas:
    print(fruta)  # Imprime cada fruta na lista
```

## Dicionários

```python
# Criar um dicionário
pessoa = {
    "nome": "João",
    "idade": 30,
    "cidade": "Lisboa"
}
# Aceder a valores do dicionário
print(pessoa["nome"])  # Imprime "João"
print(pessoa["idade"])  # Imprime 30
print(pessoa["cidade"])  # Imprime "Lisboa"
# Modificar valores do dicionário
pessoa["idade"] = 31  # Atualiza a idade para 31
print(pessoa)  # Imprime {'nome': 'João', 'idade': 31, 'cidade': 'Lisboa'}


# Adicionar novos pares chave-valor ao dicionário
pessoa["profissão"] = "Engenheiro"  # Adiciona a profissão ao dicionário
print(pessoa)  # Imprime {'nome': 'João', 'idade': 31, 'cidade': 'Lisboa', 'profissão': 'Engenheiro'}
# Remover um par chave-valor do dicionário
del pessoa["cidade"]  # Remove a chave "cidade" e seu valor do dicionário
print(pessoa)  # Imprime {'nome': 'João', 'idade': 31, 'profissão': 'Engenheiro'}
```

- Percorrer um dicionário com um loop

```python
# percorrer as chaves do dicionário
for chave in pessoa:
    print(chave)  # Imprime cada chave do dicionário
# percorrer os valores do dicionário
for valor in pessoa.values():
    print(valor)  # Imprime cada valor do dicionário
# percorrer os pares chave-valor do dicionário
for chave, valor in pessoa.items():
    print(f"{chave}: {valor}")  # Imprime cada chave e seu valor
```
