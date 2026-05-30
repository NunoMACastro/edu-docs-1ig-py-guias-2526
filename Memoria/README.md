![Header](../Images/Header.png)

[Voltar ao README principal](../README.md)

# Memória · 10.º Ano (Informática de Gestão)

Materiais de apoio em formato **Markdown** sobre memória de computador, execução de programas e gestão de memória em Python.

Estes ficheiros foram escritos para alunos em fase inicial, com explicações muito guiadas, linguagem simples, esquemas e foco em compreensão real dos conceitos.

A rota principal segue uma ideia central:

```text
Fundamentos físicos e digitais
-> tipos de memória
-> bits, binário, bytes e endereços
-> execução de Python no contexto de memória
-> referências, mutabilidade e garbage collection
-> do Python à execução real: sistema operativo, CPU, ISA e ALU
```

O anexo `A1` contém matéria complementar sobre estruturas dinâmicas e complexidade. Essa matéria é importante, mas não faz parte do fio principal do módulo de memória.

---

## Índice

- [`00_fundamentos_hardware_bits_cpu_memoria.md`](00_fundamentos_hardware_bits_cpu_memoria.md)
- [`01_tipos_de_memoria_cache_ram_rom_disco.md`](01_tipos_de_memoria_cache_ram_rom_disco.md)
- [`02_bits_binario_bytes_enderecos.md`](02_bits_binario_bytes_enderecos.md)
- [`03_heap_stack_frames_e_execucao_python.md`](03_heap_stack_frames_e_execucao_python.md)
- [`04_referencias_mutabilidade_gc_em_python.md`](04_referencias_mutabilidade_gc_em_python.md)
- [`05_do_python_a_execucao_real_so_cpu_isa_alu.md`](05_do_python_a_execucao_real_so_cpu_isa_alu.md)
- [`A1_estruturas_dinamicas_e_complexidade.md`](A1_estruturas_dinamicas_e_complexidade.md)
- [Rota de estudo recomendada](#rota-de-estudo-recomendada)

---

### `00_fundamentos_hardware_bits_cpu_memoria.md`

**Objetivo:** criar base sólida antes da memória em Python: bits, transístor, RAM (condensador/transístor), CPU, ciclo de execução, endereços e barramentos.

---

### `01_tipos_de_memoria_cache_ram_rom_disco.md`

**Objetivo:** perceber, de forma clara, que "memória" não é uma coisa única: cache, RAM, ROM e disco/SSD têm papéis diferentes porque equilibram velocidade, capacidade, custo e persistência.

---

### `02_bits_binario_bytes_enderecos.md`

**Objetivo:** dominar bits, bytes, sistema binário, representação de informação e noções de endereçamento de memória.

> Este ficheiro contém exercícios de consolidação sobre binário.

---

### `03_heap_stack_frames_e_execucao_python.md`

**Objetivo:** compreender a execução de Python no contexto da memória: processo, bytecode, PVM, heap, stack, frames, chamadas de função, retorno, recursão e traceback.

---

### `04_referencias_mutabilidade_gc_em_python.md`

**Objetivo:** perceber como Python gere memória automaticamente: nomes, objetos, referências, alias, mutabilidade, cópias, contagem de referências e garbage collection.

---

### `05_do_python_a_execucao_real_so_cpu_isa_alu.md`

**Objetivo:** fechar o ciclo entre Python e a máquina real: sistema operativo, kernel, loader, processos, threads, chamadas de sistema, CPU, ISA, ALU, famílias de processadores e compatibilidade entre sistemas.

---

### `A1_estruturas_dinamicas_e_complexidade.md`

**Objetivo:** anexo complementar sobre estruturas dinâmicas (pilha, fila, lista ligada, árvore, dicionário) e complexidade (Big-O), usando ideias aprendidas nos módulos principais.

---

## Rota de estudo recomendada

### Rota principal

1. `00_fundamentos_hardware_bits_cpu_memoria.md`
2. `01_tipos_de_memoria_cache_ram_rom_disco.md`
3. `02_bits_binario_bytes_enderecos.md`
4. `03_heap_stack_frames_e_execucao_python.md`
5. `04_referencias_mutabilidade_gc_em_python.md`
6. `05_do_python_a_execucao_real_so_cpu_isa_alu.md`

### Anexo complementar

- `A1_estruturas_dinamicas_e_complexidade.md`

Este anexo pode ser estudado depois do módulo `04`, porque já usa referências, objetos e estruturas que crescem em memória. Também pode ser usado depois do módulo `05`, como extensão final.

---

## Changelog

- **2026-02-04**: Criação inicial da pasta `Memoria` com guia de estudo e 5 módulos.
- **2026-02-04**: Adicionado módulo `00` de fundamentos (hardware, CPU, RAM, endereços).
- **2026-02-04**: Adicionado módulo `06` com a visão completa de execução real (SO, CPU, ISA e ficheiros).
- **2026-05-22**: Reorganizada a pasta numa rota principal (`00` a `05`) e num anexo complementar `A1`; atualizada a narrativa pedagógica do módulo.

![Footer](../Images/Footer.png)
