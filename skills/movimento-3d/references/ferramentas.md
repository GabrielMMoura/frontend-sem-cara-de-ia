# Ferramentas de animação e 3D

Verificado em novembro de 2026.

## GSAP (gsap.com)
- 100% gratuito, inclusive todos os plugins (ScrollTrigger, SplitText, Flip, MorphSVG, DrawSVG), pelo pacote público `gsap` no npm.
- Melhor para: timelines encadeadas, scroll sincronizado, SVG, animação de texto por caractere, transições com Flip, qualquer framework ou JS puro.
- Skills oficiais: repositório `greensock/gsap-skills` (core, timeline, scrolltrigger, plugins, react, frameworks, utils, performance). Instalação: `npx skills add https://github.com/greensock/gsap-skills` ou `/plugin marketplace add greensock/gsap-skills` no Claude Code.

## Motion (motion.dev), antigo Framer Motion
- Pacote `motion`; em React, importar de `motion/react`.
- Melhor para: componentes React com estado, `AnimatePresence` (saída), layout animations, gestos, springs.
- Motion AI Kit (`npx motion-ai`): skill de boas práticas e busca na documentação atual gratuitas; exemplos, Performance Doctor, springs em CSS e editor de transição exigem Motion+.

## Three.js (threejs.org) / React Three Fiber
- Melhor para: cena 3D programada, visualização de dados em 3D, interação com modelo.
- Em React, preferir `@react-three/fiber` + `@react-three/drei`.
- Custo alto: bundle, GPU, bateria. Sempre lazy e com fallback estático.

## Spline (spline.design)
- Editor 3D visual; exporta embed web (`@splinetool/react-spline` ou viewer).
- Melhor para: objeto/cena 3D criado por designer, sem programar a cena.
- Cuidado: arquivos `.splinecode` pesados; testar tempo de carregamento.

## Unicorn Studio (unicorn.studio)
- Editor visual de efeitos WebGL (shaders, gradientes vivos, distorção, partículas) com embed por script/SDK.
- Melhor para: fundo de hero com identidade sem escrever shader.
- Cuidado: um efeito por página; pausar fora da viewport; fallback estático.

## Lottie (lottiefiles.com)
- Animações vetoriais exportadas do After Effects; preferir o formato dotLottie (`@lottiefiles/dotlottie-react` ou `dotlottie-web`).
- Melhor para: ilustração animada, ícones animados, estados de sucesso/vazio/carregamento.
- Cuidado: arquivos da comunidade têm licença e estilo variados; manter consistência com a ilustração do produto.

## CSS moderno
- `transition`, `@keyframes`, `@starting-style` (entrada de elementos), View Transitions API (troca de página/estado), `animation-timeline: scroll()/view()` para scroll simples sem JS.
- Primeira escolha para tudo que é nível 0 e 1.
