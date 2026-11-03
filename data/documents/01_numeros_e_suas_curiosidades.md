# Números e suas curiosidades

> Base de conhecimento para RAG. Tema: a beleza dos números, de contar nos dedos até a identidade de Euler.
> Cada seção indica o nível: **[básico]**, **[intermediário]** ou **[avançado]**.

## Contar e o nascimento do zero [básico]
- Os números naturais (1, 2, 3, ...) nasceram da necessidade de contar objetos, dias e rebanhos.
- O zero como número, e não apenas como espaço vazio, foi formalizado na Índia. O matemático Brahmagupta (século VII) descreveu regras de operação com o zero.
- O sistema posicional indo-arábico (0 a 9) permitiu cálculos muito mais simples que os algarismos romanos.

## Números primos [básico a intermediário]
- Um número primo é maior que 1 e só é divisível por 1 e por ele mesmo: 2, 3, 5, 7, 11, 13...
- O 2 é o único primo par.
- **Teorema Fundamental da Aritmética**: todo número natural maior que 1 se escreve de forma única como produto de primos (ignorando a ordem). Os primos são os "átomos" dos números.
- **Infinitude dos primos (Euclides, cerca de 300 a.C.)**: suponha que existe uma lista finita de todos os primos. Multiplique todos e some 1. O resultado deixa resto 1 na divisão por cada primo da lista, então ele é primo ou tem um fator primo fora da lista. Isso contradiz a hipótese. Logo, existem infinitos primos.
- **Crivo de Eratóstenes**: método para listar primos riscando os múltiplos de cada primo encontrado.
- **Teorema dos Números Primos**: a quantidade de primos até x é aproximadamente x / ln(x). Os primos parecem aleatórios, mas obedecem a uma lei estatística precisa.
- Problemas abertos: a conjectura dos primos gêmeos (infinitos pares de primos com diferença 2) e a conjectura de Goldbach (todo par maior que 2 é soma de dois primos).
- Os maiores primos conhecidos são primos de Mersenne (da forma 2^p − 1) e são encontrados por busca computacional distribuída. O recorde conhecido muda com o tempo.

## Racionais, irracionais e a surpresa de 0,999... [básico]
- Um número racional é uma fração de inteiros. Um irracional não pode ser escrito assim.
- **√2 é irracional**: se √2 = a/b em fração irredutível, então a² = 2b², logo a é par, depois b também seria par, contradição. Essa prova por absurdo é atribuída à tradição pitagórica.
- 0,999... = 1: se x = 0,999..., então 10x = 9,999..., e subtraindo, 9x = 9, logo x = 1.
- Entre dois racionais quaisquer há sempre outro racional e também um irracional (densidade).

## Constantes famosas [básico a intermediário]
- **π (pi) ≈ 3,14159**: razão entre a circunferência e o diâmetro. É irracional (Lambert, 1761) e transcendente (Lindemann, 1882), o que prova que "quadrar o círculo" com régua e compasso é impossível.
- **e ≈ 2,71828**: base do logaritmo natural, limite de (1 + 1/n)^n quando n cresce. É a base do crescimento contínuo e transcendente (Hermite, 1873).
- **φ (razão áurea) ≈ 1,6180339887**: φ = (1 + √5) / 2, solução positiva de x² = x + 1.
- **i**: unidade imaginária, definida por i² = −1.
- **γ (Euler-Mascheroni) ≈ 0,5772**: aparece na diferença entre a série harmônica e o logaritmo. Não se sabe se é irracional.

## A identidade de Euler [intermediário]
- e^(iπ) + 1 = 0 relaciona cinco constantes fundamentais (0, 1, e, i, π) com adição, multiplicação e exponenciação.
- Ela vem da fórmula de Euler, e^(iθ) = cos θ + i sen θ, que liga exponencial e trigonometria. Em θ = π, o resultado é −1.
- Muitos matemáticos a citam como exemplo de beleza por reunir ideias de áreas diferentes em uma frase curta.

## Sequência de Fibonacci [básico a intermediário]
- 1, 1, 2, 3, 5, 8, 13, 21, 34, 55... Cada termo é a soma dos dois anteriores.
- A razão entre termos consecutivos converge para φ.
- A fórmula de Binet dá o n-ésimo termo diretamente usando φ.
- Aparece na filotaxia (arranjo de folhas e sementes): girassóis costumam ter espirais em números de Fibonacci consecutivos, como 34 e 55, e o "ângulo de ouro" é de cerca de 137,5°.
- Propriedade curiosa: o máximo divisor comum de F(m) e F(n) é F(mdc(m, n)).

## Números com personalidade [básico]
- **Perfeitos**: iguais à soma dos seus divisores próprios. 6 = 1 + 2 + 3; 28; 496; 8128. Euclides ligou os perfeitos pares aos primos de Mersenne. Não se sabe se existe um perfeito ímpar.
- **Amigáveis**: 220 e 284. A soma dos divisores próprios de um é o outro.
- **Triangulares**: 1, 3, 6, 10, 15... Gauss, segundo a anedota, somou de 1 a 100 em segundos ao notar que 50 pares somam 101, resultando em 5.050.
- **1729**: o número do táxi de Ramanujan, o menor número que é soma de dois cubos de duas maneiras: 1³ + 12³ e 9³ + 10³.
- **142857**: 1/7 = 0,142857142857... e multiplicar por 2, 3, 4, 5 ou 6 apenas rearranja os mesmos dígitos de forma cíclica.

## Desafios com resposta
- Qual é o menor número que tem exatamente 6 divisores? Resposta: 12 (1, 2, 3, 4, 6, 12).
- Quantos zeros tem 100! no final? Resposta: 24 (conte os fatores 5: 20 + 4).
- Prove que a soma de dois ímpares é par. Resposta: (2a+1) + (2b+1) = 2(a+b+1).
