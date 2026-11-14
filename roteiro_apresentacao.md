# Roteiro da Apresentação Oral (15 Minutos)

**Regra Geral da Avaliação:** Todos os 7 integrantes devem falar ativamente durante a apresentação. O grupo será cronometrado rigorosamente.

---

## ⏱️ Distribuição de Tempo

### Minutos 0 a 3: Introdução e Demonstração do Jogo
* **Quem fala:** Membro 6 (UI/UX) e Membro 7 (QA/Relatório).
* **O que mostrar:**
  * Apresentar o tema felino do Meowdoku e as regras de não-adjacência.
  * Jogar ao vivo: clicar para marcar X em casas proibidas, colocar gatos nas casas certas.
  * Demonstrar o feedback instantâneo de conflito em vermelho quando dois gatos se tocam.
  * Clicar no botão "Dica Inteligente" e mostrar o pop-up com a dedução em texto.

### Minutos 3 a 7: Aprofundamento no Paradigma Lógico (Prolog)
* **Quem fala:** Membro 1 (Restrições) e Membro 2 (Dicas/Unicidade).
* **O que mostrar no código:**
  * Abrir `backend/prolog/meowdoku.pl`.
  * Mostrar como a biblioteca `clpfd` define o domínio binário `0..1`.
  * Explicar a restrição de não-adjacência $A + B \le 1$.
  * Explicar como a dica dedutiva identifica a regra violada.
  * Executar os testes unitários ao vivo:
    ```sh
    swipl -g run_tests -t halt backend/prolog/test_meowdoku.pl
    ```

### Minutos 7 a 11: Aprofundamento no Paradigma Funcional (Elm)
* **Quem fala:** Membro 4 (Domínio) e Membro 5 (API/HTTP).
* **O que mostrar no código:**
  * Abrir `frontend/src/Meowdoku.elm`.
  * Mostrar os Custom Types (`CellMark = Empty | MarkedX | HasCat`) destacando como eles impedem estados inválidos.
  * Mostrar a função pura `checkConflicts : Board -> Board`.
  * Abrir `frontend/src/Api.elm` e mostrar a composição de decodificadores JSON com `Decode.map4`.

### Minutos 11 a 13: Arquitetura de Integração (Python/Janus)
* **Quem fala:** Membro 3 (Ponte Python).
* **O que mostrar:**
  * Abrir `backend/app/meowdoku_prolog.py` e `backend/app/main.py`.
  * Mostrar a chamada `janus.query_once` conectando a rota FastAPI diretamente ao interpretador Prolog embutido.
  * Destacar que o Python atua exclusivamente como ponte serializadora (< 20% do código).

### Minutos 13 a 15: Arguição Individual e Perguntas da Banca
* **Quem fala:** Todos os membros respondem às perguntas do professor sobre suas respectivas partes.
