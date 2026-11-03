# Cálculo e análise

> Base de conhecimento para RAG. Tema: a matemática da mudança, do infinitamente pequeno ao infinitamente grande.

## A ideia central [básico]
- O cálculo estuda como as coisas mudam (derivadas) e como se acumulam (integrais).
- Foi desenvolvido de forma independente por Isaac Newton e Gottfried Leibniz no fim do século XVII, com disputa de prioridade. A notação de Leibniz (dy/dx e ∫) é a mais usada até hoje.

## Limites [básico a intermediário]
- O limite descreve para onde uma expressão se aproxima, mesmo sem alcançar. Exemplo: 1/n tende a 0 quando n cresce.
- Os limites resolvem os paradoxos de Zenão: a soma 1/2 + 1/4 + 1/8 + ... converge para 1.
- Nos anos 1800, Cauchy e Weierstrass deram ao cálculo uma base rigorosa com a definição épsilon-delta.

## Derivada [básico a intermediário]
- A derivada de uma função em um ponto é a inclinação da reta tangente e também a taxa de variação instantânea. Se s(t) é a posição, s'(t) é a velocidade e s''(t) é a aceleração.
- Regras básicas: derivada de x^n é n·x^(n−1); (sen x)' = cos x; (e^x)' = e^x.
- A função e^x é a única, a menos de um fator constante, que é igual à própria derivada. Por isso ela modela crescimento proporcional ao tamanho atual.
- Aplicações: otimização (máximos e mínimos), física, economia e aprendizado de máquina (descida do gradiente).

## Integral [básico a intermediário]
- A integral definida mede a área sob uma curva como limite de somas de retângulos finos.
- **Teorema Fundamental do Cálculo**: derivar e integrar são operações inversas. Se F' = f, então a integral de f entre a e b é F(b) − F(a).
- Esse teorema transformou o cálculo de áreas, antes um trabalho árduo, em um procedimento algébrico.

## Séries infinitas [intermediário]
- A série geométrica 1 + r + r² + ... converge para 1/(1 − r) quando |r| < 1.
- A série harmônica 1 + 1/2 + 1/3 + ... diverge, ainda que os termos tendam a zero, embora cresça muito devagar.
- **Problema de Basel**: a soma dos inversos dos quadrados (1 + 1/4 + 1/9 + ...) é π²/6, resultado de Euler (1734). O fato de π aparecer em uma soma sem relação aparente com círculos é um exemplo clássico de beleza matemática.
- **Série de Taylor**: funções suaves podem ser escritas como somas infinitas de potências. Por exemplo, e^x = 1 + x + x²/2! + x³/3! + ...
- Calculadoras e computadores usam aproximações desse tipo para calcular seno, cosseno e exponenciais.

## Paradoxos geométricos do infinito [intermediário]
- O **floco de neve de Koch** tem área finita e perímetro infinito.
- O **chifre de Gabriel** (sólido de revolução de 1/x para x ≥ 1) tem volume finito (π) e área de superfície infinita.
- A **integral gaussiana**: a integral de e^(−x²) sobre toda a reta vale √π, base da curva normal em estatística.

## Cálculo das variações: a curva mais rápida [avançado]
- O **problema da braquistócrona** (Johann Bernoulli, 1696) pergunta qual a curva de descida mais rápida entre dois pontos sob a gravidade. A resposta não é a reta, e sim um arco de cicloide.
- O **princípio da mínima ação** e o cálculo variacional ligam esse tipo de problema à física: muitos sistemas seguem caminhos que tornam uma quantidade (a ação) estacionária.

## Séries de Fourier e a decomposição em ondas [intermediário a avançado]
- Fourier mostrou que funções periódicas (sob condições razoáveis) podem ser expressas como somas de senos e cossenos.
- A transformada de Fourier decompõe sinais em frequências. É usada em áudio, compressão de imagens JPEG, telecomunicações e imagens médicas.
- Música e matemática: um timbre é a combinação de harmônicos, e a transformada revela quais estão presentes.

## Equações diferenciais [intermediário a avançado]
- Relacionam uma função com suas derivadas. Modelam populações, circuitos, epidemias, vibrações e o movimento dos planetas.
- Equação do crescimento: dy/dt = ky tem solução y = y₀·e^(kt).
- Equações famosas: a do calor, a das ondas, as de Maxwell e as de Navier-Stokes. A existência e a suavidade das soluções de Navier-Stokes em 3D é um dos Problemas do Milênio.

## Análise complexa [avançado]
- Estuda funções de variável complexa. Uma função derivável no sentido complexo é muito mais rígida do que no caso real: é automaticamente infinitamente derivável e igual à sua série de Taylor localmente.
- O **teorema dos resíduos** permite calcular integrais reais difíceis por caminhos no plano complexo.
- A **função zeta de Riemann** liga números primos a análise complexa. A **Hipótese de Riemann**, que afirma que os zeros não triviais têm parte real 1/2, segue em aberto.

## Dica de intuição
- Derivada: "como está mudando agora?". Integral: "quanto se acumulou?". O Teorema Fundamental diz que essas duas perguntas são lados da mesma moeda.
