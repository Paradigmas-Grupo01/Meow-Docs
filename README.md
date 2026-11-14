# Meow-Docs: Documentação do Meowdoku

Repositório de código: https://github.com/Paradigmas-Grupo01/meow-Game  
Organização: Paradigmas-Grupo01  
Disciplina: Paradigmas de Programação - FGA/UnB  
Professor: Fábio Macêdo Mendes  
Semestre: 2026/2  

---

## Visão Geral

Este repositório reúne a documentação de apoio do projeto Meowdoku, desenvolvido para a avaliação final da disciplina de Paradigmas de Programação.

O jogo baseia-se nas regras de Star Battle (e puzzles semelhantes, como Queens), adaptado para uma temática visual de gatos. A proposta do trabalho é exercitar na prática os dois paradigmas principais vistos no semestre:

- Programação Lógica (SWI-Prolog): resolução por restrições usando CLP(FD), modelagem de vizinhança de Chebyshev para evitar adjacências entre gatos, verificação de unicidade de solução e geração de dicas explicativas.
- Programação Funcional (Elm): interface web construída segundo The Elm Architecture (TEA), tipagem estática que previne estados inválidos e validação puramente funcional no frontend.
- Camada de integração (Python / FastAPI): ponte mínima via janus apenas para conectar as chamadas HTTP do frontend ao interpretador SWI-Prolog, mantendo-se restrita a menos de 20% do código.

---

## Estrutura da Documentação

- [Plano de Ação e Cronograma](plano_de_acao.md): cronograma de desenvolvimento distribuído em etapas até a entrega do primeiro lote (18/11).
- [Regras do Jogo e Originalidade](regras_do_jogo.md): definição formal das restrições e mecânicas adicionadas ao jogo.
- [Arquitetura](arquitetura.md): fluxo de dados entre os componentes, endpoints da API e estrutura interna de módulos.
- [Divisão de Tarefas](divisao_de_papeis.md): atribuição de responsabilidades para os 7 integrantes da equipe, em conformidade com a Seção 10 do relatório de entrega.
- [Roteiro da Apresentação Oral](roteiro_apresentacao.md): divisão dos 15 minutos de banca entre os integrantes e pontos de atenção para as perguntas individuais.
