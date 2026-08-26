Total de solucoes avaliadas: 64
Tempo de execucao: 0.000742 segundos
Melhor valor encontrado: 8
Combinacao otima (0=nao leva, 1=leva): (1, 0, 1, 1, 0, 0)

Itens escolhidos:
 - Livro (peso: 2 , valor: 3 )
 - Camiseta (peso: 1 , valor: 2 )
 - Carregador (peso: 2 , valor: 3 )

1- Porque para cada item, no caso 5, temos somente duas possibilidades, levar ou não levar sendo valor 1=levar e 0=não levar. Com 5 itens fazemos 2x2x2x2x2= 32 combinações que formam o nosso espaço de busca.

2- Seguindo a mesma lógica, com 15 itens teriamos 32.768 possibilidades para o computador analisar, o suficiente para ele demorar mais para testar todas as combinações possíveis. Porém ainda é um número de possibilidades que um computador consegue usar "força bruta", o problema é quando aumentamos o números de itens, pois a cada 1 que adicionamos, o número de possibilidades práticamente duplica, por isso a importancia de entender o problema e aplicar por exemplo uma programação dinâmica.

3- Um outro caso parecido com esse seria o problema de campanhias aéreas de escolher a quantidade de cargas ideal para colocar no avião, respeitando o limite de peso.





<img width="642" height="342" alt="image" src="https://github.com/user-attachments/assets/c04d24ea-caf3-4b4b-8c73-cb382c7bcdab" />

<img width="436" height="84" alt="image" src="https://github.com/user-attachments/assets/1838a94e-9629-4899-94f5-0a398ad75085" />

1- o numero de rotas cresce de forma fatorial, por exemplo se uma cidade possui 6 rotas, esse valor será multiplicado por 4 (N-1)

2- <img width="340" height="70" alt="image" src="https://github.com/user-attachments/assets/4d4e3d07-4fdb-4a62-9ecc-9e6baad7584f" />

3- O TSP é considerado difícil porque o número de rotas cresce muito rapidamente com o número de cidades.
Na força-bruta, o número de rotas é dado por (n-1)!.
Por exemplo, 6 cidades geram 120 rotas, enquanto 10 geram 362.880.
Com mais cidades, o número de possibilidades aumenta de forma muito rápida.
Isso faz com que o tempo para testar todas as rotas fique cada vez maior.
Por isso, a força-bruta se torna inviável para problemas grandes.




<img width="497" height="439" alt="image" src="https://github.com/user-attachments/assets/1e0d90f7-9abe-4934-8ca4-5a7d952ced2d" />

20 - O gap médio costuma ficar na casa dos 3% a 8%, com alguns casos sendo 0%, a heurística acertou o ótimo cravado e em outros chegando a 15% ou mais de erro.

21- A heurística gulosa é boa porque encontra uma solução rapidamente.
Porém, ela nem sempre encontra a melhor solução possível.
Isso acontece porque escolhe os itens de maior valor/peso primeiro.
Eu usaria essa técnica em problemas grandes e que precisam de rapidez.
Ela também é útil quando uma solução aproximada já é suficiente,quando a solução precisa ser a melhor possível, usaria um método exato.
Assim, gastaria mais tempo para garantir o resultado ótimo.

=======================================================================================================================================

LAB 04
1. Descrição do Problema 
Otimização da Carga de Veículo de Entrega (Logística)  
Diariamente, o centro de distribuição recebe uma lista de pedidos que precisam ser enviados. Cada pedido possui um peso específico (em kg) e uma prioridade associada (urgência ou valor para o cliente). O veículo de entrega tem uma capacidade máxima de carga que não pode ser excedida por razões de segurança e conformidade legal. O desafio é decidir quais pedidos devem ser carregados no veículo hoje de forma que a soma das prioridades dos pedidos escolhidos seja a maior possível, sem ultrapassar o limite de peso do caminhão.

2. Modelagem Formal 
O que é uma solução (Representação):
A solution candidate é representada por um vetor binário $x = [x_1, x_2, \dots, x_n]$, onde $n$ é o total de pedidos disponíveis no dia. Se $x_i = 1$, o pedido $i$ foi selecionado para embarque. Se $x_i = 0$, o pedido $i$ permanece no armazém para o próximo dia.

Qual é o espaço de busca:
Como cada um dos $n$ pedidos pode ter dois estados (embarcado ou não), o espaço total de busca é composto por $2^n$ combinações possíveis. Para apenas 30 pedidos, já existem mais de 1 bilhão de soluções possíveis.

Qual é a função objetivo:
Queremos maximizar a prioridade total dos itens carregados.  
$$\max \sum_{i=1}^{n} (p_i \cdot x_i)$$  
Sendo $p_i$ a prioridade do pedido $i$.

Quais são as restrições:
A soma dos pesos dos pedidos selecionados não pode ultrapassar a capacidade máxima $W$ do veículo. Uma solução torna-se inválida se houver excesso de peso.  
$$\sum_{i=1}^{n} (w_i \cdot x_i) \le W$$  
Sendo $w_i$ o peso do pedido $i$.

3.Classificação do Problema 
**Classificação:** Problema "Difícil" (NP-Difícil).  
**Justificativa:** Este é o tradicional Problema da Mochila Binária (0/1 Knapsack). Ele é considerado NP-Difícil porque não há um algoritmo conhecido que consiga encontrar a solução exata e ótima em tempo polinomial para todos os casos. Como o espaço de busca cresce exponencialmente ($2^n$), tentar resolver o problema verificando todas as combinações por "força bruta" torna-se computacionalmente inviável à medida que a quantidade de pedidos no sistema aumenta.


4- imagem do resultado

<img width="539" height="94" alt="image" src="https://github.com/user-attachments/assets/82a6da54-34f7-4892-a8eb-9e0f762e3e2d" />



