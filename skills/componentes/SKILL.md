---
name: componentes
description: Escolhe, busca, inspeciona e instala componentes de UI das bibliotecas certas (shadcn/ui, Magic UI, Aceternity, React Bits, Motion Primitives, 21st.dev, Uiverse, Hover.dev) via registry do shadcn e MCP, adaptando ao DESIGN.md do projeto. Use quando o usuário disser "adiciona um componente de X", "preciso de um hero/pricing/tabela/formulário", "pega algo do Magic UI/Aceternity/React Bits", "configura os registries", "qual biblioteca usar para Y", ou ao construir qualquer tela em React/Next.
---

# Componentes

Objetivo: usar componentes prontos onde eles economizam trabalho, sem que a interface vire um catálogo de efeitos de biblioteca.

## Regra de três camadas

1. **Primitivos**: shadcn/ui. Botão, input, dialog, tabela, form, dropdown. Sempre a base.
2. **Superfícies de produto** (formulários, tabelas, navegação, settings): shadcn/ui + blocos de uma única fonte geral, para manter consistência.
3. **Peças de destaque**: no máximo um ou dois componentes animados por página (Magic UI, Aceternity, React Bits, Motion Primitives), escolhidos por motivo escrito no DESIGN.md.

Ler `references/catalogo.md` para saber o forte, o risco e o namespace de cada fonte.

## Fluxo

1. **Ler o contexto**: `DESIGN.md` (fontes permitidas, nível de movimento, tokens). Se não existir e a tarefa for uma tela nova, rodar antes a skill `direcao-visual`.
2. **Contexto do projeto**: `npx shadcn@latest info --json` (framework, aliases, Tailwind v3/v4, componentes já instalados). Não reinstalar o que existe. Se a skill oficial `shadcn` estiver instalada, seguir as regras dela para add, compose e fix.
3. **Registries**: garantir que `components.json` tenha os namespaces que o DESIGN.md permite (bloco pronto em `references/catalogo.md`). Adicionar só os que o projeto vai usar.
4. **Buscar antes de escrever**: usar o MCP `shadcn` (deste plugin) ou a CLI: `npx shadcn@latest search @magicui -q "marquee"`, `npx shadcn@latest list @aceternity`. Comparar duas ou três opções entre registries.
5. **Inspecionar antes de instalar**: `npx shadcn@latest view @namespace/item`. Conferir dependências (motion, gsap, three, @tsparticles etc.), tamanho, se usa canvas/WebGL, se respeita `prefers-reduced-motion`, licença. Rejeitar componente que puxa dependência pesada para um efeito pequeno.
6. **Instalar**: `npx shadcn@latest add @namespace/item`. Depois corrigir imports hardcoded (`@/components/ui/...`) para os aliases do projeto.
7. **Adaptar ao sistema**: trocar cores fixas, gradientes e raios do componente pelos tokens do DESIGN.md. Remover partes decorativas que não têm função aqui. Componente instalado e não adaptado é o caminho mais curto para AI slop.
8. **Registrar**: anotar no DESIGN.md (seção Componentes) o que entrou e onde.

## Fontes fora do registry

- **Uiverse**: HTML/CSS (e Tailwind) por elemento, licença MIT. Usar como ponto de partida para um botão, loader ou toggle: reescrever em componente do projeto com tokens próprios e manter o crédito em comentário.
- **Hover.dev**: componentes animados React/Tailwind/Motion, a maior parte paga. Usar só se o usuário tiver acesso; nunca copiar conteúdo pago de terceiros.
- **21st.dev**: além do registry, existe o 21st MCP (busca e geração de componentes), que exige chave de API. Se estiver conectado na sessão, usá-lo para busca. Componentes da comunidade variam muito em qualidade: sempre inspecionar.

## Não fazer

- Não instalar componente animado em painel/ferramenta interna com orçamento de movimento 0.
- Não misturar dois efeitos de fundo animados na mesma tela.
- Não deixar dependência de animação duplicada (framer-motion e motion juntos, por exemplo).
- Não usar componente de biblioteca para algo que um primitivo shadcn + 10 linhas de Tailwind resolve.
