LAB 01

Aqui está o log produzido pelo console ao rodar o segundo script do laboratório com os seguintes parâmetros: População de 6, 5 Bits, 8 Gerações e Taxa de Mutação de 0.1.

ALGORITMO GENÉTICO PASSO A PASSO

População inicial: [[1, 0, 1, 0, 0], [0, 0, 1, 1, 1], [1, 1, 0, 0, 1], [0, 1, 0, 1, 0], [1, 1, 1, 0, 0], [0, 0, 0, 1, 1]]

==================== GERAÇÃO 0 ====================
Avaliação dos indivíduos:
  [1, 0, 1, 0, 0] → x=20 → f(x)=400
  [0, 0, 1, 1, 1] → x=7 → f(x)=49
  [1, 1, 0, 0, 1] → x=25 → f(x)=625
  [0, 1, 0, 1, 0] → x=10 → f(x)=100
  [1, 1, 1, 0, 0] → x=28 → f(x)=784
  [0, 0, 0, 1, 1] → x=3 → f(x)=9

 Melhor: x = 28 → f(x) = 784

... [Gerações de 1 a 6 omitidas para brevidade] ...

==================== GERAÇÃO 7 ====================
Avaliação dos indivíduos:
  [1, 1, 1, 1, 1] → x=31 → f(x)=961
  [1, 1, 1, 1, 1] → x=31 → f(x)=961
  [1, 1, 1, 0, 1] → x=29 → f(x)=841
  [1, 1, 1, 1, 1] → x=31 → f(x)=961
  [1, 1, 1, 1, 0] → x=30 → f(x)=900
  [1, 1, 1, 1, 1] → x=31 → f(x)=961

 Melhor: x = 31 → f(x) = 961

==================================================
RESULTADO FINAL
==================================================

Melhor indivíduo: [1, 1, 1, 1, 1]
x = 31
f(x) = 961

Ótimo global: x = 31, f(x) = 961
Erro: 0


Ao analisar este segundo código, percebemos diferenças fundamentais na modelagem e no comportamento do algoritmo em relação ao problema OneMax:

- Espaço de Busca Reduzido: O algoritmo encontrou a solução ótima (31) rapidamente mesmo com uma população pequena (6 indivíduos), devido ao pequeno espaço de busca: com apenas cinco bits existem $2^5 = 32$ soluções. Em aplicações reais e complexas como as rotinas logísticas em sistemas como o TOTVS Protheus, um espaço de apenas trinta e duas variáveis é resolvido rapidamente, mas ainda assim serve para ilustrar a lógica de otimização em cenários mais extensos.
- Seleção por Roleta:Diferente do código anterior que utilizava torneio para seleção. Neste exemplo é usada a roleta. Como a função objetivo é $f(x) = x^2$, as diferenças no valor de fitness são acentuadas. Um indivíduo com $x=30$ possui um fitness de novecentos enquanto um com $x=10$ possui cem. Na roleta o indivíduo com $x=30$ tem uma chance muito maior de ser escolhido o que acelera a convergência da solução.
- Mapeamento Genótipo-Fenótipo: Destacamos a clara distinção entre o cromossomo (lista binária) e o fenótipo (valor decimal real). A função `binario_para_decimal` atua como o tradutor que permite calcular o fitness matemático a partir dos dados genéticos.
- Elitismo Focado: O algoritmo preserva apenas o melhor indivíduo (`nov


LINK 1 -> <img width="1008" height="503" alt="image" src="https://github.com/user-attachments/assets/e3eb0d6a-8469-4b47-8b43-8e91c4a6f78e" />
LINK 2 -> <img width="525" height="202" alt="image" src="https://github.com/user-attachments/assets/8fe0b885-112a-4475-934d-569a3ae4cb18" />
LINK 3 -> <img width="561" height="393" alt="image" src="https://github.com/user-attachments/assets/48526244-1075-4df7-a07f-ede23f932239" />
LINK 4 -> <img width="551" height="427" alt="image" src="https://github.com/user-attachments/assets/b4b24181-5b51-47d9-bea2-88fbc5812eff" />
LINK 5 -> <img width="685" height="378" alt="image" src="https://github.com/user-attachments/assets/0b7e3c32-2354-4095-a35c-54fca8ecfdfa" />
LINK 6 -> <img width="773" height="355" alt="image" src="https://github.com/user-attachments/assets/458a9a02-54e1-4bd1-8d9f-95ad6112bd17" />





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

       
