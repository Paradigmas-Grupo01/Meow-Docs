# Meow-Docs: Documentação Central do Meowdoku 🐱
**Repositório de Código:** [meow-Game](https://github.com/Paradigmas-Grupo01/meow-Game)  
**Organização:** [Paradigmas-Grupo01](https://github.com/Paradigmas-Grupo01)  
**Disciplina:** Paradigmas de Programação — Engenharia de Software (UnB/FGA)  
**Professor:** Fábio Macêdo Mendes  
**Semestre:** 2026/2  

---

## 📌 Visão Geral

Este repositório centraliza toda a documentação de engenharia, planejamento, especificação matemática de restrições, divisão de responsabilidades e ensaios de apresentação para o projeto **Meowdoku**.

O Meowdoku é um jogo de raciocínio lógico em grade inspirado nas mecânicas de *Star Battle* / *LinkedIn Queens*, contextualizado no universo felino. O sistema integra dois paradigmas fundamentais:
- **Paradigma Lógico (SWI-Prolog com CLP/FD):** Modelagem de restrições de tabuleiro, não-adjacência felina, busca, geração com solução única e motor de dedução para dicas inteligentes.
- **Paradigma Funcional (Elm 0.19):** Frontend web reativo (SPA) baseado na Arquitetura Elm (TEA), com modelagem rígida de tipos de domínio para eliminar estados inválidos e validação instantânea de conflitos.
- **Ponte de Integração (Python FastAPI + Janus):** Camada mínima (<20% do código) que conecta a interface em Elm ao runtime em C do SWI-Prolog.

---

## 📚 Índice de Documentos

1. [Plano de Ação e Cronograma](plano_de_acao.md): Roadmap detalhado das 4 sprints até a entrega final (Lote 1 em 18/11).
2. [Regras do Jogo e Pontos de Originalidade](regras_do_jogo.md): Especificação das regras básicas, restrições de vizinhança de Chebyshev e mecânicas originais (*Smart Hint*, *Double Trouble* e *Cardboard Obstacle*).
3. [Arquitetura do Sistema](arquitetura.md): Diagramas de fluxo de dados, contratos de API JSON/HTTP e modelagem dos módulos em Prolog e Elm.
4. [Divisão de Papéis e Responsabilidades](divisao_de_papeis.md): Matriz de responsabilidades para os 7 integrantes do grupo (alinhada à Seção 10 do relatório oficial e avaliação 360°).
5. [Roteiro da Apresentação Oral (15 Minutos)](roteiro_apresentacao.md): Minutagem detalhada da apresentação, guia de demonstração e perguntas esperadas da banca com respostas modelo.

---

## 🔗 Links Rápidos

* 🎮 **Código do Jogo:** [github.com/Paradigmas-Grupo01/meow-Game](https://github.com/Paradigmas-Grupo01/meow-Game)
* 📖 **Template Oficial do Curso:** [fabiommendes/paradigmas-trabalho-final](https://github.com/fabiommendes/paradigmas-trabalho-final)
* 📋 **Critérios de Avaliação:** Consulte o arquivo `AVALIACAO.md` no repositório de código.
