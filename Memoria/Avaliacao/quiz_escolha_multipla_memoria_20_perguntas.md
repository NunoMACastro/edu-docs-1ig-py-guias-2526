![Header](../../Images/Header.png)

# Quiz de escolha múltipla - Memória e execução de programas

## Matéria incluída

- `00_fundamentos_hardware_bits_cpu_memoria.md` - tudo
- `01_tipos_de_memoria_cache_ram_rom_disco.md` - tudo
- `02_bits_binario_bytes_enderecos.md` - tudo
- `03_heap_stack_frames_e_execucao_python.md` - tudo menos os capítulos 11, 15 e 16
- `04_referencias_mutabilidade_gc_em_python.md` - tudo
- `05_do_python_a_execucao_real_so_cpu_isa_alu.md` - até ao capítulo 11 incluído

---

## Perguntas

1. Porque é que os computadores usam bits para representar informação?
    - A) Porque os computadores só conseguem guardar letras.
    - B) Porque é simples representar dois estados físicos, como ligado/desligado.
    - C) Porque o sistema decimal ocupa sempre menos memória.
    - D) Porque a RAM só consegue guardar números positivos.

2. Qual é o papel principal de um transístor num computador?
    - A) Funcionar como um pequeno interruptor eletrónico.
    - B) Guardar ficheiros permanentemente no disco.
    - C) Converter automaticamente Python em código de máquina.
    - D) Mostrar imagens no ecrã.

3. Um byte corresponde a:
    - A) 2 bits.
    - B) 4 bits.
    - C) 8 bits.
    - D) 16 bits.

4. Qual é a representação binária correta do número decimal `22`?
    - A) `10110`
    - B) `11010`
    - C) `10011`
    - D) `11100`

5. Qual é o valor decimal do número binário `101101`?
    - A) 37
    - B) 41
    - C) 45
    - D) 53

6. O que representa um endereço de memória?
    - A) O nome de uma variável escrito no código.
    - B) A localização onde um dado ou instrução está guardado na memória.
    - C) O tipo de um objeto em Python.
    - D) A velocidade máxima da CPU.

7. Qual é a principal função da memória cache?
    - A) Guardar ficheiros do utilizador de forma permanente.
    - B) Guardar dados e instruções usados frequentemente perto da CPU.
    - C) Substituir a ROM durante o arranque.
    - D) Aumentar o tamanho do disco.

8. Qual das opções descreve corretamente a RAM?
    - A) É volátil e funciona como memória de trabalho do computador.
    - B) É não volátil e serve apenas para guardar firmware.
    - C) É mais lenta do que o disco e usada só para backups.
    - D) É uma memória apenas de leitura.

9. Qual é a afirmação correta sobre ROM?
    - A) É onde ficam normalmente os documentos do utilizador.
    - B) É usada sobretudo para guardar informação essencial de arranque/firmware.
    - C) É apagada sempre que o computador é desligado.
    - D) É a zona onde vivem os objetos Python criados em tempo de execução.

10. Qual é a sequência básica do ciclo de execução da CPU?
    - A) Decode -> Fetch -> Execute
    - B) Execute -> Decode -> Fetch
    - C) Fetch -> Decode -> Execute
    - D) Fetch -> Execute -> Decode

11. Numa leitura de memória, qual é a função geral dos barramentos?
    - A) Transportar dados, endereços e sinais de controlo entre a CPU e a memória.
    - B) Guardar permanentemente os dados do utilizador.
    - C) Converter código Python em código de máquina.
    - D) Mostrar o conteúdo da memória no monitor.

12. Qual das opções descreve melhor o percurso de execução de um programa Python?
    - A) Código `.py` -> código de máquina direto -> CPU executa o `.py`.
    - B) Código `.py` -> bytecode Python -> PVM/interpretador -> CPU executa o interpretador.
    - C) Código `.py` -> ROM -> cache -> monitor.
    - D) Código `.py` -> ISA -> ISA converte para Python.

13. O bytecode Python é:
    - A) Código de máquina executado diretamente pela CPU.
    - B) Um formato intermédio entendido pela Python Virtual Machine.
    - C) Um ficheiro de imagem temporário.
    - D) Uma cópia do código-fonte com comentários removidos.

14. Em termos gerais, a stack de execução guarda sobretudo:
    - A) Frames de chamadas de função.
    - B) Ficheiros permanentes do utilizador.
    - C) Firmware de arranque.
    - D) Apenas imagens e vídeos.

15. Em Python, objetos como listas e dicionários vivem normalmente:
    - A) Na ROM.
    - B) Na heap.
    - C) No teclado.
    - D) No barramento de controlo.

16. Quando uma função Python é chamada, o que acontece normalmente?
    - A) É criada uma nova stack frame para essa chamada.
    - B) Todos os objetos da heap são apagados.
    - C) O ficheiro `.py` é guardado na ROM.
    - D) A CPU deixa de executar instruções.

17. Observa o código:

    ```python
    a = [1, 2]
    b = a
    b.append(3)
    print(a)
    ```

    Qual é o resultado esperado?
    - A) `[1, 2]`
    - B) `[1, 2, 3]`
    - C) `[3]`
    - D) Erro, porque listas são imutáveis.

18. Em Python, um objeto órfão é um objeto que:
    - A) Tem referências mas não é acessível.
    - B) Não tem referências e pode ser libertado pelo Garbage Collector.
    - C) É guardado na ROM.
    - D) É um tipo especial de variável global.

19. Qual é a afirmação correta sobre contagem de referências e Garbage Collection em Python?
    - A) Objetos sem referências podem ser libertados; ciclos inacessíveis podem precisar do Garbage Collector.
    - B) Python nunca liberta objetos automaticamente.
    - C) O Garbage Collector converte listas em tuplos para poupar memória.
    - D) A contagem de referências só aumenta quando o computador é reiniciado.

20. Qual é a afirmação correta sobre ISA, sistema operativo e CPU?
    - A) A ISA é um programa que converte Python em instruções da CPU.
    - B) O sistema operativo inventa todas as instruções da CPU em tempo real.
    - C) A ISA define regras/instruções que a CPU implementa; a CPU executa instruções de máquina.
    - D) O kernel corre fora da CPU e não é software.

---

## Chave de respostas

1. B
2. A
3. C
4. A
5. C
6. B
7. B
8. A
9. B
10. C
11. A
12. B
13. B
14. A
15. B
16. A
17. B
18. B
19. A
20. C

![Footer](../../Images/Footer.png)
