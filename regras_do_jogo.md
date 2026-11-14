# Regras do Jogo e Pontos de Originalidade: Meowdoku

---

## 1. Regras do Jogo Base

O **Meowdoku** é um puzzle lógico disputado em uma grade quadrada $N \times N$, dividida em $N$ territórios coloridos conexos.

O objetivo do jogador é posicionar gatos na grade de forma a respeitar três restrições fundamentais:

1. **Restrição de Linhas:** Cada linha horizontal deve conter exatamente **$K$ gatos** (no modo padrão, $K = 1$).
2. **Restrição de Colunas:** Cada coluna vertical deve conter exatamente **$K$ gatos**.
3. **Restrição de Territórios (Cores):** Cada território de mesma cor deve conter exatamente **$K$ gatos**.
4. **Restrição de Não-Adjacência Felina (Vizinhança de Chebyshev):**
   Gatos são criaturas territoriais: **nenhum gato pode tocar em outro gato**, nem ortogonalmente (cima, baixo, esquerda, direita) e nem diagonalmente.
   * Matematicamente: se um gato está em $(R_1, C_1)$ e outro em $(R_2, C_2)$, deve valer:
     $$\max(|R_1 - R_2|, |C_1 - C_2|) > 1$$

---

## 2. Pontos de Originalidade (Remix Original $\Delta = +0{,}5$)

Para se diferenciar de clones comuns de *Star Battle* e Sudoku (garantindo o bônus máximo de originalidade da rubrica da UnB), o projeto incorpora:

### 2.1 Smart Feline Hint (Dica com Dedução Explicativa)
Ao solicitar uma dica, o motor em Prolog não apenas injeta o gato na resposta, mas executa um predicado dedutivo que identifica a causa lógica da jogada e a transmite em linguagem natural:
* *Exemplo 1:* `"Na Região 3 (Rosa), a célula (2, 4) é a única posição que não é vizinha de nenhum outro gato já colocado."`
* *Exemplo 2:* `"A Linha 4 já possui seu gato na coluna 1. Portanto, todas as demais células da linha foram marcadas com 'X'."`

### 2.2 Modo "Dois Gatinhos" (Double Trouble)
Em tabuleiros maiores ($8 \times 8$ ou $10 \times 10$), o jogador pode ativar o modo com **$K = 2$ gatos por linha, coluna e região**, multiplicando o espaço de busca e as deduções lógicas, mantendo a regra de que nenhum gato pode tocar outro gato.

### 2.3 Modo "Caixa de Papelão" (Cardboard Obstacle)
Obstáculos estáticos colocados estrategicamente pelo gerador onde gatos não podem entrar, forçando bifurcações interessantes de resolução lógica no CLP(FD).

