# Probabilidade, estatística, caos e fractais

> Base de conhecimento para RAG. Tema: a matemática do acaso, da incerteza e dos padrões complexos.

## Contagem e combinatória [básico]
- **Princípio multiplicativo**: se há m maneiras de fazer uma escolha e n de fazer outra, há m·n maneiras de fazer as duas.
- **Permutações** de n objetos: n! maneiras.
- **Combinações**: C(n, k) = n! / (k!(n−k)!), o número de subconjuntos de k elementos em n.
- **Triângulo de Pascal**: cada número é a soma dos dois acima. As linhas contêm os coeficientes do binômio, somam potências de 2 e, quando se pintam os números ímpares, revelam o triângulo de Sierpinski.
- **Princípio da casa dos pombos**: se n + 1 pombos ocupam n casas, alguma casa tem ao menos dois pombos. Ele prova, por exemplo, que em qualquer cidade suficientemente grande existem duas pessoas com o mesmo número de fios de cabelo.

## Probabilidade básica [básico]
- A probabilidade de um evento é um número entre 0 e 1: casos favoráveis dividido por casos possíveis (quando igualmente prováveis).
- Eventos independentes: P(A e B) = P(A)·P(B).
- **Valor esperado**: média ponderada dos resultados possíveis. Loterias têm valor esperado negativo para o apostador.
- **Falácia do apostador**: após dez caras seguidas em uma moeda justa, a próxima jogada continua com 50% de chance de cara.

## Problemas que enganam a intuição [básico a intermediário]
- **Problema do aniversário**: em um grupo de apenas 23 pessoas, a chance de duas fazerem aniversário no mesmo dia passa de 50%. Em 70 pessoas, supera 99%.
- **Problema de Monty Hall**: em um jogo com três portas (um prêmio e duas cabras), depois que o apresentador, que sabe onde está o prêmio, abre uma porta com cabra, trocar de porta dá 2/3 de chance de ganhar, e manter, 1/3.
- **Paradoxo dos falsos positivos**: um teste com 99% de acerto para uma doença que afeta 1 em 1.000 pessoas pode ter, quando positivo, apenas cerca de 9% de chance de a pessoa estar doente. Isso é explicado pelo Teorema de Bayes.

## Teorema de Bayes [intermediário]
- P(A | B) = P(B | A) · P(A) / P(B). Permite atualizar crenças à luz de novas evidências.
- Aplicações: diagnóstico médico, filtros de spam, ciência de dados, raciocínio científico e aprendizado de máquina.

## Lei dos grandes números e Teorema Central do Limite [intermediário]
- **Lei dos Grandes Números**: a média de muitas repetições independentes se aproxima do valor esperado.
- **Teorema Central do Limite**: a soma (ou média) de muitas variáveis independentes, com variância finita, tende a uma distribuição normal (curva em sino), independentemente da forma original. Isso explica por que a curva normal aparece tanto na natureza e na estatística.
- Desvio padrão mede a dispersão dos dados. Em uma normal, cerca de 68% dos valores ficam a 1 desvio da média, 95% a 2 e 99,7% a 3.

## Curiosidades estatísticas [intermediário]
- **Lei de Benford**: em muitos conjuntos de dados reais, o dígito inicial 1 aparece cerca de 30% das vezes, e o 9, menos de 5%. É usada em auditorias para detectar fraudes.
- **Passeio aleatório**: o matemático George Pólya mostrou que, em uma e duas dimensões, o caminhante aleatório volta à origem com probabilidade 1. Em três dimensões, não necessariamente. Em tom de brincadeira: "um bêbado encontra o caminho de casa, mas um pássaro bêbado pode se perder para sempre".
- **Correlação não implica causalidade**: duas séries podem variar juntas por acaso ou por um fator comum.

## Teoria dos jogos [intermediário a avançado]
- Estuda decisões estratégicas. O **Dilema do Prisioneiro** mostra que escolhas racionais individuais podem levar a um resultado pior para todos.
- O **equilíbrio de Nash** é uma situação em que nenhum jogador ganha mudando sozinho de estratégia.

## Caos [intermediário a avançado]
- Um sistema caótico é determinístico, mas sensível às condições iniciais: pequenas diferenças crescem exponencialmente.
- **Edward Lorenz (1963)**, estudando um modelo simplificado de convecção atmosférica, observou que arredondar um número alterava totalmente a previsão. Surgiu o "efeito borboleta" e o **atrator de Lorenz**, uma figura com duas asas.
- **Mapa logístico** x → r·x·(1 − x): para r pequeno, a população se estabiliza. Com o aumento de r, surgem ciclos de período 2, 4, 8... (duplicação de período) até o caos em torno de r ≈ 3,57. A razão entre intervalos sucessivos converge para a **constante de Feigenbaum**, cerca de 4,669, comum a muitos sistemas diferentes.
- Previsão do tempo de longo prazo é limitada por essa sensibilidade, não por falta de equações.

## Fractais [intermediário]
- Fractal é uma forma com estrutura em todas as escalas, frequentemente autossimilar. O termo foi criado por Benoît Mandelbrot em 1975.
- **Conjunto de Mandelbrot**: o conjunto dos números complexos c para os quais a iteração z → z² + c, começando em 0, não diverge. Uma regra de uma linha gera uma figura de complexidade infinita.
- **Triângulo de Sierpinski**: dimensão de cerca de 1,585 (log 3 / log 2).
- **Curva de Koch**: dimensão de cerca de 1,262 (log 4 / log 3), com perímetro infinito.
- **Paradoxo da costa**: o comprimento da costa de um país depende da régua usada, e cresce conforme a escala diminui.
- Fractais aparecem em samambaias, brócolis romanesco, relâmpagos, redes de rios, pulmões e vasos sanguíneos, e são usados em gráficos computacionais e antenas compactas.
