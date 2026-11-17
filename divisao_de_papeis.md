# Divisão de Papéis e Responsabilidades (7 Integrantes)

Esta matriz foi elaborada para atender rigorosamente à **Seção 10 do `RELATORIO.md`** e aos critérios de avaliação da UnB:

---

## Matriz de Responsabilidades

| Integrante | Função Oficial | Módulos e Arquivos | Issues (Prazo: 18/11 às 22h) | Critério de Pronto (DoD) |
| :--- | :--- | :--- | :--- | :--- |
| **Membro 1** | *Engenheiro de Restrições Prolog* | `backend/prolog/meowdoku.pl`<br>`backend/prolog/test_meowdoku.pl` | [#1](https://github.com/Paradigmas-Grupo01/meow-Game/issues/1) (Concluída)<br>[#8](https://github.com/Paradigmas-Grupo01/meow-Game/issues/8) (Concluída) | Modelagem do CSP com CLP(FD), parametrização K=2 e suite `plunit` com 8 testes passando com zero falhas. |
| **Membro 2** | *Algoritmo de Dicas e Geração* | `backend/prolog/meowdoku.pl` | [#2](https://github.com/Paradigmas-Grupo01/meow-Game/issues/2)<br>[#9](https://github.com/Paradigmas-Grupo01/meow-Game/issues/9) | Predicado dedutivo `hint/4` com explicação em texto e geração de mapas conexos com unicidade. |
| **Membro 3** | *Arquiteto de Integração Python* | `backend/app/meowdoku_prolog.py`<br>`backend/app/main.py`<br>`backend/tests/` | [#3](https://github.com/Paradigmas-Grupo01/meow-Game/issues/3)<br>[#10](https://github.com/Paradigmas-Grupo01/meow-Game/issues/10) | Ponte `janus` entre FastAPI e SWI-Prolog, validação Pydantic, rotas Swagger e testes pytest. |
| **Membro 4** | *Engenheiro de Domínio Elm* | `frontend/src/Meowdoku.elm` | [#4](https://github.com/Paradigmas-Grupo01/meow-Game/issues/4)<br>[#11](https://github.com/Paradigmas-Grupo01/meow-Game/issues/11) | Tipagem pura do modelo (`CellMark`, `Cell`, `Board`), ciclo de marcação, validação instantânea de conflitos e vitória. |
| **Membro 5** | *Engenheiro de API & HTTP Elm* | `frontend/src/Api.elm`<br>`frontend/src/Main.elm` (update) | [#5](https://github.com/Paradigmas-Grupo01/meow-Game/issues/5)<br>[#12](https://github.com/Paradigmas-Grupo01/meow-Game/issues/12) | Mapeamento JSON (`meowdokuPuzzleDecoder`, `meowdokuHintDecoder`), ciclo TEA (`init`, `update`, `Cmd Msg`) e erro HTTP. |
| **Membro 6** | *Designer de UI/UX & Interações* | `frontend/src/Main.elm` (view)<br>`frontend/src/style.css` | [#6](https://github.com/Paradigmas-Grupo01/meow-Game/issues/6)<br>[#13](https://github.com/Paradigmas-Grupo01/meow-Game/issues/13) | Layout em CSS Grid, paleta pastel por região, destaque de conflito, contador de gatos e modal de vitória. |
| **Membro 7** | *QA, Validação e Relatório* | `RELATORIO.md`<br>`scripts/validar_entrega.py`<br>`avaliacao-360/` | [#7](https://github.com/Paradigmas-Grupo01/meow-Game/issues/7)<br>[#14](https://github.com/Paradigmas-Grupo01/meow-Game/issues/14) | Validação formal do relatório (`validar_entrega.py` com zero erros), testes automatizados e consolidação da Seção 13. |

---

## Histórico de Versões

<p className="tabela-titulo">Tabela 1: Histórico de versões</p>

| Versão | Data | Descrição | Autor(es) | Revisor(es) |
| :---: | :---: | :--- | :--- | :--- |
| `1.0` | 14/11/2026 | Definição da matriz inicial de responsabilidades para 7 membros | [Gabriel Monteiro](https://github.com/GabrielSMonteiro) | |
| `1.1` | 16/11/2026 | Desdobramento em 2 issues por integrante (total 14 issues) com prazo até 18/11 às 22h | [Gabriel Monteiro](https://github.com/GabrielSMonteiro) | |
| `1.2` | 16/11/2026 | Conclusão e homologação das Issues #1 e #8 (Membro 1) com suíte de testes passando | [Gabriel Monteiro](https://github.com/GabrielSMonteiro) | |

<p className="tabela-fonte">Fonte: [Gabriel Monteiro](https://github.com/GabrielSMonteiro), 2026.</p>

