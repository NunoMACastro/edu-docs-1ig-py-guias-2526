# Quiz intermédio 04 - Revisão geral: memória e execução de programas

## 1. Explica como um computador representa informação usando bits. Na tua resposta, inclui a ideia de dois estados físicos, transístores, portas lógicas, bits, bytes e exemplos de representação de números, texto e imagens.

**Consulta:** `Memoria/00_fundamentos_hardware_bits_cpu_memoria.md`, capítulos 2, 3, 4, 5 e 6; `Memoria/02_bits_binario_bytes_enderecos.md`, capítulos 2, 3 e 6.

## 2. Compara memória cache, RAM, ROM e armazenamento secundário (SSD/HDD). Na tua resposta, explica para que serve cada uma, se é volátil ou não volátil, e como se relacionam com velocidade, capacidade e execução de programas.

**Consulta:** `Memoria/01_tipos_de_memoria_cache_ram_rom_disco.md`, capítulos 1 a 12; `Memoria/00_fundamentos_hardware_bits_cpu_memoria.md`, capítulos 7, 8 e 11; `Memoria/02_bits_binario_bytes_enderecos.md`, capítulo 1.

## 3. Converte `45` de decimal para binário e converte `101101` de binário para decimal. Depois explica o que é um endereço de memória e porque é que dados e instruções podem ambos ser representados em binário.

**Consulta:** `Memoria/02_bits_binario_bytes_enderecos.md`, capítulos 3, 4, 5 e 7; `Memoria/00_fundamentos_hardware_bits_cpu_memoria.md`, capítulos 5, 6 e 10.

## 4. Descreve o percurso de execução de um programa Python desde o ficheiro `.py` até à execução real no computador.

**Consulta:** `Memoria/03_heap_stack_frames_e_execucao_python.md`, capítulos 2, 3, 4, 5, 6, 7 e 8; `Memoria/05_do_python_a_execucao_real_so_cpu_isa_alu.md`, capítulos 1, 2, 3 e 4.

## 5. Explica a diferença entre stack, heap e stack frames num programa Python. Na tua resposta, refere o processo, o espaço de memória do programa, o que acontece quando uma função é chamada e o que pode acontecer aos objetos quando a função termina.

**Consulta:** `Memoria/03_heap_stack_frames_e_execucao_python.md`, capítulos 1, 9, 10, 12, 13 e 14; `Memoria/04_referencias_mutabilidade_gc_em_python.md`, capítulos 1, 2 e 3.

## 6. Analisa o seguinte código e explica o resultado esperado.

```python
a = [1, [2, 3]]
b = a
c = a.copy()

b.append(4)
c[1].append(5)

print(a)
print(b)
print(c)
```

**Consulta:** `Memoria/04_referencias_mutabilidade_gc_em_python.md`, capítulos 2, 3, 4 e 5; `Memoria/03_heap_stack_frames_e_execucao_python.md`, capítulo 9.7.

## 7. Explica como Python gere memória automaticamente usando o Garbage Collector.

**Consulta:** `Memoria/04_referencias_mutabilidade_gc_em_python.md`, capítulos 1, 6, 7, 8, 9 e 10; `Memoria/03_heap_stack_frames_e_execucao_python.md`, capítulo 14.

## 8. Explica o que acontece quando um programa é aberto e começa a executar no computador. Na tua resposta, inclui o papel do sistema operativo, kernel, loader, processo, thread, modo utilizador, modo kernel, chamadas de sistema, código de máquina, ISA e ciclo `fetch -> decode -> execute`.

**Consulta:** `Memoria/05_do_python_a_execucao_real_so_cpu_isa_alu.md`, capítulos 1 a 11; `Memoria/00_fundamentos_hardware_bits_cpu_memoria.md`, capítulos 8, 9, 10 e 11.
