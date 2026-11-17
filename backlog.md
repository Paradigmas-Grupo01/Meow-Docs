# Product Backlog e Histórias de Usuário: Meowdoku

**Projeto:** Meowdoku (Paradigmas de Programação, UnB/FGA, 2026/2)  
**Última atualização:** 14/11/2026  
**Classificação de escopo pretendida:** Remix Original (bonus +0,5)

---

## Legenda de Prioridade (MoSCoW)

- **Must** — sem isso, o projeto não funciona ou reprova.
- **Should** — necessário para atingir a nota almejada e o bonus de originalidade.
- **Could** — agrega valor perceptível, mas pode ser cortado sem prejuízo fatal.
- **Won't (por enquanto)** — ideia registrada para o futuro; não entra nesta entrega.

---

## Épicos

| ID | Épico | Descrição resumida |
| :--- | :--- | :--- |
| E1 | Motor Lógico Prolog | Modelagem CSP com CLP(FD), solver, gerador de puzzles e sistema de dicas |
| E2 | Integração Python/FastAPI | Ponte Janus entre Prolog e a API HTTP, rotas REST documentadas |
| E3 | Frontend Elm (Domínio) | Tipos puros, validação local de conflitos, ciclo de marcação |
| E4 | Frontend Elm (TEA / Main) | Ciclo completo The Elm Architecture: init, update, view, subscriptions |
| E5 | UI/UX e Estilização | Layout CSS, paleta de cores, sprites, responsividade, acessibilidade |
| E6 | Funcionalidades Originais | Smart Feline Hint, Modo Dois Gatinhos, Caixa de Papelão |
| E7 | QA, Testes e Validação | plunit, elm-test, pytest, validar_entrega.py, formatação de código |
| E8 | Documentação e Relatório | RELATORIO.md (13 seções), avaliacao-360, atas de reunião |

---

## Histórias de Usuário

### E1 — Motor Lógico Prolog

**US-01: Resolver um tabuleiro Meowdoku**  
Como jogador, quero que o sistema consiga resolver qualquer tabuleiro válido, para que eu possa verificar minha solução ou receber a resposta correta.

Critérios de aceite:
- O predicado `solve/3` recebe tamanho N, mapa de regiões e estado parcial, e retorna a solução completa.
- A solução respeita as 4 restrições do jogo (linha, coluna, região, não-adjacência).
- Tabuleiros 6x6 resolvem em menos de 2 segundos.
- Tabuleiros 8x8 resolvem em menos de 10 segundos.

Prioridade: **Must**  
Responsável: Membro 1  
Issue: #1

---

**US-02: Verificar se uma solução é válida**  
Como jogador, quero que o sistema valide minha solução ao finalizar o tabuleiro, para que eu saiba se acertei.

Critérios de aceite:
- O predicado `valid_solution/3` retorna `true` se todas as restrições são satisfeitas.
- Retorna `false` com indicação de qual restrição foi violada (linha, coluna, região ou adjacência).

Prioridade: **Must**  
Responsável: Membro 1  
Issue: #1

---

**US-03: Gerar tabuleiros com solução única**  
Como jogador, quero que o jogo gere novos puzzles aleatórios, para que eu não jogue sempre os mesmos.

Critérios de aceite:
- O predicado `generate/4` produz um tabuleiro com regiões conexas e solução única verificada.
- Aceita parâmetro de tamanho (6, 8 ou 10).
- As regiões geradas são contíguas (4-conectadas).

Prioridade: **Should**  
Responsável: Membro 2  
Issue: #2

---

**US-04: Receber uma dica com justificativa lógica (Smart Feline Hint)**  
Como jogador, quero receber uma dica que me explique o raciocínio dedutivo usado, para que eu aprenda a resolver sozinho.

Critérios de aceite:
- O predicado `hint/4` identifica a próxima célula mais determinada pelo solver.
- Retorna texto em português explicando por que aquela célula deve (ou não) ter um gato.
- A explicação referencia a restrição específica usada na dedução (ex: "Linha 3 já atingiu o limite de gatos").

Prioridade: **Should**  
Responsável: Membro 2  
Issue: #2

---

**US-05: Resolver tabuleiros no modo Dois Gatinhos (K=2)**  
Como jogador avançado, quero que o solver funcione com K=2 gatos por unidade, para que eu possa jogar o modo difícil.

Critérios de aceite:
- O solver aceita o parâmetro `CatsPerUnit` e funciona corretamente com K=2.
- As restrições de não-adjacência continuam valendo entre todos os pares de gatos.
- Tabuleiros 8x8 com K=2 resolvem em menos de 30 segundos.

Prioridade: **Should**  
Responsável: Membro 1 e Membro 2  
Issue: #1, #2

---

**US-06: Suportar obstáculos de Caixa de Papelão**  
Como jogador, quero que alguns tabuleiros tenham células bloqueadas onde gatos não podem ficar, para que os puzzles sejam mais variados.

Critérios de aceite:
- O solver aceita uma lista de coordenadas bloqueadas e as trata como restrição adicional (valor fixo 0).
- Puzzles com obstáculos mantêm solução única.

Prioridade: **Could**  
Responsável: Membro 2  
Issue: #2

---

### E2 — Integração Python/FastAPI

**US-07: Buscar um puzzle de exemplo via API**  
Como frontend, quero chamar `GET /api/meowdoku/example` e receber um puzzle pronto para jogar, para que o jogo inicie sem configuração manual.

Critérios de aceite:
- A rota retorna JSON com campos `size`, `regions` (matriz NxN) e `initial` (estado vazio ou parcial).
- Aceita query parameter `size` (6, 8 ou 10).
- Tempo de resposta abaixo de 3 segundos.

Prioridade: **Must**  
Responsável: Membro 3  
Issue: #3

---

**US-08: Solicitar solução via API**  
Como frontend, quero chamar `POST /api/meowdoku/solve` enviando o estado atual e receber a solução completa.

Critérios de aceite:
- O corpo da requisição contém `size`, `regions` e `board`.
- A resposta contém `solution` (matriz NxN) e `solvable` (booleano).
- Se o tabuleiro não tem solução, retorna `solvable: false` com mensagem descritiva.

Prioridade: **Must**  
Responsável: Membro 3  
Issue: #3

---

**US-09: Solicitar dica via API**  
Como frontend, quero chamar `POST /api/meowdoku/hint` e receber a sugestão com explicação textual.

Critérios de aceite:
- A resposta contém `row`, `col`, `value` e `explanation` (string em português).
- Se o tabuleiro já está completo ou inconsistente, retorna erro HTTP 400 com mensagem clara.

Prioridade: **Should**  
Responsável: Membro 3  
Issue: #3

---

**US-10: Manter Python abaixo de 20% do código**  
Como equipe, precisamos garantir que Python represente menos de 20% das linhas de código do projeto, conforme exigência da disciplina.

Critérios de aceite:
- O script `metricas.py` confirma que a proporção de Python está abaixo do limite.
- Toda lógica de negócio fica em Prolog; Python só faz a ponte HTTP.

Prioridade: **Must**  
Responsável: Membro 3  
Issue: #3

---

### E3 — Frontend Elm (Domínio)

**US-11: Representar o estado do tabuleiro em tipos Elm**  
Como desenvolvedor, quero uma modelagem tipada e imutável do tabuleiro no Elm, para que bugs de estado sejam pegos em tempo de compilação.

Critérios de aceite:
- Tipo `CellMark` com variantes `Empty`, `Blocked`, `Cat`.
- Tipo `Cell` com campos `mark`, `regionId`, `hasConflict`.
- Tipo `Board` como `Array (Array Cell)`.
- Módulo compila sem warnings.

Prioridade: **Must**  
Responsável: Membro 4  
Issue: #4

---

**US-12: Ciclar marcação de uma célula**  
Como jogador, quero clicar numa célula e ver a marcação mudar de Vazio para X, de X para Gato, de Gato para Vazio.

Critérios de aceite:
- A função `cycleMark` implementa a transição circular corretamente.
- Células bloqueadas (obstáculo) não são alteráveis.

Prioridade: **Must**  
Responsável: Membro 4  
Issue: #4

---

**US-13: Validar conflitos localmente no Elm**  
Como jogador, quero ver imediatamente quais células estão em conflito (sem esperar o servidor), para ter feedback instantâneo.

Critérios de aceite:
- A função `checkConflicts` percorre o tabuleiro e marca `hasConflict = True` em células que violam qualquer restrição.
- A verificação roda em tempo puro (sem Cmd) e é chamada a cada alteração de estado.
- Conflitos verificados: excesso de gatos na linha, coluna ou região, e adjacência proibida.

Prioridade: **Must**  
Responsável: Membro 4  
Issue: #4

---

**US-14: Detectar vitória**  
Como jogador, quero que o jogo reconheça automaticamente quando resolvi o puzzle corretamente.

Critérios de aceite:
- A função `isSolved` retorna `True` quando todas as restrições estão satisfeitas e o número correto de gatos foi posicionado.
- A detecção é feita localmente no Elm, sem chamada à API.

Prioridade: **Must**  
Responsável: Membro 4  
Issue: #4

---

### E4 — Frontend Elm (TEA / Main)

**US-15: Carregar um puzzle ao abrir o jogo**  
Como jogador, quero que ao acessar o jogo um tabuleiro já apareça carregado, sem que eu precise fazer nada.

Critérios de aceite:
- O `init` dispara um `Cmd` que busca o puzzle via `fetchMeowdokuExample`.
- Enquanto carrega, exibe indicação de "Carregando..." (sem animação sofisticada, basta texto).
- Se falhar, exibe mensagem de erro legível.

Prioridade: **Must**  
Responsável: Membro 5  
Issue: #5

---

**US-16: Tratar interações do jogador no update**  
Como jogador, quero que meus cliques e teclas sejam processados corretamente para alterar o tabuleiro.

Critérios de aceite:
- Mensagem `CellClicked row col` aciona `cycleMark` e depois `checkConflicts`.
- Mensagem `HintRequested` dispara chamada à API de dica.
- Mensagem `SolveRequested` dispara chamada à API de solução.
- Mensagem `NewGameRequested` busca novo puzzle.

Prioridade: **Must**  
Responsável: Membro 5  
Issue: #5

---

**US-17: Decodificar e tratar respostas da API**  
Como desenvolvedor, quero que os decoders JSON do Elm traduzam corretamente as respostas do backend.

Critérios de aceite:
- `meowdokuPuzzleDecoder` mapeia o JSON de `/api/meowdoku/example` para o modelo Elm.
- `meowdokuHintDecoder` mapeia o JSON de `/api/meowdoku/hint` para o tipo `MeowdokuHint`.
- Erros de decodificação são tratados com mensagem amigável na tela.

Prioridade: **Must**  
Responsável: Membro 5  
Issue: #5

---

**US-18: Atalhos de teclado**  
Como jogador, quero usar teclas do teclado para marcar células mais rapidamente.

Critérios de aceite:
- Tecla `X` marca a célula selecionada como bloqueada (X).
- Tecla `G` marca como gato.
- Tecla `Delete` ou `Backspace` limpa a célula.
- Funciona com a célula que está sob o cursor ou a última célula clicada.

Prioridade: **Could**  
Responsável: Membro 5  
Issue: #5

---

### E5 — UI/UX e Estilização

**US-19: Renderizar o tabuleiro com cores por região**  
Como jogador, quero que cada região do tabuleiro tenha uma cor distinta, para que eu consiga identificar visualmente os territórios.

Critérios de aceite:
- Paleta de no mínimo 10 cores pastel mapeadas por `regionId`.
- As cores têm contraste suficiente entre regiões adjacentes.
- O tabuleiro é renderizado com CSS Grid.

Prioridade: **Must**  
Responsável: Membro 6  
Issue: #6

---

**US-20: Exibir gatos e marcações nas células**  
Como jogador, quero ver representações visuais claras de gatos e marcações X nas células.

Critérios de aceite:
- Gatos são representados por ícone SVG ou caractere Unicode reconhecível.
- Marcação X aparece em cinza semitransparente.
- Células vazias ficam limpas, sem ruído visual.

Prioridade: **Must**  
Responsável: Membro 6  
Issue: #6

---

**US-21: Destacar conflitos visualmente**  
Como jogador, quero que células com conflito fiquem destacadas em vermelho, para que eu identifique erros imediatamente.

Critérios de aceite:
- Células com `hasConflict = True` recebem borda ou fundo vermelho.
- O destaque desaparece assim que o conflito é corrigido.
- Animação de transição suave (CSS transition de ~200ms).

Prioridade: **Must**  
Responsável: Membro 6  
Issue: #6

---

**US-22: Exibir contador de gatos**  
Como jogador, quero ver quantos gatos já coloquei e quantos faltam, para acompanhar meu progresso.

Critérios de aceite:
- Exibe "Gatos colocados: X / N" em posição visível.
- Atualiza instantaneamente a cada marcação.

Prioridade: **Should**  
Responsável: Membro 6  
Issue: #6

---

**US-23: Modal de vitória**  
Como jogador, quero ver uma tela de parabéns quando resolver o puzzle, para ter satisfação ao completar o desafio.

Critérios de aceite:
- Aparece um overlay ou modal ao detectar `isSolved = True`.
- Mostra tempo de resolução e botão "Novo Jogo".
- Pode ser fechado clicando fora ou no botão.

Prioridade: **Should**  
Responsável: Membro 6  
Issue: #6

---

**US-24: Exibir a dica na interface**  
Como jogador, quero ver a explicação da dica em um painel ao lado do tabuleiro, para entender o raciocínio.

Critérios de aceite:
- Ao receber a dica da API, destaca a célula sugerida no tabuleiro.
- Exibe o texto da explicação em um painel lateral ou abaixo do tabuleiro.
- O destaque da dica desaparece após o jogador interagir com outra célula.

Prioridade: **Should**  
Responsável: Membro 6  
Issue: #6

---

**US-25: Seletor de modo de jogo**  
Como jogador, quero escolher entre modo clássico (K=1) e modo Dois Gatinhos (K=2), para variar a dificuldade.

Critérios de aceite:
- Dropdown ou botões de seleção na tela inicial ou acima do tabuleiro.
- Ao trocar de modo, busca novo puzzle com o parâmetro correspondente.

Prioridade: **Should**  
Responsável: Membro 6  
Issue: #6

---

### E6 — Funcionalidades Originais

As histórias de originalidade já foram incluídas nos épicos correspondentes (US-04, US-05, US-06, US-24, US-25). Este épico serve como agrupamento lógico para rastreamento:

| Funcionalidade | Histórias relacionadas | Status |
| :--- | :--- | :--- |
| Smart Feline Hint | US-04, US-09, US-24 | Esqueleto pronto no backend |
| Modo Dois Gatinhos | US-05, US-25 | Solver parametrizado; falta UI |
| Caixa de Papelão | US-06 | Planejado, não iniciado |

---

### E7 — QA, Testes e Validação

**US-26: Suite de testes Prolog (plunit)**  
Como equipe, precisamos de testes automatizados para o motor Prolog, para garantir que o solver não regride.

Critérios de aceite:
- Mínimo de 10 testes cobrindo: solver básico 6x6, solver 8x8, validação de solução, contagem de gatos por linha/coluna/região, restrição de adjacência, hint, e caso sem solução.
- Todos passam com `swipl -g run_tests -t halt`.
- Zero warnings do compilador Prolog.

Prioridade: **Must**  
Responsável: Membro 7 (com apoio dos Membros 1 e 2)  
Issue: #7

---

**US-27: Testes de API (pytest)**  
Como equipe, precisamos de testes para as rotas FastAPI, para garantir que a integração Python-Prolog funciona.

Critérios de aceite:
- Testes para as 3 rotas (`/example`, `/solve`, `/hint`).
- Testa cenários de sucesso e erro (body inválido, puzzle sem solução).
- Cobertura mínima de 80% no módulo `meowdoku_prolog.py`.

Prioridade: **Should**  
Responsável: Membro 7 (com apoio do Membro 3)  
Issue: #7

---

**US-28: Validação formal com validar_entrega.py**  
Como equipe, precisamos que o validador oficial do professor passe com zero erros, pois isso é critério de aprovação.

Critérios de aceite:
- `uv run scripts/validar_entrega.py RELATORIO.md` executa sem erros.
- Todas as seções obrigatórias do relatório estão preenchidas.
- Arquivos de avaliação 360 existem para todos os 7 membros.

Prioridade: **Must**  
Responsável: Membro 7  
Issue: #7

---

**US-29: Formatação e qualidade de código**  
Como equipe, queremos código limpo e padronizado, para facilitar a leitura e avaliação do professor.

Critérios de aceite:
- Código Elm formatado com `elm-format --yes`.
- Código Python formatado com `black` ou `ruff format`.
- Código Prolog sem warnings de variáveis singleton.
- Sem arquivos desnecessários commitados (node_modules, __pycache__, etc).

Prioridade: **Should**  
Responsável: Membro 7  
Issue: #7

---

### E8 — Documentação e Relatório

**US-30: Preencher o RELATORIO.md completo**  
Como equipe, precisamos entregar o relatório com as 13 seções preenchidas corretamente.

Critérios de aceite:
- Seção 1: Apresentação com classificação "Remix Original" e justificativa.
- Seção 2: Descrição do jogo original (Star Battle/Queens) e adaptação Meowdoku.
- Seção 3: Prints da interface funcionando.
- Seção 4: Diagrama de arquitetura (Elm TEA + FastAPI + Prolog).
- Seção 5: Protocolo de comunicação HTTP documentado.
- Seção 6: Exemplos reais de código Prolog com CLP(FD).
- Seção 7: Como o Prolog resolve o CSP passo a passo.
- Seção 8: Exemplos reais de código Elm com The Elm Architecture.
- Seção 9: Integração frontend/backend detalhada.
- Seção 10: Tabela de contribuição por membro (com links para commits).
- Seção 11: Declaração honesta de uso de IA.
- Seção 12: Instruções completas de build e execução.
- Seção 13: Reflexão sobre os paradigmas aprendidos.

Prioridade: **Must**  
Responsável: Membro 7 (cada membro contribui com sua seção)  
Issue: #7

---

**US-31: Avaliação 360 individual**  
Como integrante do grupo, preciso preencher minha avaliação 360 sobre todos os colegas.

Critérios de aceite:
- Cada membro cria `avaliacao-360/<matricula>.md` seguindo o template.
- Todas as 7 avaliações estão presentes no repositório antes do prazo.

Prioridade: **Must**  
Responsável: Todos  
Issue: #7

---

## Mapeamento: Histórias por Membro e Issue (Prazo: 18/11/2026 às 22:00)

| Membro | Issues GitHub | Histórias de Usuário |
| :--- | :--- | :--- |
| Membro 1 (Engenheiro de Restrições Prolog) | [#1](https://github.com/Paradigmas-Grupo01/meow-Game/issues/1) (1/2: CSP base)<br>[#8](https://github.com/Paradigmas-Grupo01/meow-Game/issues/8) (2/2: K=2 e plunit) | US-01, US-02, US-05 |
| Membro 2 (Algoritmo de Dicas e Geração) | [#2](https://github.com/Paradigmas-Grupo01/meow-Game/issues/2) (1/2: Smart Hint)<br>[#9](https://github.com/Paradigmas-Grupo01/meow-Game/issues/9) (2/2: Geração e unicidade) | US-03, US-04, US-05, US-06 |
| Membro 3 (Arquiteto de Integração Python) | [#3](https://github.com/Paradigmas-Grupo01/meow-Game/issues/3) (1/2: Janus e rotas base)<br>[#10](https://github.com/Paradigmas-Grupo01/meow-Game/issues/10) (2/2: Hints, Pydantic, pytest) | US-07, US-08, US-09, US-10 |
| Membro 4 (Engenheiro de Domínio Elm) | [#4](https://github.com/Paradigmas-Grupo01/meow-Game/issues/4) (1/2: Tipos imutáveis)<br>[#11](https://github.com/Paradigmas-Grupo01/meow-Game/issues/11) (2/2: Conflitos e vitória) | US-11, US-12, US-13, US-14 |
| Membro 5 (Engenheiro de API e HTTP Elm) | [#5](https://github.com/Paradigmas-Grupo01/meow-Game/issues/5) (1/2: Decoders JSON)<br>[#12](https://github.com/Paradigmas-Grupo01/meow-Game/issues/12) (2/2: Ciclo TEA Update) | US-15, US-16, US-17, US-18 |
| Membro 6 (Designer de UI/UX) | [#6](https://github.com/Paradigmas-Grupo01/meow-Game/issues/6) (1/2: CSS Grid e cores)<br>[#13](https://github.com/Paradigmas-Grupo01/meow-Game/issues/13) (2/2: Conflitos, modal, contador) | US-19, US-20, US-21, US-22, US-23, US-24, US-25 |
| Membro 7 (QA, Validação e Relatório) | [#7](https://github.com/Paradigmas-Grupo01/meow-Game/issues/7) (1/2: Validador formal e lint)<br>[#14](https://github.com/Paradigmas-Grupo01/meow-Game/issues/14) (2/2: 13 seções do RELATORIO) | US-26, US-27, US-28, US-29, US-30, US-31 |

---

## Ordem de Execução Sugerida (Dependências)

```
US-01 (solver)
  |
  +---> US-02 (validação) ---+
  |                          |
  +---> US-03 (geração)      |
  |                          v
  +---> US-04 (hint) ----> US-07, US-08, US-09 (rotas API)
                              |
             +----------------+----------------+
             |                                 |
             v                                 v
     US-11, US-12, US-13, US-14         US-15, US-16, US-17
     (domínio Elm puro)                (TEA, HTTP, update)
             |                                 |
             +----------------+----------------+
                              |
                              v
                   US-19 a US-25 (UI/UX)
                              |
                              v
              US-05, US-06 (modos avançados)
                              |
                              v
              US-26 a US-31 (QA, relatório)
```

Leitura: as setas indicam dependência. O solver (US-01) é a fundação de tudo. A UI depende do domínio Elm e das rotas. Modos avançados podem ser adicionados quando o fluxo básico funcionar de ponta a ponta.

---

## Status Atual do Backlog

| ID | Título resumido | Status |
| :--- | :--- | :--- |
| US-01 | Solver Prolog | Esqueleto pronto, falta testar com SWI instalado |
| US-02 | Validação de solução | Esqueleto pronto |
| US-03 | Geração de puzzles | Predicado declarado, implementação pendente |
| US-04 | Smart Feline Hint | Esqueleto pronto, falta refinar explicações |
| US-05 | Modo K=2 | Solver parametrizado, falta testar |
| US-06 | Caixa de Papelão | Planejado |
| US-07 | GET /example | Rota implementada |
| US-08 | POST /solve | Rota implementada |
| US-09 | POST /hint | Rota implementada |
| US-10 | Limite 20% Python | Sob controle (verificar com metricas.py) |
| US-11 | Tipos Elm | Módulo implementado |
| US-12 | Ciclo de marcação | Função implementada |
| US-13 | Validação de conflitos Elm | Função implementada |
| US-14 | Detecção de vitória | Função implementada |
| US-15 | Init com fetch | Pendente (Main.elm ainda do Sudoku) |
| US-16 | Update do jogador | Pendente |
| US-17 | Decoders JSON | Implementados em Api.elm |
| US-18 | Atalhos de teclado | Pendente |
| US-19 | Cores por região | Pendente |
| US-20 | Sprites de gato | Pendente |
| US-21 | Destaque de conflitos | Pendente |
| US-22 | Contador de gatos | Pendente |
| US-23 | Modal de vitória | Pendente |
| US-24 | Painel de dica | Pendente |
| US-25 | Seletor de modo | Pendente |
| US-26 | Testes plunit | Esqueleto pronto, falta rodar |
| US-27 | Testes pytest | Pendente |
| US-28 | validar_entrega.py | Pendente |
| US-29 | Formatação de código | Pendente |
| US-30 | RELATORIO.md | Template presente, conteudo pendente |
| US-31 | Avaliação 360 | Template presente, preenchimento individual pendente |

---

## Histórico de Versões

<p className="tabela-titulo">Tabela 5: Histórico de versões</p>

| Versão | Data | Descrição | Autor(es) | Revisor(es) |
| :---: | :---: | :--- | :--- | :--- |
| `1.0` | 14/11/2026 | Elaboração inicial do backlog do produto e 31 histórias de usuário | [Gabriel Monteiro](https://github.com/GabrielSMonteiro) | |
| `1.1` | 16/11/2026 | Desdobramento das tarefas em 2 issues por integrante (total 14) com prazo para 18/11 às 22h | [Gabriel Monteiro](https://github.com/GabrielSMonteiro) | |

<p className="tabela-fonte">Fonte: [Gabriel Monteiro](https://github.com/GabrielSMonteiro), 2026.</p>

