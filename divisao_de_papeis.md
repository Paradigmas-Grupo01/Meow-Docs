# Divisão de Papéis e Responsabilidades (7 Integrantes)

Esta matriz foi elaborada para atender rigorosamente à **Seção 10 do `RELATORIO.md`** e aos critérios de avaliação da UnB:

---

## Matriz de Responsabilidades

| Integrante | Função Oficial | Módulos e Arquivos | Critério de Pronto (DoD) |
| :--- | :--- | :--- | :--- |
| **Membro 1** | *Engenheiro de Restrições Prolog* | `backend/prolog/meowdoku.pl`<br>`backend/prolog/test_meowdoku.pl` | Modelagem matemática do CSP com CLP(FD), predicado `solve/3` e suite de testes `plunit` passando sem falhas nem warnings. |
| **Membro 2** | *Algoritmo de Dicas e Geração* | `backend/prolog/meowdoku.pl`<br>(predicados `hint` e `generate`) | Implementação do predicado dedutivo `hint/4` com explicação em texto e geração de mapas conexos com solução única comprovada. |
| **Membro 3** | *Arquiteto de Integração Python* | `backend/app/meowdoku_prolog.py`<br>`backend/app/main.py`<br>`backend/tests/` | Ponte `janus` entre FastAPI e SWI-Prolog funcionando, rotas documentadas no Swagger e cobertura de testes de API. |
| **Membro 4** | *Engenheiro de Domínio Elm* | `frontend/src/Meowdoku.elm` | Tipagem pura do modelo (`CellMark`, `Cell`, `Board`), ciclo de marcação e validação local instantânea de conflitos (`checkConflicts`). |
| **Membro 5** | *Engenheiro de API & HTTP Elm* | `frontend/src/Api.elm`<br>`frontend/src/Main.elm` (update) | Mapeamento JSON (`meowdokuPuzzleDecoder`, `meowdokuHintDecoder`), ciclo de comandos assíncronos (`Cmd Msg`) e tratamento de erros. |
| **Membro 6** | *Designer de UI/UX & Interações* | `frontend/src/Main.elm` (view)<br>`frontend/src/style.css` | Layout em CSS Grid/SVG, estilização de regiões com paleta pastel, sprites dos gatos, contador de gatos e modal comemorativo. |
| **Membro 7** | *QA, Validação e Relatório* | `RELATORIO.md`<br>`scripts/validar_entrega.py`<br>`frontend/tests/` | Validação formal do relatório (`validar_entrega.py` com zero erros), testes de integração e redação da Seção 13 (reflexão dos paradigmas). |
