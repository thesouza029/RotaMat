# Infinito, lógica e fundamentos

> Base de conhecimento para RAG. Tema: os limites do que se pode provar e os diferentes tamanhos de infinito.

## Tipos de prova [básico]
- **Prova direta**: parte das hipóteses e chega à conclusão passo a passo.
- **Prova por contradição (absurdo)**: supõe o contrário e chega a uma impossibilidade. Exemplos: irracionalidade de √2 e infinitude dos primos.
- **Indução matemática**: prova que algo vale para n = 1 e que, se vale para n, vale para n + 1. É como derrubar uma fila infinita de dominós.
- **Prova sem palavras**: argumentos visuais que revelam o resultado, como a soma dos n primeiros ímpares ser n², mostrada por quadrados em L.
- Paul Erdős dizia que Deus guarda um "Livro" com as provas perfeitas, e a obra *Proofs from THE BOOK* reúne provas consideradas especialmente elegantes.

## Conjuntos e correspondências [básico a intermediário]
- Dois conjuntos têm o mesmo tamanho (cardinalidade) se existe uma correspondência um a um entre eles.
- Galileu já notava que os quadrados perfeitos podem ser emparelhados com todos os naturais (1↔1, 2↔4, 3↔9...), embora pareçam "menos".

## O Hotel de Hilbert [básico]
- Um hotel com infinitos quartos, todos ocupados, ainda pode receber um novo hóspede: cada pessoa passa do quarto n para o n + 1.
- Também pode receber infinitos novos hóspedes: cada hóspede do quarto n vai para o 2n, liberando todos os quartos ímpares.
- O exemplo ilustra que o infinito não segue a intuição dos números finitos.

## Cantor e os infinitos de tamanhos diferentes [intermediário]
- Georg Cantor mostrou que os números racionais são enumeráveis (tão numerosos quanto os naturais), com cardinalidade ℵ₀ (alef-zero).
- **Argumento diagonal (1891)**: supondo uma lista completa dos números reais entre 0 e 1, constrói-se um número que difere do n-ésimo da lista no n-ésimo dígito. Esse número não está na lista, o que gera contradição. Logo, os reais são não enumeráveis.
- **Teorema de Cantor**: o conjunto das partes de qualquer conjunto é estritamente maior que o conjunto. Assim, existe uma hierarquia infinita de infinitos.
- **Hipótese do Contínuo**: não existe cardinalidade intermediária entre ℵ₀ e a dos reais. Gödel (1940) mostrou que ela não pode ser refutada em ZFC, e Cohen (1963) mostrou que não pode ser provada. Ela é independente dos axiomas usuais.

## Paradoxo de Russell e axiomas [intermediário]
- Em 1901, Bertrand Russell considerou o conjunto de todos os conjuntos que não pertencem a si mesmos. Ele pertence a si mesmo? A pergunta leva a contradição e abalou a teoria ingênua de conjuntos.
- A resposta foi axiomatizar: a teoria de Zermelo-Fraenkel (ZF), geralmente com o **Axioma da Escolha** (ZFC), é a base mais usada da matemática atual.
- O Axioma da Escolha implica resultados contraintuitivos, como o **paradoxo de Banach-Tarski**: uma esfera pode ser decomposta em um número finito de partes que se rearranjam em duas esferas do mesmo tamanho. As partes são conjuntos não mensuráveis e não podem ser construídas fisicamente.

## Programa de Hilbert e os teoremas de Gödel [avançado]
- David Hilbert (início do século XX) propôs formalizar toda a matemática em um sistema completo, consistente e decidível.
- **Primeiro Teorema da Incompletude de Gödel (1931)**: em qualquer sistema formal consistente que expresse a aritmética básica, existem afirmações verdadeiras que não podem ser provadas dentro dele.
- **Segundo Teorema**: tal sistema não pode provar a própria consistência.
- Esses resultados não significam que a matemática seja inconsistente, e sim que nenhum sistema único captura toda a verdade aritmética.

## Computação e o limite do calculável [avançado]
- Alan Turing (1936) definiu um modelo abstrato de computação e provou que o **problema da parada** é indecidível: não existe algoritmo que decida, para todo programa e entrada, se o programa termina.
- A tese de Church-Turing afirma que as funções efetivamente calculáveis são as calculáveis por máquinas de Turing.
- **P versus NP**: pergunta se todo problema cuja solução é verificável rapidamente também é resolvível rapidamente. É um dos Problemas do Milênio.

## Provas assistidas por computador [intermediário a avançado]
- O **Teorema das Quatro Cores** (todo mapa pode ser colorido com 4 cores sem que regiões vizinhas coincidam) foi provado em 1976 por Appel e Haken com ajuda de computador, o que gerou debate sobre o que conta como prova.
- Hoje, assistentes de prova como Lean, Coq e Isabelle verificam formalmente demonstrações. A formalização da prova da conjectura de Kepler (projeto Flyspeck) é um exemplo.

## Visões sobre a natureza da matemática [intermediário]
- **Platonismo**: objetos matemáticos existem independentemente de nós, e descobrimos, não inventamos.
- **Formalismo**: a matemática é a manipulação de símbolos segundo regras.
- **Intuicionismo**: só se aceitam objetos que podem ser construídos, e a lei do terceiro excluído não vale em geral.
- Não há consenso, e a escolha raramente afeta o trabalho diário dos matemáticos.
