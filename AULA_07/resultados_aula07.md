

## LAB 01 - ACO com Busca Local (Exploration vs. Exploitation)



Output da execução:

```
[LAB 01 - SUCESSO] Melhor Caminho: [0, 1, 3, 4, 2, 0] | Custo: 70
```

![alt text](image.png)

Respostas: 

1 - Como o uso da busca local 2-opt afeta o equilíbrio entre Exploration e Exploitation na busca de caminhos?

A construção probabilística das rotas pelas formigas, guiada por feromônio e visibilidade, é a parte de Exploration: ela varre diferentes regiões do espaço de busca e gera diversidade de soluções. A busca local 2-opt é a parte de Exploitation: ela pega a rota construída por cada formiga e a refina, invertendo trechos até não haver mais melhoria. Com o 2-opt, o equilíbrio se desloca para a intensificação, porque cada formiga entrega um ótimo local e não uma rota apenas razoável. Isso acelera a convergência e reduz o custo já nas primeiras iterações, mas aumenta o risco de convergência prematura, já que muitas formigas passam a terminar em rotas parecidas e o feromônio se concentra nelas. Por isso a evaporação e a aleatoriedade na escolha dos nós continuam sendo importantes para manter a exploração.

2 - O que aconteceria com a convergência do algoritmo se a taxa de evaporação (rho) fosse definida em 0.0 (sem evaporação)?

Sem evaporação, o feromônio só cresce e nunca é esquecido. Os rastros das primeiras soluções, mesmo as ruins, permanecem com a mesma força, e os depósitos se acumulam sem limite. Isso faz o feromônio dominar a probabilidade de escolha rapidamente, e o algoritmo passa a repetir os mesmos caminhos (estagnação), perdendo exploração. A convergência seria rápida, porém prematura, com alta chance de ficar preso em um ótimo local, sem capacidade de corrigir decisões iniciais ruins.


## LAB 02 - Algoritmo Genético: Seleção, Crossover e Mutação



Output da execução:

```
Geração 01 | Melhor fitness: 13 | Fitness médio: 5.10
Geração 02 | Melhor fitness: 13 | Fitness médio: 7.90
Geração 03 | Melhor fitness: 15 | Fitness médio: 11.60
Geração 04 | Melhor fitness: 15 | Fitness médio: 10.80
Geração 05 | Melhor fitness: 15 | Fitness médio: 10.00
Geração 06 | Melhor fitness: 15 | Fitness médio: 9.30
Geração 07 | Melhor fitness: 15 | Fitness médio: 11.00
Geração 08 | Melhor fitness: 15 | Fitness médio: 11.80
Geração 09 | Melhor fitness: 15 | Fitness médio: 10.70
Geração 10 | Melhor fitness: 15 | Fitness médio: 12.80
Melhor indivíduo final: [0 1 1 1 1] | Peso: 8 | Valor: 15
[LAB 02] Execute e teste o seu algoritmo preenchido!
```

Respostas:

1 - Explique qual é o papel do operador de Mutação em um Algoritmo Genético e o que ocorre se a taxa de mutação for configurada em 100%.

A mutação introduz diversidade genética na população, alterando genes de forma aleatória. Ela permite recuperar informações perdidas pela seleção e pelo crossover e evita que a população fique presa em um ótimo local. Com taxa de 100%, todos os genes de todos os filhos seriam invertidos a cada geração, e o algoritmo deixaria de herdar o que os pais tinham de bom. O crossover e a seleção perderiam o efeito, e a busca viraria praticamente aleatória, sem convergência.

2 - Por que a penalização do fitness (atribuir 0 para indivíduos que estouram a capacidade) é fundamental para a convergência das restrições?

Sem a penalização, o algoritmo veria como melhores as soluções que pegam todos os itens, mesmo ultrapassando a capacidade da mochila, e convergiria para soluções inválidas. Ao atribuir fitness 0 a quem estoura o peso máximo, esses indivíduos perdem nos torneios e deixam de ser escolhidos como pais, e a população é empurrada para a região factível do espaço de busca. Assim a restrição é respeitada sem precisar de um mecanismo de reparo explícito.


## LAB 03 - PSO: Inércia, Componente Cognitiva e Social


Output da execução:

```
[LAB 03] Melhor posição encontrada pelo Enxame (gbest): [ 0.00742668 -0.0130891 ]
[LAB 03] Fitness do gbest: 0.00022648016727061363
```

Respostas:

1 - O que acontece com o comportamento das partículas se zerarmos a componente cognitiva (c_1 = 0)?

As partículas deixam de ser atraídas pela melhor posição que elas mesmas já visitaram (pbest) e passam a ser guiadas apenas pela inércia e pelo melhor global (gbest). O enxame vira um comportamento puramente social: todas correm na direção do líder atual. A convergência tende a ser mais rápida, mas a diversidade cai e há maior risco de convergência prematura para um mínimo local, porque as partículas perdem a memória individual que as ajudava a explorar regiões diferentes.

2 - Qual a função do parâmetro de Inércia (w) na busca por mínimos globais?

A inércia controla quanto da velocidade anterior é mantida. Valores altos de w favorecem a exploração global, pois as partículas continuam se movendo em sua direção e varrem mais espaço. Valores baixos favorecem a exploração local (exploitation), pois a velocidade é rapidamente dominada pelas atrações do pbest e do gbest. Um w bem ajustado, ou decrescente ao longo das iterações, equilibra os dois comportamentos e ajuda a escapar de mínimos locais antes de refinar a solução.


## LAB 04 - ACO: Feromônio, Evaporação e Atratividade


Output da execução:

```
[LAB 04] Matriz de Feromônio Atualizada:
 [[0.75       0.91666667 0.91666667 0.75      ]
 [0.75       0.75       0.75       1.08333333]
 [0.75       0.91666667 0.75       0.75      ]
 [0.75       0.75       0.75       0.75      ]]
```

respostas:

1 - Por que a evaporação do feromônio é necessária no algoritmo ACO?

A evaporação faz o sistema esquecer gradualmente rastros antigos. Ela impede que o feromônio cresça indefinidamente e que as primeiras soluções encontradas, que podem ser ruins, dominem a busca para sempre. Com isso, caminhos pouco reforçados perdem atratividade e o algoritmo mantém a capacidade de explorar alternativas.

2 - O que ocorreria em grafos complexos sem ela? Qual a relação matemática entre a latência de um enlace e sua atratividade inicial (eta) para as formigas?

Em grafos complexos, sem evaporação os rastros se acumulariam em muitos enlaces ao mesmo tempo, as diferenças entre bons e maus caminhos ficariam diluídas ou travadas nas primeiras escolhas, e o algoritmo estagnaria em soluções subótimas, sem conseguir abandonar caminhos ruins. A atratividade inicial é inversamente proporcional à latência do enlace: eta(i,j) = 1 / latência(i,j). Enlaces com menor latência têm maior eta e, portanto, maior probabilidade de serem escolhidos pelas formigas. Na regra de decisão, ela entra elevada a beta: eta^beta.


## LAB 05 - Memético: Meta-heurística + Busca Local


Output da execução:

```
[LAB 05] Solução Inicial: [ 2.5 -3.1] | Fitness: 37.7698
[LAB 05] Solução Refinada: [ 2.47553974 -3.04650038] | Fitness: 35.7154
```

Respostas:

1 - Qual a diferença fundamental de conceito entre um Algoritmo Genético Puro e um Algoritmo Memético?

O Algoritmo Genético puro evolui a população apenas com seleção, crossover e mutação, ou seja, só com aprendizado populacional. O Algoritmo Memético combina esse processo evolutivo com uma busca local aplicada aos indivíduos (aprendizado individual, inspirado nos "memes"), que refina cada solução na sua vizinhança. O resultado é a união de exploração global, feita pelo AG, com intensificação local, feita pela busca local, o que em geral acelera a convergência e melhora a qualidade das soluções.

2 - Em termos de custo computacional, qual o impacto de executar a busca local sobre todos os indivíduos de uma população a cada geração?

O custo aumenta bastante. Cada indivíduo passa a exigir várias avaliações extras da função de fitness, e o custo por geração é aproximadamente tamanho da população × número de passos da busca local, além das avaliações normais do AG. Se a função de fitness for cara, isso pode inviabilizar o método. Por isso, na prática, costuma-se aplicar a busca local só a uma fração da população, só aos melhores indivíduos, ou a cada certo número de gerações, em troca de menos gerações para convergir.
