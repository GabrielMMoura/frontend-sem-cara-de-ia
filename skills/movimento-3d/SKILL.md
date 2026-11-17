---
name: movimento-3d
description: Decide se uma interface precisa de animação ou 3D, escolhe a ferramenta certa (CSS, Motion, GSAP/ScrollTrigger, Three.js/R3F, Spline, Unicorn Studio, Lottie) e implementa com orçamento de performance e prefers-reduced-motion. Use quando o usuário disser "anima isso", "coloca uma animação", "efeito de scroll", "parallax", "3D no hero", "usa GSAP/Motion/Three/Spline/Lottie", "micro-interação", "transição de página", ou quando o DESIGN.md prevê movimento.
---

# Movimento e 3D

Movimento existe para explicar (de onde veio, para onde foi, o que mudou), dar resposta a uma ação ou criar um único momento de marca. Fora disso, é ruído.

## 1. Conferir o orçamento

Ler o nível de movimento no `DESIGN.md`:

- **0**: só transições de estado (hover, focus, abrir/fechar) em CSS, 120–200 ms.
- **1**: micro-interações e transições de layout (Motion ou CSS).
- **2**: revelações de scroll pontuais, sequências curtas, texto animado em um ou dois lugares (Motion ou GSAP).
- **3**: cena 3D, shader, scroll narrativo (Three.js/R3F, Spline, Unicorn Studio, GSAP ScrollTrigger).

Se o pedido exigir subir o nível, dizer isso ao usuário com o custo (peso, performance em celular, manutenção) e recomendar. Painel e ferramenta de trabalho diário não passam do nível 1 sem motivo forte.

## 2. Escolher a ferramenta

Ler `references/ferramentas.md`. Resumo:

| Caso | Ferramenta |
|---|---|
| Hover, focus, abrir/fechar, skeleton | CSS (transition, @keyframes, `@starting-style`, View Transitions) |
| Componentes React com estado, layout animation, gestos, exit | Motion (`motion/react`) |
| Timeline complexa, scroll sincronizado, SVG, texto por letra, Flip | GSAP + ScrollTrigger/SplitText/Flip (todos os plugins são gratuitos) |
| Cena 3D programada, interação com dados | Three.js ou React Three Fiber |
| Objeto 3D desenhado por designer, sem código de cena | Spline (embed) |
| Fundo/shader/efeito WebGL desenhado visualmente | Unicorn Studio (embed) |
| Ilustração animada, ícone animado, estado de sucesso | Lottie (dotLottie) |

Uma página usa uma biblioteca de animação JS, não duas. Se o projeto já usa Motion, não adicionar GSAP para um efeito que o Motion faz.

## 3. Usar as skills oficiais

- **GSAP**: se as skills oficiais da GreenSock (`gsap-core`, `gsap-scrolltrigger`, `gsap-react` etc.) estiverem instaladas, seguir as regras delas. Em React, usar `useGSAP` e limpar no unmount.
- **Motion**: se o Motion AI Kit estiver instalado, consultar a documentação atual por ele antes de escrever código; não confiar em APIs antigas do `framer-motion`.
- Se não estiverem instaladas, sugerir a skill `preparar-projeto` uma vez e seguir com a documentação oficial (gsap.com/docs, motion.dev/docs).

## 4. Regras de implementação

- Animar só `transform` e `opacity` (e `filter` com cuidado). Nunca `width`, `height`, `top`, `left` em loop.
- Duração: 150–300 ms para interface, até 600–800 ms para entrada de seção. Easing de saída (`ease-out` / curvas tipo `[0.22, 1, 0.36, 1]`), nunca linear em UI.
- `prefers-reduced-motion: reduce`: desligar parallax, scroll scrub, autoplay e 3D em movimento; manter só mudanças de opacidade. Em GSAP, usar `gsap.matchMedia()`; em Motion, `useReducedMotion`.
- 3D/WebGL: carregar sob demanda (lazy, `IntersectionObserver`), ter imagem estática de fallback para mobile fraco e para reduced motion, limitar a no máximo 2 contextos WebGL por página, pausar fora da viewport.
- Embeds (Spline, Unicorn Studio, Lottie): definir tamanho fixo para evitar layout shift; carregar depois do conteúdo principal; não usar como única forma de transmitir informação.
- Nada de animação na primeira pintura que atrase o LCP do título principal.

## 5. Validar

Abrir no navegador, testar em largura de celular, com reduced motion ligado e com CPU limitada (DevTools, 4x slowdown). Registrar no relatório final o que foi testado e o que não foi.
