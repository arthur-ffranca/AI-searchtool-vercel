# Busca de Especificacoes - Vercel

Substituto Vercel-native para o scraper Streamlit de especificacoes tecnicas.

O app usa:

- Next.js para a interface.
- Route Handler `/api/search` para processar lotes.
- Exa e Tavily como fontes de busca IA.
- Extracao local por regex dos campos tecnicos principais.

## Campos extraidos

- Potencia
- Voltagem
- Consumo kWh
- BTU
- Fase
- Corrente
- Consumo de gas
- Fonte/evidencia por campo

## Configuracao local

```bash
cd specs-scraper-vercel
npm install
copy .env.example .env.local
npm run dev
```

Preencha `.env.local`:

```bash
EXA_API_KEY=...
TAVILY_API_KEY=...
```

Acesse `http://localhost:3000`.

## Deploy na Vercel

1. Crie um novo projeto na Vercel apontando para esta pasta.
2. Configure as variaveis:
   - `EXA_API_KEY`
   - `TAVILY_API_KEY`
   - `SCRAPER_MAX_PRODUCTS` opcional, padrao `8`
   - `SCRAPER_MAX_AI_RESULTS` opcional, padrao `8`
3. Deploy.

Importante: a Vercel precisa enxergar o `package.json` desta pasta. Se o repositório tambem tiver arquivos Python como `app_busca.py` ou `freezer_specs_scraper.py`, configure **Root Directory** como `specs-scraper-vercel` ou mova o conteudo desta pasta para a raiz do repositorio. Se a Vercel tentar usar Python, o deploy correto ainda nao esta apontando para este app Next.js.

Configuracao esperada no projeto Vercel:

- Framework Preset: Next.js
- Root Directory: `specs-scraper-vercel`, se esta pasta estiver dentro de um repo maior
- Install Command: `npm install`
- Build Command: `npm run build`
- Output Directory: deixe em branco/default

## Como funciona

1. A UI envia uma lista de produtos para `/api/search`.
2. A API consulta Exa e Tavily em paralelo.
3. Os resultados sao deduplicados por URL.
4. O extrator local procura padroes tecnicos no conteudo retornado.
5. Cada campo recebe valor, fonte, provedor e evidencia.

## Diferencas em relacao ao Streamlit/Python

Esta versao foi desenhada para rodar bem em Vercel. Por isso, ela nao usa Selenium/headless browser. Em vez disso, delega a descoberta e conteudo de paginas a Exa e Tavily. Isso reduz instabilidade em serverless e evita depender de Chrome dentro da funcao.

Se voce precisar manter o parser de PDF profundo do script Python original, o melhor desenho e separar um worker Python em Render/Fly.io/Cloud Run e deixar este app Vercel como frontend + orquestrador.
