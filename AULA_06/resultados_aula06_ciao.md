# Resultados — Aula 06: ACO e Algoritmos Híbridos


//LABORATÓRIO 01 — ACO: Otimização por Colônia de Formigas

//Outputs da execução

Matriz inicial de feromônio:
```
[[1. 1. 1. 0. 0. 0.]
 [1. 1. 1. 1. 0. 0.]
 [1. 1. 1. 1. 1. 0.]
 [0. 1. 1. 1. 1. 1.]
 [0. 0. 1. 1. 1. 1.]
 [0. 0. 0. 1. 1. 1.]]
```

 Vizinhos:
- Vizinhos do nó 0: `[1, 2]`
- Vizinhos do nó 2: `[0, 1, 3, 4]`

//Rotas construídas por 5 formigas (exploração inicial):
```
Formiga 1: [0, 1, 2, 3, 4, 5]
Formiga 2: [0, 1, 2, 3, 4, 5]
Formiga 3: [0, 1, 2, 3, 4, 5]
Formiga 4: [0, 1, 2, 3, 4, 5]
Formiga 5: [0, 2, 1, 3, 4, 5]
```

//Rota de teste e custo:
- Rota: `[0, 1, 2, 3, 4, 5]` | Custo: `8.0`

//Resultado final (20 formigas, 50 iterações, ALPHA=1.0, BETA=2.0, evaporação=0.5):
```
Melhor rota encontrada: [0, 1, 2, 3, 4, 5]
Melhor custo: 8.0
```

Matriz final de feromônio:
```
[[  0. 500.   0.   0.   0.   0.]
 [  0.   0. 500.   0.   0.   0.]
 [  0.   0.   0. 500.   0.   0.]
 [  0.   0.   0.   0. 500.   0.]
 [  0.   0.   0.   0.   0. 500.]
 [  0.   0.   0.   0.   0.   0.]]
```

Curva de convergência:

![Convergência ACO Lab01](lab01_aula06_ciao_img1.png)

Mapa de calor do feromônio final:

![Feromônio final Lab01](lab01_aula06_ciao_img2.png)


Respostas:

1. Por que o ACO utiliza várias formigas em vez de apenas uma formiga procurando a melhor rota?

Uma única formiga só consegue explorar um caminho de cada vez e, sem nenhuma informação prévia de feromônio, sua escolha seria praticamente aleatória ela poderia ficar presa em uma rota ruim sem nunca descobrir alternativas melhores. Usar várias formigas permite que a colônia explore simultaneamente diferentes caminhos da rede a cada iteração. Isso gera diversidade de soluções, aumenta a chance de que pelo menos uma formiga encontre um caminho de baixo custo, e é justamente essa exploração paralela que alimenta o mecanismo de feromônio: quanto mais rotas diferentes forem testadas, mais rica é a "experiência coletiva" que orienta a busca nas iterações seguintes.

2. Por que uma rota de menor custo recebe mais feromônio?

Porque o depósito de feromônio é calculado como um custo. Quanto menor o custo da rota, maior é esse valor, logo mais feromônio é depositado nas arestas percorridas. Essa regra é a forma que o algoritmo tem de "premiar" boas soluções: rotas baratas ficam mais atrativas (mais feromônio) para as próximas formigas, que passam a escolhê-las com maior probabilidade. Isso cria um ciclo de reforço positivo — boas rotas atraem mais formigas, que depositam ainda mais feromônio nelas — fazendo a colônia convergir gradualmente para as soluções de menor custo.

3. O que poderia acontecer se não existisse evaporação do feromônio?

Sem evaporação, o feromônio depositado nas primeiras iterações nunca diminuiria, apenas se acumularia. Isso significa que, se por acaso as primeiras formigas encontrassem uma rota apenas razoável (não necessariamente a melhor), essa rota acabaria dominando permanentemente as escolhas futuras, pois seu feromônio acumulado sempre seria maior do que o de qualquer rota nova, mesmo que essa rota nova fosse melhor. O algoritmo perderia a capacidade de "esquecer" escolhas antigas e ficaria preso em ótimos locais, sem explorar novas possibilidades. A evaporação é o que permite que soluções mais recentes e potencialmente melhores tenham chance de competir com as soluções antigas.

---

## LABORATÓRIO 02 — Experimentando o ACO

Outputs dos experimentos

Experimento 1 — Influência do ALPHA (BETA=2.0, evaporação=0.5, 20 formigas, 50 iterações)

| ALPHA | Melhor rota | Melhor custo | Fração média de formigas na rota ótima |
|---|---|---|---|
| 1.0 | [0, 1, 2, 3, 4, 5] | 8.0 | 99% |
| 0.1 | [0, 1, 2, 3, 4, 5] | 8.0 | 61% |
| 5.0 | [0, 1, 2, 3, 4, 5] | 8.0 | 99% |

![Experimento ALPHA](lab02_aula06_ciao_img1.png)

Experimento 2 — Influência do BETA (ALPHA=1.0, evaporação=0.5)

| BETA | Melhor rota | Melhor custo | Fração média de formigas na rota ótima |
|---|---|---|---|
| 2.0 | [0, 1, 2, 3, 4, 5] | 8.0 | 99% |
| 0.5 | [0, 1, 2, 3, 4, 5] | 8.0 | 93% |
| 5.0 | [0, 1, 2, 3, 4, 5] | 8.0 | 100% |

![Experimento BETA](lab02_aula06_ciao_img2.png)

Experimento 3 — Evaporação (ALPHA=1.0, BETA=2.0)

| Taxa de evaporação | Melhor rota | Melhor custo | Fração média de formigas na rota ótima |
|---|---|---|---|
| 0.5 | [0, 1, 2, 3, 4, 5] | 8.0 | 99% |
| 0.1 | [0, 1, 2, 3, 4, 5] | 8.0 | 99% |
| 0.9 | [0, 1, 2, 3, 4, 5] | 8.0 | 99% |

![Experimento Evaporação](lab02_aula06_ciao_img3.png)

**Experimento 4 — Número de formigas**

| Número de formigas | Melhor rota | Melhor custo |
|---|---|---|
| 20 | [0, 1, 2, 3, 4, 5] | 8.0 |
| 5 | [0, 1, 2, 3, 4, 5] | 8.0 |
| 50 | [0, 1, 2, 3, 4, 5] | 8.0 |

![Experimento Número de Formigas](lab02_aula06_ciao_img4.png)

Respostas

Experimento 1 (ALPHA): Quando aumentamos o ALPHA, a influência da experiência acumulada (feromônio) aumenta. Isso significa que a colônia passa a confiar mais no que já foi descoberto anteriormente, reforçando ainda mais as rotas já usadas. Com ALPHA baixo (0.1), o feromônio quase não pesa na decisão, e as formigas escolhem os caminhos quase que só pelo custo — o que gera mais exploração e menos "memória coletiva".

Experimento 2 (BETA): Com BETA baixo, o custo do caminho tem pouca influência na escolha, tornando as formigas mais tolerantes a caminhos caros (mais exploração aleatória). Com BETA alto, caminhos de menor custo tornam-se muito mais atrativos, fazendo com que a colônia explote rapidamente os trechos mais baratos, mesmo com pouco feromônio acumulado.

Experimento 3 (Evaporação):Quando o algoritmo "esquece" rapidamente as experiências anteriores (evaporação alta, ex.: 0.9), o feromônio se dissipa quase todo a cada iteração, e a colônia depende muito mais das descobertas mais recentes — o que aumenta a exploração, mas pode tornar a convergência mais instável. Com evaporação baixa (0.1), o feromônio acumulado permanece por mais tempo, favorecendo a explotação de rotas já conhecidas, mas com risco maior de ficar preso a uma solução inicial caso ela não seja a ótima.

Experimento 4 (Número de formigas): Com poucas formigas (5), a exploração da rede a cada iteração é mais limitada — menos caminhos são testados simultaneamente, e a colônia demora relativamente mais para acumular experiência suficiente. Com muitas formigas (50), a rede é explorada de forma muito mais ampla em cada iteração, acelerando a descoberta e o reforço da rota ótima, ao custo de mais processamento computacional por iteração.


## LABORATÓRIO 03 — Completando o ACO

//Outputs da execução

```
Melhor rota: [0, 1, 2, 3, 4, 5]
Melhor custo: 8.0
```

Curva de convergência:

![Convergência ACO Lab03](lab03_aula06_ciao_img1.png)

Respostas:

1. Por que a fórmula da atratividade utiliza 1/custo em vez de utilizar diretamente o custo?

Porque o objetivo do algoritmo é minimizar o custo — encontrar o caminho mais barato. Usando 1/custo, caminhos com custo baixo geram um valor alto de atratividade, e caminhos com custo alto geram um valor baixo. Se a fórmula usasse o custo diretamente, o efeito seria o oposto: caminhos caros pareceriam mais "atrativos" e mais prováveis de serem escolhidos, o que iria contra a lógica de otimização do problema.

2. O que acontece com a atratividade quando uma rota recebe mais feromônio?

Como a atratividade é calculada por feromônio^ALPHA × (1/custo)^BETA, um aumento no feromônio de uma aresta eleva diretamente o valor da atratividade daquele caminho (considerando ALPHA > 0). Isso aumenta a probabilidade de essa aresta ser escolhida pelas próximas formigas, reforçando o comportamento de "seguir os caminhos que já deram certo" — a base do mecanismo de aprendizado coletivo do ACO.

3. Por que a função construir_rota() precisa impedir que a formiga visite novamente um nó que já está na rota?

Sem essa restrição, a formiga poderia entrar em um ciclo infinito, indo e voltando entre os mesmos nós sem nunca chegar ao destino. Além disso, revisitar nós geraria rotas inválidas (com repetições) e custos artificialmente maiores, sem sentido prático para o problema de encontrar o caminho mais curto entre origem e destino. Impedir a revisita garante que cada rota construída seja um caminho válido, progressivo e finito na rede.


## LABORATÓRIO 04 — ACO do Zero

//Outputs da execução

Resultado com os parâmetros mínimos (20 formigas, 50 iterações, ALPHA=1.0, BETA=2.0, evaporação=0.5, Q=100):
```
========== RESULTADO ==========
Melhor rota encontrada: [0, 1, 2, 3, 4, 5]
Melhor custo: 8.0
```

Curva de evolução do melhor custo:

![Convergência ACO Lab04](lab04_aula06_ciao_img1.png)

Teste de sensibilidade a diferentes parâmetros:

| Configuração | Formigas | Iterações | ALPHA | BETA | Evaporação | Melhor rota | Melhor custo |
|---|---|---|---|---|---|---|---|
| Base | 20 | 50 | 1.0 | 2.0 | 0.5 | [0, 1, 2, 3, 4, 5] | 8.0 |
| Mais formigas | 50 | 50 | 1.0 | 2.0 | 0.5 | [0, 1, 2, 3, 4, 5] | 8.0 |
| Mais iterações | 20 | 150 | 1.0 | 2.0 | 0.5 | [0, 1, 2, 3, 4, 5] | 8.0 |
| ALPHA alto | 20 | 50 | 5.0 | 2.0 | 0.5 | [0, 1, 2, 3, 4, 5] | 8.0 |
| BETA alto | 20 | 50 | 1.0 | 5.0 | 0.5 | [0, 1, 2, 3, 4, 5] | 8.0 |
| Evaporação alta | 20 | 50 | 1.0 | 2.0 | 0.9 | [0, 1, 2, 3, 4, 5] | 8.0 |

![Sensibilidade a parâmetros Lab04](lab04_aula06_ciao_img2.png)


Respostas:

1. Explique, com suas palavras, como o feromônio ajuda o ACO a aprender quais caminhos são melhores.

O feromônio funciona como uma "memória coletiva" da colônia. Cada vez que uma formiga percorre uma rota, ela deposita feromônio proporcional à qualidade dessa rota (quanto menor o custo, maior o depósito). Com o passar das iterações, os caminhos que foram percorridos por rotas boas acumulam mais feromônio, tornando-se mais atrativos para as próximas formigas. Ao mesmo tempo, a evaporação reduz gradualmente o feromônio de caminhos que não são mais reforçados. Esse ciclo de depósito e evaporação faz com que a informação sobre "quais caminhos valem a pena" seja compartilhada indiretamente entre todas as formigas da colônia, permitindo que o algoritmo aprenda, de forma distribuída, sem nenhuma formiga individual conhecer o problema como um todo

2. Qual é a diferença entre explorar novos caminhos e aproveitar caminhos que já demonstraram ser bons?

Explorar (exploração) significa que a formiga arrisca escolher caminhos com pouco ou nenhum feromônio, tentando descobrir alternativas ainda não testadas — isso é importante para não deixar o algoritmo preso em soluções apenas razoáveis. Aproveitar (explotação) significa seguir os caminhos que já acumularam bastante feromônio por terem se mostrado bons no passado, aproveitando o conhecimento já obtido pela colônia. O ACO precisa balancear essas duas forças: exploração demais impede a convergência (a colônia nunca se firma em uma boa solução); explotação demais pode levar a um ótimo local, ignorando caminhos melhores ainda não descobertos. Os parâmetros ALPHA, BETA e a taxa de evaporação controlam justamente esse equilíbrio.

3. Se você precisasse melhorar o desempenho desse ACO para uma rede muito maior, qual parâmetro ou parte do algoritmo você investigaria primeiro? Justifique.

Investigaria primeiro a taxa de evaporação e o equilíbrio entre ALPHA e BETA, pois em redes muito maiores o espaço de busca cresce muito, e o risco de convergência prematura para um ótimo local aumenta bastante. Uma evaporação bem ajustada é essencial para permitir exploração contínua sem perder o conhecimento acumulado nas rotas boas. Além disso, investigaria a função de construção de rota, pois em grafos grandes o custo computacional de percorrer todos os vizinhos e recalcular atratividades a cada passo cresce rapidamente; técnicas como limitar o número de candidatos avaliados, paralelizar a construção de rotas entre as formigas, ou usar estruturas de dados mais eficientes para representar o grafo (ex.: listas de adjacência ao invés de matriz densa) ajudariam a manter o algoritmo viável em escala. Por fim, também avaliaria o número de formigas e iterações, já que redes maiores tendem a exigir mais amostragem para que o feromônio reflita bem a estrutura do problema.

