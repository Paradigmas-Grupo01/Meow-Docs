# Registro de Atas de Reuniões: Meowdoku

Este documento serve como histórico auditável do alinhamento do grupo. As atas auxiliam na prestação de contas da Seção 10 do relatório final e na distribuição da avaliação 360 graus.

---

## Template de Ata

### Reunião [Número] - [Data]
- **Horário:** [Início] às [Término]
- **Local:** [Presencial FGA / Discord / Google Meet]
- **Presentes:** [Lista de nomes dos integrantes presentes]
- **Ausentes com justificativa:** [Nomes e motivos]
- **Pauta da Reunião:**
  1. Ponto 1
  2. Ponto 2
- **Discussões e Decisões Tomadas:**
  - Decisão 1
  - Decisão 2
- **Tarefas Atribuídas para o Próximo Ciclo:**
  - [Nome do Integrante]: Tarefa X (Prazo: DD/MM)
  - [Nome do Integrante]: Tarefa Y (Prazo: DD/MM)

---

## Ata 01 - Alinhamento Inicial e Definição do Escopo (14/11/2026)
- **Horário:** 05:00 às 05:30
- **Local:** Discord
- **Presentes:** Gabriel
- **Pauta da Reunião:**
  1. Escolha do tema do projeto final de Paradigmas de Programação.
  2. Definição da arquitetura e das linguagens cobradas (SWI-Prolog, Elm e FastAPI/Janus).
  3. Divisão inicial de papéis para 7 integrantes.
- **Discussões e Decisões Tomadas:**
  - Definido o projeto Meowdoku (adaptação temática de Star Battle / Queens).
  - Escopo enquadrado como *Remix Original* com adição da mecânica de *Smart Hint* explicativo e modo com 2 gatos por linha/coluna/cor.
  - Criação da organização GitHub `Paradigmas-Grupo01` e repositórios `meow-Game` e `Meow-Docs`.
  - Configuração do ponto de partida de código com restrições CLP(FD) no Prolog e tipos de domínio em Elm.
- **Tarefas Atribuídas:**
  - Membro 1: Revisão e expansão dos testes em Prolog (`test_meowdoku.pl`).
  - Membro 2: Estudo e prototipação do algoritmo de partição de regiões para geração de tabuleiros.
  - Membro 3: Configuração do ambiente Python e validação do carregamento do Prolog via `janus`.
  - Membro 4 e 5: Estruturação dos decodificadores JSON e testes das regras puras em Elm.
  - Membro 6: Prototipação do CSS Grid e classes de cores para os territórios.
  - Membro 7: Leitura e configuração do validador `validar_entrega.py`.

---

## Ata 02 - Integração da Equipe e Desdobramento em 14 Issues (16/11/2026)
- **Horário:** 20:30 às 21:15
- **Local:** Discord
- **Presentes:** Gabriel Monteiro, Ana Luiza Fernandes, Tales, Renata Kurzawa, Cayo Alencar, Gabriel MS, Paola Lima
- **Pauta da Reunião:**
  1. Recepção dos 6 novos integrantes na organização `Paradigmas-Grupo01`.
  2. Alinhamento sobre o prazo limite do Lote 1: todas as tarefas devem estar concluídas até **18/11/2026 às 22h00** para validação e ensaio final.
  3. Desdobramento das 7 tarefas macro em pelo menos 2 issues individuais por integrante no GitHub (total de 14 issues vinculadas ao Milestone 1).
- **Discussões e Decisões Tomadas:**
  - Definido que 7 issues eram insuficientes para acompanhar o avanço granular do grupo; cada papel agora possui 2 issues no repositório `meow-Game`.
  - Fixado o deadline de 18/11 às 22h00 como marco rígido para que o Membro 7 possa rodar o script `validar_entrega.py` e a equipe realizar o ensaio da apresentação de 15 minutos com antecedência.
  - Criado o Milestone "Lote 1 - Entrega Final (18/11 às 22h)" no GitHub.
- **Tarefas Atribuídas (2 issues por integrante):**
  - Membro 1: Issues #1 e #8 (Prolog: restrições CSP, modo K=2 e plunit).
  - Membro 2: Issues #2 e #9 (Prolog: dicas com explicação dedutiva e geração conexa com solução única).
  - Membro 3: Issues #3 e #10 (Python: ponte Janus, rotas base, endpoint de dicas e testes pytest).
  - Membro 4: Issues #4 e #11 (Elm: domínio puro, imutabilidade, validação funcional de conflitos e vitória).
  - Membro 5: Issues #5 e #12 (Elm: decodificadores/codificadores JSON, ciclo TEA update e requisições HTTP).
  - Membro 6: Issues #6 e #13 (Elm/CSS: grid com cores por território, destaque de conflito, contador e modal de vitória).
  - Membro 7: Issues #7 e #14 (QA: execução de validar_entrega.py, preenchimento das 13 seções do RELATORIO.md e atas).

---

## Histórico de Versões

<p className="tabela-titulo">Tabela 4: Histórico de versões</p>

| Versão | Data | Descrição | Autor(es) | Revisor(es) |
| :---: | :---: | :--- | :--- | :--- |
| `1.0` | 04/11/2026 | Registro da ata do Ponto de Controle 1 e acompanhamento das correções pedidas pela professora | [Gabriel Monteiro](https://github.com/GabrielSMonteiro) | |
| `1.1` | 14/11/2026 | Registro da Ata 01 (Alinhamento Inicial e Definição do Escopo) | [Gabriel Monteiro](https://github.com/GabrielSMonteiro) | |
| `1.2` | 16/11/2026 | Registro da Ata 02 (Integração da equipe, 14 issues e deadline para 18/11 às 22h) | [Gabriel Monteiro](https://github.com/GabrielSMonteiro) | |

<p className="tabela-fonte">Fonte: [Gabriel Monteiro](https://github.com/GabrielSMonteiro), 2026.</p>

