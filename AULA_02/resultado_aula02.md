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
