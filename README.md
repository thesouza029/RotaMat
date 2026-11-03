# 📐 Rota Mat — professor de Matemática com IA

[![CI](https://github.com/IgorSasaki/minicurso-ia-node-ifsp/actions/workflows/ci.yml/badge.svg)](https://github.com/IgorSasaki/minicurso-ia-node-ifsp/actions/workflows/ci.yml)
![Node.js 22+](https://img.shields.io/badge/node-%3E%3D22-339933?logo=node.js&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-strict-3178C6?logo=typescript&logoColor=white)

Uma API em **Node.js + TypeScript** que vai além do "chat com IA": integra o **Google Gemini** a uma aplicação de verdade, com a persona de um **professor de Matemática com doutorado (PhD)** que ensina estudantes do **ensino médio**. São três recursos.

| Recurso | Rota | O que demonstra |
|---|---|---|
| 💬 **Professor de Matemática** | `POST /chat` e `POST /chat/stream` | Persona via *system prompt*, histórico de conversa, streaming cancelável |
| 🧑‍🏫 **Aula em JSON** | `POST /career-plan` | Saída estruturada com JSON Schema + validação com **zod** |
| 📚 **Perguntas aos documentos (RAG)** | `POST /ask` | Embeddings, busca semântica e respostas **com citação de fonte** |

O professor não entrega só a resposta: começa pela **intuição**, explica o porquê, mostra um **exemplo resolvido**, avisa dos **erros comuns** e devolve um exercício para o estudante tentar.

O RAG consulta documentos que o modelo nunca viu: **7 arquivos sobre a beleza da Matemática**, de números e geometria até cálculo, infinito, probabilidade, caos e problemas abertos, com seções marcadas por nível (**[básico]**, **[intermediário]** e **[avançado]**).

![Pergunta de Matemática respondida com fontes](docs/img/shot-ask.png)

<details>
<summary>📸 Mais telas</summary>

| Aula (JSON → interface) | Chat com streaming |
|---|---|
| ![Aula](docs/img/shot-career-plan.png) | ![Chat](docs/img/shot-chat.png) |

| Tema claro | Celular |
|---|---|
| ![Tema claro](docs/img/shot-light.png) | <img src="docs/img/shot-mobile.png" alt="Versão para celular" width="260"> |

</details>

---

## Começando em 3 minutos

### Opção 1 — GitHub Codespaces (recomendado para a aula)
Nada para instalar: clique no botão **Open in GitHub Codespaces** acima. As dependências são instaladas sozinhas e o arquivo `.env` é criado automaticamente.

### Opção 2 — Na sua máquina
Pré-requisitos: **Node.js 22+** e **pnpm** (`corepack enable` já instala a versão certa).

```bash
git clone https://github.com/IgorSasaki/minicurso-ia-node-ifsp.git
cd minicurso-ia-node-ifsp
pnpm install
cp .env.example .env
```

### Configure a chave do Gemini
1. Crie uma chave gratuita em <https://aistudio.google.com/apikey> (conta Google, **sem cartão de crédito**).
2. Cole no `.env`:
   ```env
   GEMINI_API_KEY=sua_chave_aqui
   ```

> ⚠️ Os termos de uso da API do Gemini exigem **18 anos ou mais**. Na aula, quem é menor de idade faz em dupla com um colega maior.
> 🔒 A chave é uma senha: o `.env` está no `.gitignore` e nunca deve ir para o GitHub.

### Rode
```bash
pnpm hello    # etapa 1: primeira chamada ao Gemini no terminal
pnpm ingest   # gera o índice vetorial a partir de data/documents/
pnpm dev      # API + front-end em http://localhost:3333
pnpm check    # tipos + lint + testes
```

---

## As etapas do minicurso

Cada etapa é um commit com uma **tag git**. Ficou para trás? Pule direto para o código pronto:

```bash
git checkout etapa-03   # código pronto da etapa 3
git checkout main       # versão final
```

| Tag | Etapa | Conceitos | Guia |
|---|---|---|---|
| `etapa-01` | Primeira chamada à LLM | tokens, `systemInstruction`, temperatura | [📄](docs/steps/01-first-call.md) |
| `etapa-02` | API `/chat` com persona | Fastify, validação com zod, erros centralizados | [📄](docs/steps/02-chat-api.md) |
| `etapa-03` | JSON estruturado `/career-plan` | `responseJsonSchema`, schema como contrato | [📄](docs/steps/03-structured-output.md) |
| `etapa-04` | Embeddings e similaridade | vetores, similaridade de cosseno | [📄](docs/steps/04-embeddings.md) |
| `etapa-05` | Ingestão de documentos | chunking, sobreposição, índice vetorial | [📄](docs/steps/05-ingestion.md) |
| `etapa-06` | RAG completo `/ask` | top-K, score mínimo, fontes, prompt injection | [📄](docs/steps/06-rag.md) |
| `etapa-07` | Front-end e streaming | streaming cancelável, rate limit, UX, XSS | [📄](docs/steps/07-frontend.md) |
| `main` | Código de produção | testes, lint, CI | [📄](docs/steps/08-production.md) |

> Os nomes da rota `/career-plan` e do arquivo `src/schemas/career-plan.ts` foram mantidos do projeto original por compatibilidade. Aqui, eles geram **uma aula**, e não um plano de carreira.

---

## Como funciona

```mermaid
flowchart LR
    subgraph Ingestão["Ingestão (pnpm ingest — roda uma vez)"]
        D[data/documents/*.md<br/>7 arquivos de Matemática] --> C[chunkMarkdown<br/>1 seção = 1 chunk]
        C --> E1[Gemini<br/>embeddings]
        E1 --> I[(data/index.json<br/>≈ 66 chunks × 768)]
    end

    subgraph Pergunta["POST /ask"]
        P[pergunta] --> E2[Gemini<br/>embedding]
        E2 --> S{cosseno vs índice<br/>score ≥ 0,58?}
        I -.-> S
        S -- não --> N["Não encontrei"<br/>sem chamar a LLM]
        S -- "top 4" --> PR[prompt com<br/>trechos numerados]
        PR --> G[Gemini<br/>gera resposta]
        G --> R["resposta + [1][2]<br/>+ fontes"]
    end
```

### Endpoints

<details>
<summary><code>POST /chat</code> — conversa com o professor</summary>

```bash
curl -s -X POST localhost:3333/chat -H 'Content-Type: application/json' -d '{
  "messages": [{ "role": "user", "text": "Por que 0,999... é igual a 1?" }]
}'
```
```json
{ "answer": "Ótima pergunta! Vamos pela intuição: se x = 0,999..., então 10x = 9,999... ..." }
```
`POST /chat/stream` recebe o mesmo corpo e devolve o texto em *streaming* (`text/plain`).
</details>

<details>
<summary><code>POST /career-plan</code> — aula completa em JSON validado</summary>

```bash
curl -s -X POST localhost:3333/career-plan -H 'Content-Type: application/json' -d '{
  "aboutMe": "Aula de função quadrática para o 1º ano, 50 minutos. A turma tem dificuldade em fatoração e em gráficos. Tenho lousa e projetor."
}'
```
```json
{
  "topic": "Função quadrática",
  "grade": "1º ano do ensino médio",
  "durationMinutes": 50,
  "summary": "Aula que parte da trajetória de uma bola para construir a ideia de parábola...",
  "learningObjectives": ["Reconhecer uma função quadrática pela lei f(x) = ax^2 + bx + c", "..."],
  "prerequisites": ["Fatoração", "Plano cartesiano"],
  "hook": "Uma bola é chutada: por que a trajetória é uma curva e não uma reta?",
  "lessonSteps": [{ "order": 1, "title": "Da bola à parábola", "minutes": 10, "description": "...", "workedExample": "..." }],
  "classActivity": { "title": "Gráficos no GeoGebra", "format": "pairs", "description": "..." },
  "exercises": [{ "level": "basic", "statement": "...", "answer": "...", "solution": "..." }],
  "commonMistakes": [{ "mistake": "Esquecer o sinal de b na fórmula", "howToAvoid": "..." }],
  "exitQuestions": ["..."],
  "beautyConnection": "A parábola também aparece nas antenas parabólicas...",
  "adaptations": { "struggling": "...", "advanced": "..." },
  "resources": [{ "name": "Khan Academy", "kind": "course", "why": "..." }]
}
```
> O JSON acima mostra o formato esperado. O contrato real (campos e tipos) é definido em `src/schemas/career-plan.ts`.
</details>

<details>
<summary><code>POST /ask</code> — RAG com fontes</summary>

```bash
curl -s -X POST localhost:3333/ask -H 'Content-Type: application/json' \
  -d '{ "question": "Por que a raiz de 2 é irracional?" }'
```
```json
{
  "answer": "Porque, se √2 fosse uma fração a/b irredutível, teríamos a² = 2b², e isso obrigaria a e b a serem pares, o que é uma contradição [1].",
  "sources": [
    { "ref": 1, "file": "01_numeros_e_suas_curiosidades.md", "section": "Racionais, irracionais e a surpresa de 0,999... [básico]", "score": 0.8 }
  ]
}
```
Perguntas sem resposta nos documentos (por exemplo, "Qual o preço de um livro de Cálculo?") devolvem `"Não encontrei essa informação nos documentos que tenho."`, sem chamar a LLM.
</details>

`GET /health` devolve o status e o modelo em uso. Há requisições prontas em [`requests.http`](requests.http) (extensão REST Client do VS Code).

### Erros
Toda falha volta como `{ "error": "mensagem para o usuário" }`, com o status HTTP que a descreve — sem vazar detalhes internos (eles ficam no log do servidor).

| Status | Quando |
|---|---|
| `400` | corpo inválido (com `details` por campo) |
| `429` | limite de 15 chamadas de IA por minuto, ou cota do Gemini |
| `502` | o Gemini recusou a requisição ou devolveu JSON fora do schema |
| `503` / `504` | o Gemini está fora do ar / demorou demais |
| `500` | erro inesperado |

---

## Estrutura do projeto

```
├── src/                       # código da API
│   ├── server.ts              # ponto de entrada: carrega o índice e coloca no ar
│   ├── app.ts                 # buildApp(): monta o Fastify com dependências injetadas
│   ├── config/
│   │   ├── env.ts             # regras do .env (zod) — puro, testável
│   │   └── config.ts          # lê e valida o .env uma única vez
│   ├── ai/
│   │   ├── llm.ts             # createLlm(): chat, chatJson, chatStream
│   │   ├── gemini.ts          # cliente real do Gemini (único arquivo com a chave)
│   │   └── prompts.ts         # persona do professor, instruções da aula e prompts do RAG
│   ├── rag/
│   │   ├── embeddings.ts      # textos → vetores
│   │   ├── similarity.ts      # similaridade de cosseno
│   │   ├── chunker.ts         # documentos → chunks
│   │   ├── vector-store.ts    # salvar/carregar/validar o índice
│   │   └── retriever.ts       # busca dos trechos mais relevantes
│   ├── http/
│   │   ├── errors.ts          # tratamento central de erros
│   │   ├── validation.ts      # zod como validador do Fastify
│   │   ├── rate-limit.ts      # limite de chamadas de IA
│   │   └── routes/            # chat.ts, career-plan.ts, ask.ts
│   └── schemas/
│       └── career-plan.ts     # o contrato da aula (nome mantido do projeto original)
├── scripts/                   # programas de linha de comando (fora do servidor)
│   ├── 01-hello.ts            # etapa 1
│   ├── 04-similarity.ts       # etapa 4
│   └── ingest.ts              # etapa 5: gera data/index.json
├── public/                    # front-end (HTML, CSS e JS puros, sem build)
│   ├── index.html
│   ├── css/app.css
│   └── js/                    # main, api, dom, format, chat, career-plan, ask
├── test/                      # Vitest
│   ├── helpers/fakes.ts       # IA falsa: sem chave, sem internet, sem custo
│   ├── unit/
│   └── integration/
├── data/
│   ├── documents/             # corpus do RAG: 7 arquivos .md de Matemática
│   └── index.json             # índice vetorial gerado pelo pnpm ingest
└── docs/                      # guias das etapas e material do ministrante
```

## Scripts

| Comando | O que faz |
|---|---|
| `pnpm hello` | Primeira chamada ao Gemini (etapa 1) |
| `pnpm dev` | API + front com recarregamento automático |
| `pnpm start` | API sem recarregamento |
| `pnpm similarity` | Demonstração de embeddings (etapa 4) |
| `pnpm ingest` | Gera `data/index.json` a partir de `data/documents/` (etapa 5) |
| `pnpm test` / `pnpm test:watch` | Testes automatizados |
| `pnpm typecheck` | Verifica os tipos TypeScript |
| `pnpm lint` / `pnpm format` | Lint e formatação (Biome) |
| `pnpm check` | Tipos + lint + testes (o mesmo que o CI roda) |

## Configuração (`.env`)

| Variável | Padrão | Descrição |
|---|---|---|
| `GEMINI_API_KEY` | — | **Obrigatória.** Chave do Google AI Studio |
| `GEMINI_MODEL` | `gemini-3.5-flash-lite` | Modelo de geração (rápido, cota gratuita generosa) |
| `GEMINI_THINKING_LEVEL` | `MINIMAL` | Quanto o modelo "pensa": `MINIMAL`, `LOW`, `MEDIUM` ou `HIGH` (para contas e gabaritos, `MEDIUM` ou `HIGH` tende a errar menos) |
| `GEMINI_EMBEDDING_MODEL` | `gemini-embedding-2` | Modelo de embeddings do RAG |
| `LLM_TIMEOUT_MS` | `30000` | Tempo máximo esperando a IA |
| `PORT` | `3333` | Porta da API |
| `LOG_LEVEL` | `info` | Nível de log (`debug`, `info`, `warn`...) |

## Padrões de código

| Padrão | Exemplo |
|---|---|
| Identificadores em **inglês**, `camelCase` | `createRetriever`, `chatJson`, `aboutMe` |
| Tipos e classes em `PascalCase` | `CareerPlan`, `InvalidResponseError` |
| Constantes em `UPPER_SNAKE_CASE` | `MIN_SCORE`, `AI_RATE_LIMIT` |
| Arquivos em `kebab-case` | `vector-store.ts`, `career-plan.ts` |
| Comentários e mensagens ao usuário em **português** | o código fala a língua do mercado; a explicação, a do time |

## Stack

| Peça | Escolha | Por quê |
|---|---|---|
| Runtime | Node.js 22 + `tsx` | TypeScript sem etapa de build |
| HTTP | Fastify 5 | rápido, simples, com plugins de rate limit e arquivos estáticos |
| IA | `@google/genai` (SDK oficial) | geração, JSON estruturado, streaming e embeddings num só SDK |
| Validação | zod 4 | um schema vira JSON Schema, validação e tipo TypeScript |
| Banco vetorial | `index.json` em memória | didático e sem infraestrutura; em produção, pgvector, Qdrant etc. |
| Qualidade | Vitest, Biome, GitHub Actions | testes rápidos, lint/formatação, CI a cada push |

---

## Problemas comuns

| Sintoma | Solução |
|---|---|
| `❌ Configuração inválida... GEMINI_API_KEY` | Rode `cp .env.example .env` e cole a chave |
| `502 Não foi possível falar com o provedor de IA` | A chave está inválida; copie de novo do AI Studio |
| `429` | Limite por minuto: aguarde 60 segundos |
| Servidor não sobe: `Índice não encontrado` | `pnpm ingest` |
| Servidor não sobe: `O índice foi gerado com ...` | Você trocou o modelo de embedding: `pnpm ingest` |
| `EADDRINUSE :3333` | Já existe um servidor rodando; feche-o ou mude a `PORT` |
| A IA responde com contas erradas | Suba o `GEMINI_THINKING_LEVEL` e confira sempre os resultados; modelos de linguagem podem errar em aritmética |

Mais detalhes em [`docs/setup.md`](docs/setup.md).

## Faça o seu 🛠️

Este projeto foi feito para virar o **seu** projeto de portfólio. A versão de carreira virou esta versão de Matemática só trocando os documentos, os prompts e o front-end, e você pode fazer o mesmo:

1. Faça um **fork** deste repositório.
2. Troque os arquivos de `data/documents/` por um tema seu (regras de um jogo, cardápio da cantina, matérias do seu ano, física, história...), com seções `##` claras.
3. Ajuste a persona em `src/ai/prompts.ts` e os textos em `public/index.html`.
4. Rode `pnpm ingest` e teste no `/ask`.
5. Escreva o seu README e publique. Marque [@igor-sasaki](https://www.linkedin.com/in/igor-sasaki/) no LinkedIn!

## Documentação

- [Índice da documentação](docs/README.md) — guias das 8 etapas
- [Preparação do ambiente](docs/setup.md)
- Para o ministrante: [roteiro](docs/teaching/script.md) · [checklist](docs/teaching/checklist.md) · [plano B](docs/teaching/plan-b.md)

## Fontes do corpus

Os 7 documentos de `data/documents/` cobrem, em ordem crescente de dificuldade:

1. `01_numeros_e_suas_curiosidades.md`: primos, irracionais, π, e, φ, identidade de Euler e Fibonacci.
2. `02_geometria_simetria_e_formas.md`: Pitágoras, sólidos platônicos, simetria, geometrias não euclidianas e topologia.
3. `03_algebra_e_estruturas.md`: equações, números complexos, Galois, grupos, aritmética modular e álgebra linear.
4. `04_calculo_e_analise.md`: limites, derivadas, integrais, séries, Fourier e equações diferenciais.
5. `05_infinito_logica_e_fundamentos.md`: provas, Cantor, Russell, Gödel e Turing.
6. `06_probabilidade_estatistica_caos_e_fractais.md`: combinatória, Bayes, caos e fractais.
7. `07_historia_aplicacoes_e_problemas_abertos.md`: história, matemática no Brasil, aplicações, Problemas do Milênio, glossário e FAQ.

> Os documentos foram preparados para fins didáticos e podem conter imprecisões. Para conteúdo oficial e atualizado, consulte livros didáticos e a Base Nacional Comum Curricular (BNCC). Recordes e problemas em aberto mudam com o tempo.

## Sobre o autor

**Igor Leonardo Sasaki da Silva Moreira** — Engenheiro Full Stack Sênior, ex-Tech Lead, com mais de 8 anos de experiência com Node.js, TypeScript, React, arquitetura de software e cloud. Técnico em Informática pelo IFSP Araraquara e tecnólogo em Segurança da Informação pela FATEC Araraquara. Professor e palestrante.

[LinkedIn](https://www.linkedin.com/in/igor-sasaki/) · [GitHub](https://github.com/IgorSasaki) · [Lattes](https://lattes.cnpq.br/0034940506327539)

## Licença

[MIT](LICENSE) — use, adapte e publique no seu portfólio.
