# Guia da Avaliação 360 Graus Individual

Cada integrante da equipe deve entregar obrigatoriamente um arquivo individual no seu próprio repositório gerado via GitHub Classroom, no caminho:  
`avaliacao-360/<sua-matricula>.md`

A data limite para entrega da avaliação 360 é **30/11/2026 às 23h59**. Não entregar desconta 0,5 ponto da nota individual.

---

## 1. Como a Nota Individual é Calculada

A nota individual ($I$) é derivada da nota do grupo ($G$) por meio da distribuição percentual de esforço atribuída pelos colegas:

$$\text{Parte Justa} = \frac{100}{N} \quad (N = 7 \implies \approx 14{,}28\%)$$

$$\text{Esforço} = \text{mediana do percentual atribuído pelos colegas}$$

$$F = \frac{\text{Esforço}}{\text{Parte Justa}}, \quad \text{limitado ao intervalo } [0{,}6 ; 1{,}2]$$

$$I = \min(10, G \times F)$$

- A autoavaliação (o percentual que você atribui a si mesmo) não entra no cálculo.
- A fórmula utiliza a **mediana** para anular avaliações extremas, vingativas ou combinadas.
- Se todos os colegas atribuírem a parte justa de esforço a você, $F = 1{,}0$ e sua nota individual será exatamente igual à nota do grupo ($I = G$).

---

## 2. Instruções de Preenchimento

1. Copie o arquivo `avaliacao-360/TEMPLATE.md` do repositório para `avaliacao-360/<sua-matricula>.md`.
2. Apague todos os comentários de instrução `<!-- ... -->`.
3. Preencha seu nome e matrícula.
4. Na tabela de notas (escala de 1 a 5), atribua notas para cada colega nos critérios de assiduidade, entrega e comunicação.
5. Na tabela de esforço, distribua os percentuais de forma que a soma de todos os integrantes (incluindo você) totalize **exatamente 100%**.
6. Justifique em parágrafos objetivos qualquer nota 1, 2 ou 5 atribuída.
7. Valide a forma do arquivo antes de submeter:
   ```sh
   python scripts/validar_entrega.py avaliacao-360/<sua-matricula>.md
   ```
