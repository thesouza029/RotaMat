# Álgebra e estruturas

> Base de conhecimento para RAG. Tema: de equações simples a grupos, corpos e álgebra linear.

## O que é álgebra [básico]
- A palavra vem de *al-jabr*, do livro de Al-Khwarizmi (século IX), sobre resolver equações movendo termos de um lado para outro.
- A ideia central é usar símbolos para representar números desconhecidos e estudar relações gerais, não casos isolados.
- A palavra "algoritmo" também vem do nome latinizado de Al-Khwarizmi.

## Equações de primeiro e segundo graus [básico]
- Equação linear: ax + b = 0 tem solução x = −b/a (se a ≠ 0).
- Equação quadrática: ax² + bx + c = 0 tem soluções x = (−b ± √(b² − 4ac)) / (2a).
- O discriminante Δ = b² − 4ac indica o número de raízes reais: duas se Δ > 0, uma se Δ = 0, nenhuma real se Δ < 0.
- No Brasil, a fórmula é chamada de "fórmula de Bhaskara", nome pouco usado em outros países. Métodos para resolver quadráticas são anteriores ao matemático Bhaskara II (século XII).
- A parábola y = ax² + bx + c tem vértice em x = −b/(2a).

## Números complexos nascem da álgebra [intermediário]
- No século XVI, Cardano, Tartaglia e Bombelli resolveram equações cúbicas. A fórmula às vezes exigia raízes quadradas de números negativos, mesmo quando as três raízes finais eram reais.
- Bombelli tratou essas quantidades como números válidos. Assim nasceram os números imaginários.
- Os números complexos têm a forma a + bi. No plano complexo (plano de Argand-Gauss), a multiplicação combina escala e rotação.
- **Teorema Fundamental da Álgebra**: todo polinômio não constante com coeficientes complexos tem pelo menos uma raiz complexa. Um polinômio de grau n tem exatamente n raízes, contadas com multiplicidade.

## Polinômios e a impossibilidade da quíntica [avançado]
- Existem fórmulas por radicais para equações de grau 2, 3 e 4.
- Abel e Ruffini mostraram que não existe fórmula geral por radicais para o grau 5. Évariste Galois (1811–1832) explicou o porquê usando grupos de simetria das raízes. Galois morreu em um duelo, com 20 anos, após deixar suas ideias em cartas.
- A **Teoria de Galois** relaciona a solubilidade de equações à estrutura de grupos, um dos grandes triunfos da matemática abstrata.

## Grupos [intermediário a avançado]
- Um grupo é um conjunto com uma operação que satisfaz fechamento, associatividade, elemento neutro e inverso.
- Exemplos: os inteiros com soma; as rotações de um quadrado; as permutações de n objetos.
- O **grupo do Cubo de Rubik** tem 43.252.003.274.489.856.000 posições (cerca de 4,3 × 10^19), e a matemática de grupos mostra por que algumas configurações são inalcançáveis sem desmontar o cubo.
- A **classificação dos grupos finitos simples** é uma das maiores demonstrações coletivas, espalhada por milhares de páginas e dezenas de autores.
- O **Grupo Monstro** é o maior grupo simples esporádico, com ordem de cerca de 8 × 10^53. A ligação inesperada com funções modulares ficou conhecida como "monstrous moonshine".

## Anéis e corpos [avançado]
- Um anel tem soma e produto (por exemplo, os inteiros e os polinômios).
- Um corpo é um anel em que se pode dividir por qualquer elemento diferente de zero (racionais, reais, complexos).
- Existem corpos finitos, como os inteiros módulo um primo p, fundamentais na criptografia e em códigos corretores de erros.

## Aritmética modular [básico a intermediário]
- Em "aritmética do relógio", números são considerados equivalentes se deixam o mesmo resto. Em módulo 12, 14 equivale a 2.
- O **Pequeno Teorema de Fermat**: se p é primo e a não é múltiplo de p, então a^(p−1) ≡ 1 (mod p).
- Aplicação: o **RSA** (1977, Rivest, Shamir e Adleman) usa a dificuldade de fatorar o produto de dois primos grandes para proteger comunicações.

## Álgebra linear [intermediário]
- Estuda vetores, matrizes e transformações lineares. Uma matriz pode girar, esticar ou projetar o espaço.
- O **determinante** mede o fator de mudança de área ou volume.
- **Autovalores e autovetores** revelam as direções que uma transformação apenas estica. Eles aparecem em vibração de estruturas, mecânica quântica, componentes principais em estatística e no algoritmo PageRank do Google.
- A **decomposição em valores singulares (SVD)** é usada em compressão de imagens e sistemas de recomendação.
- Redes neurais e aprendizado de máquina dependem fortemente de multiplicação de matrizes.

## Frase para guardar
- A álgebra moderna deixa de perguntar "qual é o valor de x?" e passa a perguntar "qual é a estrutura que torna essa resposta possível?".
