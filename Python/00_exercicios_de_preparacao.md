# Python (10.º Ano) - 00 · Exercicios de preparação

> **Objetivo deste ficheiro**  
> Preparar os alunos para as avaliações, através de exercícios que envolvem os conceitos básicos de Python.

## Preparação para o teste de 30/04/2026

### Exercícios

**Fundamentos (variáveis, operadores, controlo de fluxo, listas e dicionários)**

1. Lê dois números inteiros com `input()`, converte para `int` e imprime a soma, a diferença, o produto, a divisão e o resto.

2. Lê uma temperatura em Celsius (`float`) e converte para Fahrenheit. Usa a formula seguinte para a conversão: `F = C * 9/5 + 32`. Imprime o resultado.

3. Lê um número inteiro `N` e imprime todos os números pares entre 0 e `N` (inclusive), um por linha.

4. Lê 5 notas (0-20), guarda numa lista, calcula a média e indica quantas negativas existem.

5. Cria um dicionário para representar um aluno com as chaves `nome`, `turma` e `notas` (lista com 3 valores). Calcula a média desse aluno.

Depois imprime tudo com o formato:

```
Aluno: [nome]
Turma: [turma]
Notas: [notas]
Média: [média]
```

6. Cria uma função que calcule a área de um retângulo. A função deve receber a largura e a altura como parâmetros e imprimir a área.

7. Escreve uma função que receba uma lista de números e imprima cada número multiplicado por 2. Depois testa a função com uma lista de 5 números à tua escolha.

8. Cria uma função que receba uma lista de números e retorne a soma de todos os números pares na lista.

9. Escreve uma função que receba uma string e retorne o número de vogais na string.

10. Escreve uma função que recebe dois parâmetros: uma lista de números e um número. A função deve retornar `True` se o número estiver na lista e `False` caso contrário.

11. Cria uma função que recebe um dicionário e o mostre de forma organizada.

12. Cria uma função que receba uma lista de dicionários (cada dicionário representa uma pessoa com nome e idade) e retorne a média das idades.

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

14. Pede ao utilizador para introduzir o nome, idade e cidade. Guarda estes dados num ficheiro JSON com o formato de um dicionário.

15. Lê o ficheiro JSON criado no exercício anterior e imprime os dados de forma organizada.

16. Cria um módulo `math_utils.py` com as funções `soma(a, b)`, `subtracao(a, b)`, `multiplicacao(a, b)` e `divisao(a, b)`.
    Usa-o no ficheiro `main.py` com `import math_utils` e números pedidos ao utilizador.

17. Cria um módulo `texto_utils.py` com a função `contar_vogais(texto)` e usa `from texto_utils import contar_vogais` num ficheiro principal.
