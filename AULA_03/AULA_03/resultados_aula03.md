











































======================================================================================================

LAB 02


Problema:OneMax 

1. Saída da Execução Padrão

A seguir está o log gerado pelo console ao executar o arquivo `lab02_aula03_CIAO.py` com as configurações iniciais (Tamanho=20, População=30, Gerações=50, Crossover=0.85, Mutação=0.02, Elite=2):

ONEMAX - AG com 30 indivíduos, 50 gerações

Geração   0: Melhor = 14/20, Média = 10.13  
Geração  10: Melhor = 18/20, Média = 16.47  
Geração  20: Melhor = 20/20, Média = 18.90  
Geração  30: Melhor = 20/20, Média = 19.33  
Geração  40: Melhor = 20/20, Média = 19.67  

MELHOR FITNESS: 20/20  
Ótimo = 20 (todos os bits são 1)

DESAFIO: Mude os parâmetros e veja o que acontece!

1. Aumente a TAXA_MUT para 0.1. O que acontece?  
2. Diminua POPULACAO para 10. O que acontece?  
3. Aumente GERACOES para 100. O que acontece?  
4. Mude ELITE para 0. O que acontece?  

Além dos resultados no console, o script gerou um gráfico mostrando a curva de convergência, onde a linha do "Melhor" atinge rapidamente o topo (20), e a linha da "Média" sobe gradualmente, aproximando-se do topo.


2. Considerações sobre os Resultados

Baseando-nos na execução do algoritmo com os parâmetros padrão, extraímos as seguintes observações sobre o comportamento do Algoritmo Genético (AG):

Estado Inicial: Na Geração 0, como os indivíduos são gerados aleatoriamente, a média de *fitness* da população fica próxima a 10 (metade de 20), o que é estatisticamente esperado para um vetor de bits aleatórios com probabilidade de 50% para cada valor.
  
Velocidade de Convergência: Com esses parâmetros, o algoritmo foi bastante eficiente. Em torno de 20 gerações, ele já alcançou a solução ótima (20/20). Isso se deve à pressão seletiva (torneio) combinada com a alta taxa de crossover (85%), que rapidamente integra as características favoráveis dos indivíduos.

O Papel do Elitismo: Manter os dois melhores indivíduos (Elite=2) garantiu que a linha do "Melhor indivíduo" não caísse. Uma vez que o algoritmo encontrou o máximo de 20/20, ele permaneceu inalterado, mesmo com mutações ocorrendo nas descêndias.

Por que a Média não atinge exatamente 20: Apesar do melhor indivíduo alcançar seu máximo, a média da população estabiliza perto de 19.5 e raramente chega a 20. Isso pode ser atribuído à **Mutação (2%)**: em cada nova geração, alguns bits são inevitavelmente revertidos (de 1 para 0), criando indivíduos ligeiramente piores e ligeiramente reduzindo a média. Este fenômeno é positivo, pois assegura a preservação da diversidade genética.

LINK PARA O GRÁFICO ---> <img width="1192" height="393" alt="image" src="https://github.com/user-attachments/assets/9a3ecb0b-dfdd-4641-921e-66c327b9cdea" />

       
