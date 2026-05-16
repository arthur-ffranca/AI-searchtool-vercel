# WebScrapping - Vercel

Subistituto do Streamlit para o VERCEL + Agentes de AI.

Funcionamento:
   - Next.js para a interface.
   - FastAPI para processar lotes.
   - Exa e Tavily como agentes para WebScrapping.
     
## Base de Dados pelo NEON para buscar

- Preço
- Concorrência
- NPS
  
## Integração com o Vercel

1. Configure as variaveis:
   - `EXA_API_KEY`
   - `TAVILY_API_KEY`

2. Deploy.

## Como funciona

1. A UI envia uma lista de produtos para `/api/search` dentro do Banco de Dados.
2. A API consulta Exa e Tavily em paralelo.
3. Os resultados sao deduplicados por URL.
4. O extrator local procura padroes tecnicos no conteudo retornado.
5. Cada campo recebe o valor respectivo.
