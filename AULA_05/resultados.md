Missão 01

<img width="1205" height="605" alt="image" src="https://github.com/user-attachments/assets/04862334-a8b4-4972-abcb-dbbe64f89d82" />

<img width="1212" height="498" alt="image" src="https://github.com/user-attachments/assets/071cd6e6-662b-40ce-b987-7daf689059bf" />

Missão 02

<img width="1404" height="708" alt="image" src="https://github.com/user-attachments/assets/0dcfecd7-8d93-4c23-8434-553d0d99c44c" />

Missão 03

<img width="1406" height="432" alt="image" src="https://github.com/user-attachments/assets/2eaacb14-70e4-4e53-91a9-68512f9d0093" />

<img width="1443" height="502" alt="image" src="https://github.com/user-attachments/assets/322fbacd-a094-4fac-a403-61b7d593644a" />

Missão 04

<img width="1433" height="702" alt="image" src="https://github.com/user-attachments/assets/d4ca8c38-c9e3-48d9-bb7a-09e676f70b34" />

<img width="1410" height="737" alt="image" src="https://github.com/user-attachments/assets/d188e28f-66e0-4d9f-b258-c97020035992" />


<img width="1429" height="172" alt="image" src="https://github.com/user-attachments/assets/18c47ae2-4f7a-4663-a3e8-90a5a275d4f4" />


# RELATÓRIO FINAL PSO

---

## PARTE 1: O QUE VOCÊ APRENDEU?

### 1. Explique com suas palavras o que é o PSO e como ele funciona.
O PSO é um algoritmo de otimização estocástico inspirado no comportamento social e coletivo de grupos de animais, como bandos de pássaros e cardumes de peixes. Ele funciona espalhando diversas soluções candidatas em um espaço de busca multidimensional. 

A cada iteração, cada partícula atualiza sua posição com base em uma velocidade que combina três componentes:
Inércia: A tendência de manter a direção de movimento atual.
Componente Cognitivo: A atração em direção à melhor posição que a própria partícula já encontrou (*pBest*).
Componente Social: A atração em direção à melhor posição encontrada por qualquer partícula de todo o enxame (*gBest*).

---

### 2. Qual a diferença entre pBest e gBest? Por que ambos são importantes?
Personal Best (pBest): É o melhor ponto individual alcançado por uma partícula específica.
Global Best (gBest): É o melhor ponto alcançado pelo enxame todo.

**Por que ambos são importantes?**
O pBest promove a exploração, dando autonomia para que as partículas investiguem regiões distintas do espaço de busca sem se concentrarem imediatamente no mesmo lugar.
* O gBest promove a convergência/cooperação, guiando todo o grupo em direção à região globalmente mais promissora. O equilíbrio entre esses dois conceitos é o que evita que o algoritmo fique preso em mínimos locais.

---

## PARTE 2: SUA EXPERIÊNCIA COM AS MISSÕES

### Missão 1 - A Partícula Solitária:
* A partícula encontrou o mínimo? ( X ) Sim ( ) Não
* Quantas iterações foram necessárias? 20
* Dificuldade: ( X ) Fácil ( ) Médio ( ) Difícil

---

### Missão 2 - O Enxame:
* O enxame encontrou o mínimo global? ( X ) Sim ( ) Não
* Compare com a Missão 1: O enxame foi mais rápido? ( X ) Sim ( ) Não
* Dificuldade: ( ) Fácil ( X ) Médio ( ) Difícil

---

### Missão 3 - Problema Corporativo:
Compare com o custo inicial: Melhorou? ( X ) Sim ( ) Não
Quantos centros foram alocados? 5
Dificuldade: ( ) Fácil ( X ) Médio ( ) Difícil

---

### Missão 4 - Otimização de Parâmetros:
Melhor configuração encontrada:w = 0.7, c1 = 1.8, c2 = 1.8, partículas = 60
Pior configuração encontrada: w = 0.5, c1 = 1.8, c2 = 1.8, partículas = 30
Dificuldade: ( ) Fácil ( X ) Médio ( ) Difícil
