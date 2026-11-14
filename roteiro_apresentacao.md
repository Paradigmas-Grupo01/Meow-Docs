# Roteiro da Apresentação Oral (15 Minutos)

Critério do edital: todos os integrantes devem falar durante os 15 minutos e estar aptos a responder perguntas técnicas sobre o trecho de código atribuído a eles no relatório.

---

## Distribuição do Tempo

### 0 a 3 min: Demonstração Prática do Sistema
- Responsáveis: Membro 6 (UI/UX) e Membro 7 (QA/Relatório).
- Roteiro:
  - Contextualizar o problema e as regras de não-adjacência.
  - Interagir com a grade: marcar posições proibidas com "X" e posicionar gatos.
  - Mostrar a detecção instantânea de conflitos em vermelho no frontend.
  - Solicitar uma dica e exibir na tela a justificativa dedutiva gerada pelo motor em Prolog.

### 3 a 7 min: Paradigma Lógico (SWI-Prolog)
- Responsáveis: Membro 1 (Restrições) e Membro 2 (Dicas e Unicidade).
- Roteiro no código:
  - Exibir `backend/prolog/meowdoku.pl`.
  - Explicar a formulação em CLP(FD): domínio binário 0..1, restrições de linha, coluna e região.
  - Destacar o tratamento de vizinhança de Chebyshev (inequação $A + B \le 1$).
  - Explicar como a dica deriva a restrição violada em vez de apenas buscar o gabarito.
  - Rodar os testes automatizados em terminal:
    ```sh
    swipl -g run_tests -t halt backend/prolog/test_meowdoku.pl
    ```

### 7 a 11 min: Paradigma Funcional (Elm)
- Responsáveis: Membro 4 (Domínio) e Membro 5 (API/HTTP).
- Roteiro no código:
  - Exibir `frontend/src/Meowdoku.elm`.
  - Apresentar a modelagem por tipos algébricos (`type CellMark = Empty | MarkedX | HasCat`), mostrando por que ela impede estados inconsistentes.
  - Demonstrar a função pura `checkConflicts : Board -> Board`.
  - Exibir `frontend/src/Api.elm` e a decodificação tipada de JSON com `Json.Decode`.

### 11 a 13 min: Arquitetura de Integração (Python/Janus)
- Responsável: Membro 3 (Ponte Python).
- Roteiro no código:
  - Exibir `backend/app/meowdoku_prolog.py` e `backend/app/main.py`.
  - Demonstrar como o `janus` executa o arquivo Prolog diretamente na memória do processo Python.
  - Evidenciar a contagem de linhas para demonstrar que o Python não concentra lógica de domínio e respeita o teto de 20%.

### 13 a 15 min: Arguição Individual
- Todos os integrantes disponíveis para responder diretamente às perguntas do professor sobre suas contribuições declaradas na Seção 10.
