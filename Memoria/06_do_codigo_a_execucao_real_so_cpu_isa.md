# Memória (10.º Ano) - 06 · Do Código à Execução Real: SO, Kernel, CPU e ISA

> **Objetivo deste ficheiro**  
> Perceber, com calma e sem saltos, o caminho completo desde o código escrito por uma pessoa até à execução real no computador.
> Vamos ligar código-fonte, compilador/interpretador, sistema operativo, kernel, loader, processo, ISA, código de máquina e CPU.

---

**Pré-requisitos:** [`02_ram_rom_binario_bytes_enderecos.md`](02_ram_rom_binario_bytes_enderecos.md)

## Índice

- [0. Como usar este ficheiro](#0-como-usar-este-ficheiro)
- [1. Ideia principal: quem executa é sempre a CPU](#1-ideia-principal-quem-executa-é-sempre-a-cpu)
- [2. O caminho geral: do código à execução](#2-o-caminho-geral-do-código-à-execução)
- [3. Código-fonte, bytecode, assembly e código de máquina](#3-código-fonte-bytecode-assembly-e-código-de-máquina)
- [4. Binário vs código de máquina](#4-binário-vs-código-de-máquina)
- [5. O que é a ISA](#5-o-que-é-a-isa)
- [6. Muito importante: a ISA não converte instruções](#6-muito-importante-a-isa-não-converte-instruções)
- [7. Papel do sistema operativo e do kernel](#7-papel-do-sistema-operativo-e-do-kernel)
- [8. Loader: carregar um programa para memória](#8-loader-carregar-um-programa-para-memória)
- [9. Processo vs thread](#9-processo-vs-thread)
- [10. Modo utilizador, modo kernel e chamadas de sistema](#10-modo-utilizador-modo-kernel-e-chamadas-de-sistema)
- [11. Como a CPU processa uma instrução](#11-como-a-cpu-processa-uma-instrução)
- [12. Mini tabela ISA (nível introdutório)](#12-mini-tabela-isa-nível-introdutório)
- [13. Exemplo: executar um programa simples](#13-exemplo-executar-um-programa-simples)
- [14. Exemplo: executar Python](#14-exemplo-executar-python)
- [15. Caso real: abrir um programa](#15-caso-real-abrir-um-programa)
- [16. Caso real: abrir, editar e guardar um ficheiro](#16-caso-real-abrir-editar-e-guardar-um-ficheiro)
- [17. Erros comuns de interpretação](#17-erros-comuns-de-interpretação)
- [18. O que isto muda no teu raciocínio de programador](#18-o-que-isto-muda-no-teu-raciocínio-de-programador)
- [19. Resumo final](#19-resumo-final)
- [20. Changelog](#20-changelog)

---

## 0. Como usar este ficheiro

Este módulo é de integração. Junta vários níveis:

- linguagem de programação;
- ficheiros no disco;
- sistema operativo;
- memória;
- CPU;
- ISA;
- código de máquina.

É normal que alguns termos pareçam parecidos no início. O objetivo não é decorar nomes. O objetivo é perceber a cadeia:

```text
código escrito por humanos
-> transformação para algo executável
-> programa carregado pelo sistema operativo
-> instruções em memória
-> CPU busca, descodifica e executa essas instruções
```

Ao longo do ficheiro, vamos repetir várias vezes a mesma ideia com palavras diferentes. Isto é intencional: este tema é abstrato, e a repetição ajuda a construir o modelo mental correto.

---

## 1. Ideia principal: quem executa é sempre a CPU

Quando corres um programa, acontecem muitas coisas:

- o sistema operativo cria processos;
- a memória RAM recebe dados e instruções;
- o disco fornece ficheiros;
- o ecrã mostra resultados;
- o teclado e o rato enviam eventos;
- bibliotecas e frameworks ajudam o programa.

Mas, no fim da cadeia, existe uma regra essencial:

> Quem executa instruções é a CPU.

A CPU não executa ideias vagas como:

- "abrir documento";
- "mostrar botão";
- "somar lista";
- "guardar trabalho";
- "imprimir texto".

Essas ações são demasiado abstratas.

A CPU executa instruções muito mais simples, como:

- carregar um valor da memória;
- somar valores;
- comparar valores;
- saltar para outra parte do código;
- escrever um valor em memória;
- chamar uma rotina;
- pedir um serviço ao kernel.

Portanto, quando dizemos que "um programa corre", estamos a resumir uma realidade mais detalhada:

> O programa está representado por instruções de máquina, guardadas em memória, que a CPU vai buscar, descodificar e executar.

---

## 2. O caminho geral: do código à execução

Fluxo muito simplificado:

1. uma pessoa escreve código-fonte;
2. esse código é compilado, interpretado ou executado através de uma máquina virtual;
3. em algum ponto, existe código de máquina compatível com a ISA da CPU;
4. o sistema operativo cria um processo;
5. o loader carrega partes necessárias do programa para memória;
6. a CPU começa a executar instruções;
7. quando o programa precisa de serviços especiais, pede ajuda ao kernel.

Uma visão geral:

```text
programador
-> código-fonte
-> compilador / interpretador / máquina virtual
-> código de máquina compatível com uma ISA
-> sistema operativo cria processo e prepara memória
-> CPU executa instruções de máquina
-> programa produz efeitos: cálculos, ficheiros, rede, ecrã, etc.
```

### Nem todas as linguagens seguem exatamente o mesmo caminho

Um programa em C, por exemplo, costuma ser compilado antes de correr:

```text
código C
-> compilador
-> executável com código de máquina
-> SO carrega executável
-> CPU executa
```

Um programa em Python segue outro caminho:

```text
código Python (.py)
-> bytecode Python
-> PVM/interpretador executa o bytecode
-> CPU executa o interpretador, que já é um programa nativo
```

Ou seja, em Python a CPU não executa diretamente o teu `.py` nem o bytecode Python. A CPU executa o interpretador Python, e o interpretador implementa o significado do bytecode.

---

## 3. Código-fonte, bytecode, assembly e código de máquina

Para evitar confusões, vamos separar quatro níveis.

### 3.1 Código-fonte

É o texto que o programador escreve.

Exemplo em Python:

```python
print("Olá")
```

Exemplo em C:

```c
int x = 2 + 3;
```

O código-fonte é feito para humanos escreverem e lerem. A CPU não entende este texto diretamente.

### 3.2 Bytecode

Bytecode é um formato intermédio usado por algumas linguagens ou máquinas virtuais.

Em Python, o código `.py` é compilado para bytecode da Python Virtual Machine.

Esse bytecode:

- não é código-fonte normal;
- não é texto pensado para humanos;
- não é código de máquina nativo da CPU;
- é um conjunto de instruções para a máquina virtual Python.

Isto é importante:

> Bytecode Python é entendido pela PVM, não diretamente pela CPU.

### 3.3 Assembly

Assembly é uma forma textual, mais legível para humanos, de representar instruções próximas do código de máquina.

Exemplo conceptual:

```asm
LOAD R1, [1000]
ADD R1, R2
STORE [1000], R1
```

Assembly está muito perto da CPU, mas ainda é texto. Para a CPU executar, esse assembly precisa de ser transformado em código de máquina.

Essa transformação é feita por um programa chamado **assembler**.

### 3.4 Código de máquina

Código de máquina é o formato binário que a CPU consegue executar diretamente.

É composto por sequências de bits. Essas sequências seguem as regras de uma ISA.

Exemplo conceptual:

```text
10110000 00000101
```

Este exemplo não deve ser decorado. A ideia é apenas perceber que uma instrução real da CPU é guardada como bits.

Dentro desses bits podem existir partes como:

- **opcode**: indica a operação, por exemplo "somar" ou "carregar";
- identificadores de registos;
- valores imediatos;
- informação sobre endereços de memória;
- bits de controlo definidos pela arquitetura.

---

## 4. Binário vs código de máquina

Nem todo binário é código de máquina.

### Binário

Binário é uma forma de representar informação usando 0 e 1.

Pode representar:

- texto;
- imagens;
- sons;
- vídeos;
- números;
- ficheiros comprimidos;
- instruções da CPU.

### Código de máquina

Código de máquina é um caso especial de binário:

> É binário que a CPU interpreta como instruções executáveis.

Exemplo didático:

- `01000001` pode representar a letra `A`, se for interpretado como texto ASCII;
- outra sequência binária pode representar uma instrução da CPU;
- outra sequência pode ser parte de uma imagem;
- outra pode ser parte de um ficheiro `.docx`.

O significado dos bits depende do contexto.

Por isso, a regra é:

- todo código de máquina é binário;
- nem todo binário é código de máquina.

---

## 5. O que é a ISA

ISA significa **Instruction Set Architecture**.

Em português, podemos pensar nela como:

> a arquitetura do conjunto de instruções que uma família de CPUs consegue executar.

Exemplos de famílias ISA:

- x86-64, comum em muitos computadores pessoais;
- ARM64, comum em smartphones, tablets e alguns computadores modernos;
- RISC-V, uma ISA aberta usada em ensino, investigação e alguns sistemas.

### A ISA é como um contrato

A ISA define o que o software pode esperar da CPU.

Ela especifica, por exemplo:

- que instruções existem;
- como essas instruções são codificadas em bits;
- que registos são visíveis para o programador;
- como funcionam saltos e chamadas de funções;
- como se lê e escreve memória;
- como certas exceções ou chamadas especiais são feitas.

Ou seja:

```text
ISA = conjunto de regras que dizem:
"se aparecerem estes bits como instrução, a CPU deve comportar-se desta maneira"
```

### Exemplo conceptual

Imagina que uma ISA define uma instrução chamada `ADD`.

De forma simplificada, a ISA diz:

```text
ADD R1, R2
```

significa:

```text
somar o valor de R2 ao valor de R1
e guardar o resultado em R1
```

A CPU que implementa essa ISA tem de conseguir executar essa instrução com esse significado.

### ISA vs implementação física

Duas CPUs diferentes podem implementar a mesma ISA.

Por exemplo, dois processadores x86-64 podem executar os mesmos programas, mesmo que por dentro tenham circuitos diferentes.

Isto acontece porque ambos respeitam o mesmo "contrato" visível para o software: a ISA.

Por dentro, a CPU pode ter detalhes muito complexos:

- pipeline;
- cache;
- execução fora de ordem;
- micro-operações internas;
- predição de saltos.

Mas para este nível, a ideia principal é:

> O software vê a ISA. A CPU física implementa essa ISA.

---

## 6. Muito importante: a ISA não converte instruções

Este é o ponto mais importante deste ficheiro.

É tentador dizer:

> "As instruções chegam à ISA e a ISA converte para algo que o processador entende."

Mas isto não está correto.

A ISA **não é um tradutor**.

A ISA também não é:

- um programa;
- uma peça física isolada;
- uma camada que transforma comandos;
- um componente do sistema operativo;
- uma máquina virtual.

A ISA é uma especificação. É um conjunto de regras.

### Então quem converte?

Depende do caso.

Num programa compilado, como C ou C++:

```text
código-fonte
-> compilador
-> assembly ou código intermédio
-> assembler/linker
-> código de máquina compatível com uma ISA
```

Num programa em Python:

```text
código Python
-> bytecode Python
-> interpretador Python executa esse bytecode
-> CPU executa o interpretador Python, que já está em código de máquina
```

Num programa Java, simplificando:

```text
código Java
-> bytecode Java
-> JVM interpreta ou compila partes para código de máquina
-> CPU executa código de máquina
```

Portanto, quem faz transformações são ferramentas ou runtimes:

- compiladores;
- assemblers;
- linkers;
- interpretadores;
- máquinas virtuais;
- JIT compilers, em alguns casos.

A ISA não transforma. A ISA define o alvo.

### Frase correta

Em vez de dizer:

```text
O SO manda instruções para a ISA, e a ISA converte para a CPU.
```

Devemos dizer:

```text
O programa contém código de máquina compatível com uma ISA.
A CPU implementa essa ISA.
Quando a CPU busca uma instrução da memória, descodifica os bits segundo as regras da ISA e executa a operação.
```

### Outra frase correta

Para o kernel:

```text
O kernel também é software.
Ele foi compilado para código de máquina compatível com a ISA da CPU.
Quando o kernel está a correr, a CPU executa instruções do kernel tal como executa outras instruções de máquina, mas em modo privilegiado.
```

---

## 7. Papel do sistema operativo e do kernel

O sistema operativo é o software que gere o computador.

Exemplos:

- Windows;
- Linux;
- macOS;
- Android;
- iOS.

O sistema operativo inclui muitas partes:

- interface gráfica;
- gestor de ficheiros;
- drivers;
- serviços;
- bibliotecas;
- ferramentas;
- kernel.

### O que é o kernel?

O **kernel** é o núcleo do sistema operativo.

É a parte com mais responsabilidade e mais privilégios.

O kernel gere recursos fundamentais:

- processos;
- threads;
- memória;
- permissões;
- ficheiros;
- dispositivos;
- comunicação com hardware;
- escalonamento da CPU.

### O kernel também é código

Isto é muito importante:

> O kernel não é magia fora da CPU. O kernel também é um programa, escrito por programadores, compilado para código de máquina e executado pela CPU.

A diferença é que o kernel corre com permissões especiais.

Enquanto um programa normal não pode fazer tudo o que quiser, o kernel pode executar operações privilegiadas, como:

- configurar memória virtual;
- falar diretamente com drivers;
- gerir interrupções;
- decidir que processo usa a CPU;
- controlar acesso a dispositivos.

### O que o SO faz quando abres um programa?

De forma simplificada:

1. recebe o pedido para abrir o programa;
2. verifica permissões;
3. localiza o executável no disco;
4. cria um processo;
5. prepara o espaço de memória do processo;
6. carrega ou mapeia partes do programa na RAM;
7. prepara stack, heap e argumentos iniciais;
8. define o ponto onde a execução deve começar;
9. deixa a CPU começar a executar esse processo quando chegar a sua vez.

O SO não "inventa" instruções da CPU a cada momento para o teu programa. O executável já contém código de máquina. O SO prepara o ambiente para esse código poder correr corretamente e em segurança.

---

## 8. Loader: carregar um programa para memória

O **loader** é a parte do sistema que prepara um programa para começar a correr.

Quando abres um programa, o loader, com apoio do sistema operativo, faz uma sequência parecida com esta:

1. localiza o ficheiro executável no disco;
2. verifica se o formato é válido;
3. cria um novo processo;
4. cria um espaço de endereçamento virtual para esse processo;
5. mapeia secções do executável para memória;
6. prepara a stack inicial;
7. prepara dados iniciais;
8. liga bibliotecas necessárias, quando aplicável;
9. define o ponto de entrada;
10. permite que o escalonador coloque esse processo na CPU.

### Secções típicas de um executável

Um executável pode ter várias zonas, por exemplo:

- zona de código, com instruções de máquina;
- zona de dados inicializados;
- zona de dados não inicializados;
- informação para bibliotecas;
- metadados usados pelo loader.

Para 10.º ano, não é preciso decorar estes nomes. O essencial é:

> Um executável não é só "um ficheiro qualquer". Ele tem uma estrutura que o sistema operativo sabe carregar para criar um processo.

---

## 9. Processo vs thread

### Processo

Um processo é uma instância de um programa em execução.

Quando abres duas vezes o mesmo programa, podes ter dois processos diferentes.

Cada processo tem, de forma simplificada:

- código a executar;
- espaço de memória próprio;
- stack;
- heap;
- identificador do processo;
- permissões;
- recursos abertos, como ficheiros ou sockets;
- estado de execução.

### Thread

Uma thread é um fluxo de execução dentro de um processo.

Um processo pode ter várias threads.

Exemplo:

- uma thread trata da interface gráfica;
- outra thread faz uma operação em segundo plano;
- outra thread espera por dados da rede.

### Diferença prática

Processos isolam melhor:

- cada processo tem o seu espaço de memória;
- um processo não deve ler livremente a memória de outro.

Threads comunicam mais facilmente:

- threads do mesmo processo partilham a mesma memória do processo;
- isto ajuda em desempenho, mas também pode causar erros se houver acesso concorrente mal controlado.

---

## 10. Modo utilizador, modo kernel e chamadas de sistema

Um programa normal não deve ter poder total sobre o computador.

Imagina se qualquer programa pudesse:

- apagar ficheiros de outros utilizadores;
- ler passwords;
- escrever diretamente no disco sem controlo;
- aceder livremente à memória de outros programas;
- controlar a placa de rede sem permissões.

Seria inseguro.

Por isso, CPUs modernas e sistemas operativos usam níveis de privilégio.

### Modo utilizador

É o modo em que correm os programas normais.

Exemplos:

- editor de texto;
- browser;
- jogo;
- programa Python;
- aplicação de gestão.

Em modo utilizador, o programa tem limites. Não pode fazer diretamente certas operações perigosas ou sensíveis.

### Modo kernel

É o modo privilegiado.

O kernel corre neste modo.

Aqui é possível executar operações que um programa normal não pode fazer diretamente.

### Então como um programa pede ajuda ao kernel?

Usa uma **chamada de sistema**, em inglês **system call** ou **syscall**.

Uma syscall é um pedido formal ao kernel.

Exemplos de coisas que normalmente envolvem o kernel:

- abrir ficheiro;
- ler ficheiro;
- escrever ficheiro;
- criar processo;
- pedir memória;
- enviar dados pela rede;
- receber dados do teclado;
- desenhar através de serviços gráficos;
- terminar programa.

### Exemplo: guardar um ficheiro

Quando um programa quer guardar um ficheiro:

1. o programa organiza os dados em memória;
2. chama uma função de biblioteca, por exemplo "write" ou equivalente;
3. essa função prepara uma chamada ao sistema;
4. a CPU executa uma instrução especial de entrada no kernel;
5. o CPU muda para modo kernel;
6. o kernel verifica permissões e validade do pedido;
7. o kernel comunica com o sistema de ficheiros e drivers;
8. a operação é realizada ou falha;
9. o kernel devolve resultado;
10. a CPU volta ao modo utilizador;
11. o programa continua.

### Exemplos de instruções especiais

Diferentes ISAs usam nomes diferentes.

Exemplos:

- em x86-64 pode existir uma instrução como `syscall`;
- em ARM pode existir uma instrução como `SVC`;
- em RISC-V pode existir uma instrução como `ecall`.

Não precisas decorar estes nomes. A ideia é:

> Há instruções especiais que permitem ao programa pedir um serviço ao kernel de forma controlada.

---

## 11. Como a CPU processa uma instrução

A CPU repete constantemente um ciclo básico:

```text
fetch -> decode -> execute
```

Em português:

```text
buscar -> descodificar -> executar
```

Vamos detalhar.

### 11.1 Program Counter / Instruction Pointer

A CPU tem um registo especial que guarda onde está a próxima instrução.

Dependendo da arquitetura, pode chamar-se:

- Program Counter, muitas vezes abreviado como PC;
- Instruction Pointer, muitas vezes abreviado como IP.

Pensa nele como:

> "o marcador de página" da CPU.

Ele aponta para a posição de memória onde está a próxima instrução a executar.

### 11.2 Fetch: buscar a instrução

No passo de fetch:

1. a CPU olha para o endereço guardado no PC/IP;
2. pede à memória a instrução que está nesse endereço;
3. essa instrução pode vir da cache, se já estiver perto da CPU;
4. a instrução chega à CPU como bits.

De forma simplificada:

```text
PC/IP aponta para endereço X
CPU busca os bits guardados em X
```

### 11.3 Decode: descodificar a instrução

No passo de decode:

1. a CPU analisa os bits da instrução;
2. interpreta esses bits segundo as regras da ISA;
3. percebe que operação deve fazer;
4. identifica registos, valores ou endereços envolvidos.

Aqui a ISA é essencial.

Mas atenção:

> A ISA não está a converter. A CPU está a descodificar uma instrução usando as regras definidas pela ISA.

Exemplo conceptual:

```text
bits recebidos -> CPU percebe: "isto é uma instrução ADD"
```

### 11.4 Execute: executar a operação

No passo de execute, a CPU realiza a operação.

Dependendo da instrução, pode:

- usar a ALU para somar;
- comparar valores;
- ler memória;
- escrever memória;
- saltar para outro endereço;
- chamar uma função;
- alterar registos;
- entrar no kernel através de uma instrução especial.

### 11.5 Atualizar estado

Depois de executar, a CPU atualiza o seu estado.

Normalmente:

- altera registos;
- altera flags;
- altera memória, se a instrução escrever algo;
- avança o PC/IP para a próxima instrução.

Se houver um salto, o PC/IP pode mudar para outro endereço.

Exemplo:

```text
sem salto:
PC/IP passa para a instrução seguinte

com salto:
PC/IP passa para outro ponto do programa
```

### 11.6 O que acontece por dentro pode ser mais complexo

CPUs modernas podem fazer coisas avançadas:

- executar várias instruções em pipeline;
- prever saltos;
- reordenar operações internas;
- transformar instruções complexas em micro-operações internas.

Mas, para o software, o comportamento final tem de respeitar a ISA.

Para este módulo, fica com a ideia:

> A CPU pode ser muito complexa por dentro, mas o modelo básico para aprender é fetch, decode, execute.

---

## 12. Mini tabela ISA (nível introdutório)

> Isto é conceptual. Não é para decorar assembly.

| Instrução conceptual | Ideia                    | Efeito simplificado                        |
| -------------------- | ------------------------ | ------------------------------------------ |
| `LOAD R1, [addr]`    | Carregar dado da memória | R1 recebe valor guardado em `addr`         |
| `ADD R1, R2`         | Somar registos           | R1 passa a ter R1 + R2                     |
| `STORE [addr], R1`   | Guardar em memória       | Valor de R1 é escrito em `addr`            |
| `CMP R1, R2`         | Comparar valores         | CPU atualiza flags de comparação           |
| `JMP label`          | Salto                    | Execução continua noutra posição de código |
| `CALL func`          | Chamada de função        | CPU salta para uma função/rotina           |
| `RET`                | Retorno                  | CPU volta ao ponto depois da chamada       |

Estas instruções são exemplos didáticos. Cada ISA real tem a sua própria sintaxe e detalhes.

O que interessa perceber:

> Programas complexos são construídos a partir de muitas instruções simples.

---

## 13. Exemplo: executar um programa simples

Imagina este código numa linguagem compilada:

```c
int a = 2;
int b = 3;
int c = a + b;
```

O programador vê:

```text
c = a + b
```

Mas a CPU não recebe essa frase.

Depois de compilação, a ideia pode aproximar-se de algo como:

```text
carregar 2 para um registo
carregar 3 para outro registo
somar os dois registos
guardar resultado
```

Em instruções conceptuais:

```asm
LOAD R1, 2
LOAD R2, 3
ADD R1, R2
STORE [c], R1
```

Mais uma vez: isto é conceptual.

O programa real teria instruções concretas da ISA real da máquina.

### Onde entra a ISA aqui?

A ISA define:

- se existe uma instrução parecida com `ADD`;
- como se representa essa instrução em bits;
- que registos existem;
- como os operandos são indicados;
- como a CPU deve alterar o estado depois da instrução.

### Onde entra a CPU?

A CPU:

1. busca os bits da instrução;
2. descodifica esses bits segundo a ISA;
3. executa a operação usando os seus circuitos;
4. passa à instrução seguinte.

---

## 14. Exemplo: executar Python

Agora vamos usar Python, porque é o contexto mais próximo destes materiais.

Código:

```python
def soma(a, b):
    return a + b

print(soma(2, 3))
```

O percurso simplificado é:

```text
ficheiro .py
-> interpretador Python lê o ficheiro
-> Python compila para bytecode
-> PVM executa o bytecode
-> o interpretador Python, que é código nativo, corre na CPU
-> quando é preciso I/O, o interpretador pede serviços ao SO/kernel
```

### Ponto essencial

O bytecode Python não é código de máquina da CPU.

O bytecode Python é para a PVM.

A CPU executa o interpretador Python, que por sua vez interpreta o bytecode.

### Então onde está o código de máquina?

Está principalmente no próprio interpretador Python e nas bibliotecas nativas usadas por ele.

Em CPython, por exemplo:

- o interpretador é um programa nativo;
- esse programa já foi compilado para a ISA da tua máquina;
- a CPU executa as instruções de máquina desse interpretador;
- o interpretador implementa as regras da linguagem Python.

### Exemplo mental

Quando o bytecode diz algo como:

```text
somar estes dois objetos Python
```

A PVM não passa simplesmente essa instrução à CPU.

Em vez disso, o interpretador executa código nativo que:

1. verifica que objetos são;
2. decide como somá-los;
3. chama as rotinas internas adequadas;
4. cria ou devolve o objeto resultado;
5. atualiza a stack interna da PVM.

Por isso:

> O CPU não "sabe Python". O CPU executa um programa que sabe Python: o interpretador.

---

## 15. Caso real: abrir um programa

Exemplo: abrir um editor de texto.

Fluxo simplificado:

1. clicas no ícone;
2. a interface do sistema operativo recebe o evento;
3. o SO identifica o programa que deve abrir;
4. o SO verifica permissões;
5. o loader prepara o processo;
6. partes do executável são mapeadas para memória;
7. bibliotecas necessárias podem ser carregadas;
8. o processo fica pronto para executar;
9. o escalonador decide quando esse processo usa a CPU;
10. a CPU começa a executar instruções de máquina desse programa;
11. a interface aparece no ecrã.

Repara no detalhe:

> O SO não converte cada clique em instruções da ISA.
> O SO e o programa já têm código de máquina. A CPU executa esse código.

---

## 16. Caso real: abrir, editar e guardar um ficheiro

Exemplo: abrir e editar `trabalho.docx`.

### 16.1 Abrir o ficheiro

Fluxo simplificado:

1. o utilizador escolhe o ficheiro;
2. o programa pede ao SO para abrir o ficheiro;
3. esse pedido envolve uma chamada de sistema;
4. o kernel verifica permissões;
5. o sistema de ficheiros localiza os dados no disco;
6. blocos relevantes são lidos;
7. dados vão para RAM;
8. o programa interpreta o formato `.docx`;
9. o conteúdo é mostrado ao utilizador.

O ficheiro não fica apenas no disco durante a edição.

Partes importantes passam para memória, porque é em memória que o programa trabalha de forma eficiente.

### 16.2 Editar

Quando escreves uma frase:

1. o teclado gera eventos;
2. o sistema operativo entrega esses eventos à aplicação correta;
3. o programa atualiza estruturas internas em memória;
4. a interface gráfica é redesenhada;
5. a CPU executa muitas instruções para processar tudo isto.

Enquanto editas, a alteração pode estar apenas em memória.

Isto significa:

> Ver a alteração no ecrã não garante que ela já esteja gravada no disco.

### 16.3 Guardar

Quando carregas em guardar:

1. o programa organiza o documento no formato correto;
2. prepara os bytes que devem ser escritos;
3. pede ao SO para escrever no ficheiro;
4. o pedido passa pelo kernel;
5. o kernel valida permissões;
6. o sistema de ficheiros decide onde escrever;
7. os dados são enviados para o dispositivo de armazenamento;
8. o SO/programa recebe confirmação ou erro.

Só depois de uma escrita bem-sucedida é que existe persistência real no armazenamento.

---

## 17. Erros comuns de interpretação

### Erro 1: "A ISA converte instruções"

Errado.

A ISA define o significado das instruções.

Mais correto:

```text
A CPU descodifica e executa instruções segundo a ISA.
```

### Erro 2: "O SO transforma sempre ações em instruções para a CPU"

Incompleto e enganador.

O SO gere recursos, cria processos, protege memória, fornece serviços e executa código privilegiado.

Mas o programa e o kernel já estão representados em código de máquina quando são executados pela CPU.

Mais correto:

```text
O SO prepara e controla o ambiente de execução.
A CPU executa código de máquina do programa e do kernel.
```

### Erro 3: "Python é executado diretamente pela CPU"

Errado.

Mais correto:

```text
A CPU executa o interpretador Python.
O interpretador executa o bytecode Python.
```

### Erro 4: "Binário é sempre código de máquina"

Errado.

Binário pode representar muitas coisas:

- texto;
- imagem;
- som;
- número;
- ficheiro;
- instrução.

Código de máquina é apenas binário que a CPU interpreta como instruções.

### Erro 5: "O kernel está fora deste processo de execução"

Errado.

O kernel também é software compilado para código de máquina. A CPU executa instruções do kernel quando há interrupções, chamadas de sistema ou outras situações privilegiadas.

---

## 18. O que isto muda no teu raciocínio de programador

Compreender este percurso ajuda-te a perceber que linguagens de alto nível são camadas de abstração.

Quando escreves:

```python
print("Olá")
```

parece uma ação simples.

Mas por baixo podem existir:

- bytecode Python;
- execução no interpretador;
- chamadas a bibliotecas;
- chamadas ao sistema operativo;
- validação pelo kernel;
- escrita para um terminal, janela ou buffer;
- instruções de máquina executadas pela CPU;
- leituras e escritas em memória.

Isto não quer dizer que tenhas de pensar em tudo isto sempre que programas.

Mas ajuda-te a entender:

- porque algumas operações são mais lentas;
- porque ler disco é diferente de ler RAM;
- porque I/O depende do sistema operativo;
- porque Python não é executado diretamente pelo processador;
- porque código de máquina depende da arquitetura;
- porque segurança e permissões importam;
- porque o sistema operativo controla recursos partilhados.

---

## 19. Resumo final

- Código-fonte é escrito por humanos.
- A CPU não executa código-fonte diretamente.
- Código de máquina é binário executável pela CPU.
- A ISA define o conjunto de instruções e o significado dos bits de instrução.
- A ISA não converte instruções.
- Compiladores, assemblers, linkers, interpretadores e máquinas virtuais podem transformar ou executar código.
- O sistema operativo cria processos, gere memória, permissões, ficheiros e escalonamento.
- O kernel é o núcleo privilegiado do sistema operativo.
- O kernel também é código de máquina executado pela CPU.
- O loader prepara o programa para execução.
- A CPU executa o ciclo `fetch -> decode -> execute`.
- No `decode`, a CPU interpreta os bits da instrução segundo a ISA.
- Programas normais correm em modo utilizador.
- Operações sensíveis são pedidas ao kernel através de chamadas de sistema.
- Em Python, a CPU executa o interpretador; o interpretador executa o bytecode Python.

Frase final para decorar:

> A ISA é o "manual de instruções" que define o que a CPU sabe executar; o processador é quem descodifica e executa; o sistema operativo prepara, protege e gere o ambiente onde os programas correm.

---

**A seguir:** [`04_heap_stack_frames_e_execucao_python.md`](04_heap_stack_frames_e_execucao_python.md)

---

## 20. Changelog

- **2026-02-04**: versão inicial do módulo 06 (execução real, SO, CPU, ISA e ficheiros).
- **2026-05-19**: clarificada a diferença entre ISA, código de máquina, CPU, SO e kernel; adicionadas explicações sobre syscalls, modos de execução e correção explícita da ideia de que "a ISA converte instruções".
