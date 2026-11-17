# Fontes de inspiração: o que cada uma faz bem

Acesso verificado em novembro de 2026. Conferir de novo se algo falhar.

| Fonte | Melhor para | Limitação | Como o agente acessa |
|---|---|---|---|
| **Mobbin** (mobbin.com) | Telas e fluxos reais de apps iOS/web: onboarding, checkout, configurações, estados vazios. A melhor para UI de produto. | MCP só nos planos Pro/Team/Enterprise. | MCP oficial `https://api.mobbin.com/mcp` (HTTP, OAuth no primeiro uso). Sem plano: navegador logado do usuário. |
| **Refero** (refero.design) | Telas, fluxos e "styles" (sistemas visuais com DESIGN.md pronto) de produtos web. Bom para dashboards e SaaS. | MCP exige plano pago. | MCP oficial `https://api.refero.design/mcp` (OAuth ou Bearer token). |
| **Godly** (godly.website) | Landing pages com direção de arte forte, tipografia e movimento ousados. | Muito site de agência/portfólio; nem tudo serve para produto. | Navegador ou WebFetch. Abrir o site original para ver o movimento. |
| **Awwwards** (awwwards.com) | Estado da arte em interação, WebGL, scroll narrativo. Filtrar por "Sites of the Day" e categoria. | Viés para sites de vitrine pesados; performance ruim é comum. | Navegador ou WebFetch. |
| **Land-book** (land-book.com) | Landings de SaaS, apps e produtos, por categoria. Mais pragmático que Godly/Awwwards. | Às vezes conservador. | Navegador ou WebFetch. |
| **Dribbble** (dribbble.com) | Exploração de estilo, ilustração, paleta e ícones. | Muito conceito que nunca foi para produção; layouts que quebram com conteúdo real. Usar com ceticismo. | Navegador ou WebFetch. |

## Como usar uma referência

1. Abrir o site real, não só o screenshot da galeria: ver em mobile, rolar, testar hover.
2. Escrever o princípio em uma linha. Exemplo: "Linear: hierarquia feita só com peso e cinza, quase sem cor; o acento aparece só em estado ativo."
3. Escrever o que não copiar. Exemplo: "o gradiente do hero, que é a assinatura deles".
4. Nunca usar logotipo, ilustração, foto, copy ou layout idêntico de outra marca.

## Combinação por tipo de projeto

- **SaaS B2B / painel**: Mobbin e Refero (telas de produto) + Land-book (landing). Godly só para o hero, se houver.
- **Serviço profissional (jurídico, contábil, previdenciário)**: Land-book + sites reais de escritórios bem desenhados. Evitar Awwwards, que puxa para espetáculo e afasta confiança.
- **Produto infantil/educação**: Mobbin (apps infantis reais) + Dribbble para ilustração e paleta.
- **Lançamento / marca forte**: Godly + Awwwards, com orçamento de movimento definido antes.
