# frontend-sem-cara-de-ia

Plugin para Claude Code e Cowork que faz o agente criar interfaces web com direção visual própria, sem cara de template de IA. Não substitui as skills oficiais das bibliotecas: decide quando e como usá-las.

## Fluxo

1. `direcao-visual` — classifica o produto, pesquisa referências reais e grava o `DESIGN.md` do projeto.
2. `componentes` — escolhe e instala componentes (shadcn/ui, Magic UI, Aceternity, React Bits, Motion Primitives, 21st.dev, Uiverse, Hover.dev) e adapta aos tokens.
3. `movimento-3d` — decide nível de movimento e ferramenta (CSS, Motion, GSAP, Three.js/R3F, Spline, Unicorn Studio, Lottie).
4. `revisao-visual` — revisão no navegador contra DESIGN.md, anti-slop, acessibilidade e performance. Para entregas importantes, usa o agente `revisor-visual` (contexto limpo).
5. `preparar-projeto` — instala a stack complementar e configura cada projeto.

## Incluído

- Servidor MCP `shadcn` (gratuito, sem chave): busca e instala de qualquer registry configurado no `components.json`.

## Complementos recomendados (instalados pela skill `preparar-projeto`)

taste-skill, frontend-design, gsap-skills, shadcn (skill), web-design-guidelines (Vercel), Motion AI Kit. Opcionais pagos: Mobbin MCP, Refero MCP, 21st MCP.

## Instalação no Claude Code (todos os projetos)

Publicar esta pasta num repositório GitHub e rodar:

```
/plugin marketplace add GabrielMMoura/frontend-sem-cara-de-ia
/plugin install frontend-sem-cara-de-ia@frontend-sem-cara-de-ia
```

Ou localmente: `/plugin marketplace add /caminho/para/frontend-sem-cara-de-ia`.

## Requisitos

Node 22+, Chrome/Chromium (verificação visual da taste-skill).

## Licença

MIT. As bibliotecas e skills complementares têm licenças próprias.
