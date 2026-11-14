# Arquitetura do Sistema: Meowdoku

---

## 1. Visão Arquitetural

```
┌────────────────────────────────┐   HTTP/JSON   ┌───────────────────┐   janus   ┌──────────────────────────┐
│ Frontend Web (Elm 0.19)        │ ────────────▶ │ FastAPI (Python)  │ ────────▶ │ SWI-Prolog (CLP/FD)      │
│ - Elm Architecture (TEA)       │ ◀──────────── │ backend/app/      │ ◀──────── │ meowdoku.pl              │
│ - Modelagem com Custom Types   │               │ Ponte HTTP pura   │           │ - solve/3                │
│ - Validação local de conflitos │               │ (< 20% do código) │           │ - hint/4                 │
└────────────────────────────────┘               └───────────────────┘           │ - valid_solution/3       │
          [Avaliado: 30%]                            [Não Avaliado]              └──────────────────────────┘
                                                                                         [Avaliado: 20%]
```

---

## 2. Camada Lógica (SWI-Prolog com CLP/FD)

A camada em Prolog é o núcleo inteligente do sistema:
* **Arquivo:** `backend/prolog/meowdoku.pl`
* **Biblioteca:** `library(clpfd)` para modelagem CSP.
* **Variáveis de Decisão:** Para uma grade $N \times N$, cria-se uma matriz de variáveis binárias $C_{i,j} \in \{0, 1\}$.
* **Restrições:**
  * Linhas: `maplist(sum_equals(K), Solution)`
  * Colunas: `transpose(Solution, Cols), maplist(sum_equals(K), Cols)`
  * Territórios: agrupamento por ID de região e soma igual a $K$.
  * Adjacência: para cada par vizinho $(A, B)$, $A + B \le 1$.
* **Testes Automatizados:** `backend/prolog/test_meowdoku.pl` com a biblioteca `plunit`.

---

## 3. Camada Funcional (Elm 0.19)

O frontend adota a Arquitetura Elm (The Elm Architecture - TEA):
* **Arquivo de Domínio:** `frontend/src/Meowdoku.elm`
  * Impossibilita estados inválidos por construção.
  * Validação puramente funcional instantânea de conflitos (`checkConflicts`).
* **Arquivo de Comunicação:** `frontend/src/Api.elm`
  * Decoders e encoders JSON com tipagem estrita.
  * Tratamento de falhas de rede e erros HTTP.
* **Arquivo Principal:** `frontend/src/Main.elm`
  * Gerenciamento de estado, view reativa, ciclo de cliques e animações.

---

## 4. Camada de Integração (Python FastAPI + Janus)

* **Arquivos:** `backend/app/meowdoku_prolog.py` e `backend/app/main.py`
* **Papel:** Embutir o runtime do SWI-Prolog via biblioteca oficial `janus-swi` e expor rotas REST documentadas via OpenAPI/Swagger (`/docs`).
* **Diretriz de Avaliação:** Manter menos de 20% das linhas do repositório em Python, garantindo que toda a inteligência permaneça no Prolog e no Elm.
