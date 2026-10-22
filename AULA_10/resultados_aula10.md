<img width="740" height="660" alt="image" src="https://github.com/user-attachments/assets/57dc650b-2ef6-4ee7-833a-b4eb132b0de7" />

1.

**A) Por que o método do Centroide com triângulos não atinge matematicamente os extremos 0% e 100%?**
O Centroide calcula o "centro de massa" da figura geométrica. Como os triângulos possuem uma base, o peso dessa área "puxa" o centro de gravidade para o meio do gráfico. Por isso, o valor chega perto das bordas, mas nunca atinge exatamente 0 ou 100.

**B) O que acontece com o resultado final se alterarmos a função da Urgência Crítica para Trapézio (trapmf)?**
O resultado chega mais perto de 100% (sobe de 87.5% para cerca de 95%). Como o trapézio é "quadrado" no topo, ele adiciona mais peso na ponta, empurrando o centroide mais para a direita. Porém, ainda não crava em 100% por conta da sua rampa lateral.

**C) O que acontece se usarmos 'MOM' (Mean of Maximum)? Qual é recomendável e por quê?**
O método MOM atinge exatamente 0% e 100%, pois ele considera apenas o topo absoluto do gráfico e ignora o resto da área.
**Recomendação:** O **Centroide** ainda é muito melhor. O Centroide garante que as mudanças na resposta sejam graduais e suaves. O método MOM gera "degraus" (saltos bruscos) que deixam o sistema instável e imprevisível.

---

## 2. Matriz de Regras (3x3)

| Impacto \ Explorabilidade | Baixa (0-4)      | Moderada (2-8)   | Alta (6-10)      |
|---------------------------|------------------|------------------|------------------|
| **Baixo (0-40)**          | Urgência Baixa   | Urgência Baixa   | Urgência Média   |
| **Médio (20-80)**         | Urgência Média   | Urgência Alta    | Urgência Alta    |
| **Alto (60-100)**         | Urgência Crítica | Urgência Crítica | Urgência Crítica |

---

## 3. Análise da Superfície de Decisão 3D

O gráfico 3D comprova o funcionamento correto das regras e do motor Mamdani:
1. **Suavidade (Centroide):** O gráfico tem inclinações suaves, sem degraus bruscos, provando que o Centroide faz transições graduais entre as regras.
2. **Platô de Criticidade:** Quando o Impacto passa de 60 (Alto), a superfície atinge a altura máxima rapidamente (vermelho escuro). Isso mostra que, com impacto alto, a urgência será sempre crítica.
3. **Limitação nas Bordas:** Olhando o gráfico pelas laterais, é possível ver que a base não encosta perfeitamente no 0% e o topo não toca exatamente a linha dos 100%, ilustrando o problema do centroide nas pontas.
