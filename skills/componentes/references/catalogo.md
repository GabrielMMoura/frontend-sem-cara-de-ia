# Catálogo de bibliotecas de componentes

Verificado em novembro de 2026. Namespaces e URLs podem mudar: se `npx shadcn add` falhar, conferir em https://ui.shadcn.com/r/registries.json (lista oficial de registries).

| Fonte | Forte em | Risco | Namespace / acesso |
|---|---|---|---|
| **shadcn/ui** (ui.shadcn.com) | Primitivos acessíveis (Radix ou Base UI), blocos de app, charts. Base de tudo. | Visual padrão reconhecível se não ajustar tokens. | Padrão da CLI. Skill oficial: `npx skills add shadcn/ui`. |
| **Magic UI** (magicui.design) | Maior registry animado: marquee, number ticker, animated beam, text effects, backgrounds. | Muitos efeitos "assinatura" de landing de IA. Usar com parcimônia. | `@magicui` → `https://magicui.design/r/{name}.json` |
| **Aceternity UI** (ui.aceternity.com) | Efeitos de impacto: 3D card, spotlight, parallax, timelines, seções completas. | Estética muito associada a landing de IA (aurora, sparkles, beams). Alguns itens são pagos e falham na instalação. | `@aceternity` → `https://ui.aceternity.com/registry/{name}.json` |
| **React Bits** (reactbits.dev) | Animações de texto, backgrounds WebGL, cursores, componentes criativos. Variantes JS/TS × CSS/Tailwind. | Vários usam canvas/WebGL: custo de performance. Pro tem registry separado com licença. | `@react-bits` → `https://reactbits.dev/r/{name}.json` |
| **Motion Primitives** (motion-primitives.com) | Primitivos de movimento reutilizáveis (text effect, shimmer, infinite slider, morphing dialog). Mais sóbrio. | Catálogo menor. | `@motion-primitives` → `https://motion-primitives.com/c/{name}.json` |
| **21st.dev** | Marketplace comunitário de componentes shadcn-compatíveis; busca por categoria; MCP. | Qualidade varia por autor. MCP exige chave (21st.dev/mcp). | Instalação por link do componente via `npx shadcn add <url>`; MCP: `https://21st.dev/api/mcp` com header `x-api-key`. |
| **Uiverse** (uiverse.io) | Elementos isolados em HTML/CSS/Tailwind: botões, loaders, toggles, cards. MIT. | Sem tokens; código muitas vezes verboso. | Copiar e reescrever. |
| **Hover.dev** | Componentes animados React + Tailwind + Motion, bem acabados. | Majoritariamente pago. | Só com acesso do usuário. |

## Bloco de registries para components.json

Adicionar só os que o DESIGN.md permite:

```json
"registries": {
  "@magicui": "https://magicui.design/r/{name}.json",
  "@aceternity": "https://ui.aceternity.com/registry/{name}.json",
  "@react-bits": "https://reactbits.dev/r/{name}.json",
  "@motion-primitives": "https://motion-primitives.com/c/{name}.json"
}
```

## Escolha rápida

| Necessidade | Primeira opção | Alternativa |
|---|---|---|
| Formulário, tabela, settings, navegação | shadcn/ui | — |
| Números animando, logos rolando | Magic UI | Motion Primitives |
| Texto com animação de entrada | Motion Primitives (sóbrio) | React Bits (expressivo) |
| Fundo animado | React Bits ou shader do Unicorn Studio | Magic UI |
| Card com profundidade/tilt, spotlight | Aceternity | — |
| Botão, loader ou toggle com personalidade | Uiverse (reescrito) | Hover.dev |
| Seção inteira de landing | Blocos do shadcn/ui ou seções da Aceternity como esqueleto, reescritos com conteúdo real | 21st.dev |
