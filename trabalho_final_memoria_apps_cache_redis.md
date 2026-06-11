![Header](Images/Header.png)

# Trabalho Final - Memória em Aplicações Reais, Cache e Redis

## 1. Enquadramento

Neste trabalho final vais investigar como uma aplicação real pode ser pensada por dentro, usando como base os conceitos estudados no módulo de Memória.

A matéria da pasta `Memoria` serve como ponto de partida: RAM, armazenamento, stack, heap, referências, objetos, estruturas de dados, execução de programas, sistema operativo, CPU e gestão automática de memória em Python.

O objetivo não é copiar informação da Internet nem criar uma aplicação completa. O objetivo é perceber como os dados de uma aplicação real podem ser organizados, usados, guardados, carregados, temporariamente mantidos em memória e otimizados.

O trabalho tem duas partes obrigatórias:

1. Analisar uma aplicação real e explicar como poderia ser organizada se fosse implementada em Python.
2. Investigar o conceito de cache e Redis, explicando como esse conceito ajudaria a aplicação escolhida.

Data de entrega: 30 de junho de 2026.
Data de defesa oral: a definir, entre 1 e 15 de julho de 2026.

---

## 2. Tema Geral

### Pergunta Principal

> Se tivesses de programar uma aplicação real em Python, como organizarias os dados e como pensarias a gestão de memória?

Cada grupo deve escolher uma aplicação conhecida ou um sistema real, por exemplo:

- Instagram
- TikTok
- YouTube
- Spotify
- Netflix
- WhatsApp
- Discord
- Steam
- Google Maps
- Uber
- uma loja online
- uma plataforma de ensino
- uma rede social própria, desde que bem definida

O grupo não vai programar a aplicação. Vai estudar o problema e construir uma explicação técnica, fundamentada e bem organizada.

---

## 3. Parte A - Anatomia Técnica de Uma Aplicação Real

Nesta parte, o grupo deve explicar como a aplicação escolhida poderia ser organizada internamente.

### 3.1 Dados Principais da Aplicação

Identifica os principais tipos de dados usados pela aplicação.

Exemplo para uma rede social:

- utilizadores
- perfis
- publicações
- imagens ou vídeos
- comentários
- gostos
- seguidores
- mensagens
- notificações
- sessões de login

Para cada tipo de dado, deves explicar:

- que informação guarda;
- se muda frequentemente ou raramente;
- se precisa de ser guardado de forma permanente;
- se pode existir temporariamente em memória;
- que problemas podem surgir se existirem muitos dados desse tipo.

### 3.2 Possível Organização em Python

Explica que estruturas de dados poderias usar em Python para representar parte da aplicação.

Exemplos:

- `dict` para aceder rapidamente a utilizadores por `id`;
- `list` para guardar publicações ordenadas por data;
- `set` para guardar gostos ou seguidores sem repetições;
- classes para representar entidades como `User`, `Post` ou `Message`;
- filas para tarefas pendentes, como envio de notificações;
- estruturas aninhadas para representar relações entre dados.

Não basta dizer "usava uma lista" ou "usava um dicionário". Deves justificar a escolha.

Exemplo de justificação:

> Usaria um `dict` para guardar utilizadores por `id`, porque assim consigo procurar diretamente um utilizador sem percorrer todos os utilizadores um a um.

### 3.3 Onde Vivem os Dados?

Relaciona os dados da aplicação com os diferentes tipos de memória e armazenamento.

Deves distinguir:

- dados em RAM;
- dados persistidos numa base de dados;
- ficheiros guardados em disco ou cloud storage;
- dados temporários em cache;
- dados enviados entre cliente e servidor;
- objetos temporários criados durante a execução de uma função.

Exemplo:

> As imagens publicadas pelos utilizadores provavelmente não ficariam guardadas diretamente dentro de um objeto Python em memória durante muito tempo. Ficariam guardadas num sistema de ficheiros ou serviço de armazenamento. Em memória, a aplicação poderia guardar apenas metadados, como o `id`, o autor, a data e o caminho para a imagem.

### 3.4 Três Ações Reais da Aplicação

Escolhe três ações importantes da aplicação e explica o que acontece aos dados.

Exemplos:

- abrir a aplicação;
- fazer login;
- carregar o feed;
- publicar uma imagem;
- fazer like;
- comentar;
- enviar uma mensagem;
- pesquisar conteúdo;
- receber uma notificação;
- ouvir uma música;
- ver um vídeo;
- adicionar um produto ao carrinho.

Para cada ação, explica:

1. que dados são necessários;
2. que dados podem vir da base de dados;
3. que dados podem estar em cache;
4. que objetos temporários podem ser criados em Python;
5. que dados ficam guardados depois da ação terminar;
6. que dados podem ser descartados da memória.

### 3.5 Problemas de Escala

Explica o que pode correr mal quando a aplicação cresce.

Deves abordar pelo menos quatro problemas, por exemplo:

- demasiados utilizadores ao mesmo tempo;
- dados duplicados em memória;
- imagens, vídeos ou ficheiros muito pesados;
- pesquisas lentas;
- feeds lentos;
- excesso de objetos temporários;
- memory leaks;
- cache desatualizada;
- uso excessivo de RAM;
- muitas operações repetidas sobre os mesmos dados;
- necessidade de carregar apenas parte dos dados.

### 3.6 Ligação Obrigatória à Matéria de Memória

O relatório deve ligar explicitamente a análise da aplicação a conceitos estudados.

Deves usar e explicar corretamente pelo menos seis dos seguintes conceitos:

- RAM
- armazenamento secundário
- cache
- stack
- heap
- stack frame
- objeto
- referência
- mutabilidade
- garbage collection
- bytecode
- PVM
- processo
- thread
- sistema operativo
- chamada de sistema
- CPU
- endereço de memória
- estrutura de dados

---

## 4. Parte B - Investigação Obrigatória: Cache e Redis

Nesta parte, todos os grupos investigam o mesmo conceito novo: cache e Redis.

### 4.1 Pergunta de Investigação

> Como é que uma cache em memória, como Redis, pode tornar uma aplicação real mais rápida e que problemas novos pode criar?

### 4.2 O Que Deves Explicar Sobre Cache

O relatório deve explicar:

- o que é uma cache;
- porque uma cache normalmente usa memória rápida;
- que diferença existe entre cache e base de dados principal;
- que dados fazem sentido guardar em cache;
- que dados não devem ficar apenas em cache;
- o que significa guardar dados temporariamente;
- o que é um `cache hit`;
- o que é um `cache miss`;
- o que é TTL, ou seja, tempo de vida de um dado em cache;
- o que significa invalidar uma cache;
- que problemas podem acontecer quando uma cache fica desatualizada.

### 4.3 O Que Deves Explicar Sobre Redis

Investiga Redis como exemplo real de tecnologia usada para cache.

Deves explicar:

- o que é Redis;
- porque é frequentemente descrito como uma base de dados em memória;
- porque pode ser usado como cache;
- que tipos de dados Redis consegue guardar, de forma introdutória;
- porque Redis pode ser mais rápido do que ir sempre a uma base de dados tradicional;
- que vantagens traz;
- que riscos ou desvantagens tem;
- o que acontece se Redis falhar;
- porque dados importantes não devem depender apenas de uma cache sem persistência adequada.

Não é necessário instalar Redis, a menos que o professor autorize ou o grupo tenha condições técnicas para isso.

### 4.4 Aplicação de Redis ao Sistema Escolhido

Cada grupo deve explicar onde usaria cache/Redis na aplicação escolhida.

Exemplos:

#### Instagram ou TikTok

- guardar temporariamente o feed inicial de um utilizador;
- guardar contadores de likes;
- guardar perfis muito consultados;
- guardar sessões de login;
- guardar resultados de pesquisas recentes;
- guardar thumbnails ou metadados de imagens.

#### Spotify

- guardar playlists recentes;
- guardar dados de músicas populares;
- guardar recomendações temporárias;
- guardar estado de sessões;
- guardar resultados de pesquisa.

#### Loja Online

- guardar produtos mais vistos;
- guardar carrinhos temporários;
- guardar stock consultado recentemente;
- guardar resultados de pesquisa;
- guardar sessões de utilizador.

Para cada uso de cache, explica:

1. que dado seria guardado;
2. porque esse dado é bom candidato a cache;
3. durante quanto tempo faria sentido guardá-lo;
4. o que aconteceria se o dado ficasse desatualizado;
5. como a aplicação poderia corrigir ou atualizar esse dado.

### 4.5 Padrão Cache-Aside

Todos os grupos devem explicar, com palavras suas, o padrão `cache-aside`.

Ideia geral:

1. A aplicação procura primeiro o dado na cache.
2. Se o dado existir na cache, usa-o imediatamente.
3. Se o dado não existir na cache, procura-o na base de dados principal.
4. Depois de obter o dado da base de dados, guarda uma cópia na cache.
5. Na próxima vez, a aplicação pode responder mais depressa.

O grupo deve criar um pequeno diagrama que represente este processo.

---

## 5. Entregáveis

Cada grupo deve entregar:

1. Relatório em PDF ou Markdown.
2. Pelo menos dois diagramas originais.
3. Bibliografia/fontes consultadas.
4. Apresentação oral.

### Diagramas Obrigatórios

O relatório deve incluir pelo menos:

- um diagrama dos principais dados da aplicação, ou seja, um diagrama que mostre os tipos de dados, as suas relações e onde vivem (RAM, base de dados, cache, objetos temporários);
- um diagrama que mostre a diferença entre base de dados, cache/Redis e memória temporária do programa.

Opcionalmente, pode incluir:

- diagrama de stack/heap;
- diagrama do fluxo de uma ação;
- diagrama do padrão `cache-aside`;
- diagrama de arquitetura cliente-servidor.

---

## 6. Estrutura Recomendada do Relatório

1. Título e identificação do grupo.
2. Aplicação escolhida e pergunta principal.
3. Descrição geral da aplicação.
4. Dados principais da aplicação.
5. Possível organização dos dados em Python.
6. Onde vivem os dados: RAM, base de dados, disco, cache e objetos temporários.
7. Explicação detalhada de três ações reais.
8. Problemas de escala e memória.
9. Investigação sobre cache.
10. Investigação sobre Redis.
11. Aplicação de Redis ao sistema escolhido.
12. Análise: vantagens, riscos e limites da solução proposta.
13. Conclusão.
14. Fontes consultadas.

---

## 7. Critérios de Avaliação

| Critério                                 |        Cotação |
| ---------------------------------------- | -------------: |
| Escolha e compreensão da aplicação real  |      2 valores |
| Identificação e organização dos dados    |      3 valores |
| Ligação correta à matéria de Memória     |      4 valores |
| Investigação sobre cache e Redis         |      5 valores |
| Aplicação de cache/Redis ao sistema      |      2 valores |
| Diagramas, tabelas e clareza visual      |      2 valores |
| Conclusão, fontes e qualidade da escrita |        1 valor |
| Apresentação oral e defesa individual    |        1 valor |
| **Total**                                | **20 valores** |

---

## 8. Perguntas de Defesa Oral

Durante a apresentação, o professor pode fazer perguntas como:

1. Porque é que escolheste essa estrutura de dados em Python?
2. Que dados da tua aplicação não devem ficar apenas em cache?
3. O que acontece se a cache tiver dados antigos?
4. Qual é a diferença entre RAM, cache e base de dados?
5. Onde aparecem objetos temporários no sistema que analisaste?
6. O que é um `cache hit`?
7. O que é um `cache miss`?
8. Porque é que Redis pode tornar uma aplicação mais rápida?
9. O que pode correr mal se Redis falhar?
10. Que parte da matéria de Memória foi mais importante para o teu trabalho?

---

## 9. Regras Importantes

- O trabalho deve ser escrito com palavras do grupo.
- Todas as fontes externas devem ser indicadas.
- Não basta copiar definições: é obrigatório aplicar os conceitos à aplicação escolhida.
- Cada aluno pode ser questionado individualmente sobre qualquer parte do trabalho.
- O uso de inteligência artificial só é permitido se for autorizado pelo professor e devidamente declarado.

---

## 10. Objetivo Final

No final deste trabalho, deves conseguir explicar como uma aplicação real pode usar memória, armazenamento, estruturas de dados, objetos, referências e cache para funcionar de forma eficiente.

Mais importante: deves conseguir perceber que programar uma aplicação real não é apenas escrever funções. Também é decidir onde vivem os dados, durante quanto tempo vivem, como são encontrados rapidamente e o que acontece quando existem milhares ou milhões de utilizadores.

![Footer](Images/Footer.png)
