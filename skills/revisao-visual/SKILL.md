---
name: revisao-visual
description: Revisa uma interface pronta ou em andamento contra o DESIGN.md, a lista anti-AI-slop, acessibilidade (WCAG AA), responsividade e performance, abrindo a página no navegador em várias larguras antes de declarar qualquer tela pronta. Use quando o usuário disser "revisa o visual", "está com cara de IA?", "audita essa página", "está pronto?", "confere no navegador", ou ao terminar qualquer trabalho de UI.
---

# Revisão visual

Nenhuma tela é declarada pronta sem ter sido vista renderizada. Implementar não é validar.

## 1. Preparar

1. Ler `DESIGN.md` do projeto. Sem ele, revisar contra a lista anti-slop do plugin (arquivo `../direcao-visual/references/anti-slop.md`, relativo a esta skill) e registrar que não havia direção definida.
2. Subir o projeto (dev server ou build de preview) e abrir no navegador disponível na sessão.

## 2. Verificação automática disponível

Rodar o que estiver instalado, sem instalar nada novo no meio da revisão:

- **taste-skill**: `consistency.mjs` (larguras múltiplas, PASS/WARN/FAIL), `perf.mjs` e `shoot.mjs` (screenshots). Se o gate dela estiver ativo como Stop hook, deixar ele rodar.
- **web-design-guidelines** (Vercel): auditoria de código contra as Web Interface Guidelines, saída `arquivo:linha`.
- **design:accessibility-review**, se disponível, para auditoria WCAG mais detalhada.
- Lighthouse ou Performance do DevTools para LCP, CLS e peso de JS.

## 3. Verificação manual (sempre)

Olhar screenshots em 1440, 1024, 768 e 390 de largura, em claro e escuro se houver os dois:

- **Direção**: a tela cumpre a frase de posicionamento do DESIGN.md? Poderia ser de qualquer produto?
- **Anti-slop**: percorrer a lista do arquivo anti-slop.md. Para cada item encontrado, existe motivo escrito? Se não, é um problema.
- **Hierarquia**: em 3 segundos dá para saber o que é a tela e qual a ação principal? Existe um único foco?
- **Conteúdo**: sem lorem ipsum, número inventado, depoimento falso, logo de cliente inexistente.
- **Tokens**: cores, raios, sombras e espaçamentos vêm do sistema? Procurar valores hardcoded (`#hex`, `rounded-[..]`, `shadow-[..]`) fora dos tokens.
- **Componentes de biblioteca**: foram adaptados ou estão com o visual padrão da demo?
- **Acessibilidade**: contraste AA, foco visível, navegação por teclado na ação principal, alvos de toque ≥ 44 px, `alt` em imagens, rótulos em campos.
- **Movimento**: respeita o nível do DESIGN.md; testar com `prefers-reduced-motion` ligado.
- **Responsivo**: nada estoura, nada fica sobreposto, texto legível em 390 px.

Para trabalho importante (landing pública, tela principal do produto), pedir a revisão ao agente `revisor-visual` deste plugin, que não viu a construção e avalia com contexto limpo.

## 4. Relatar

Formato curto, nesta ordem:

1. **Veredito**: pronto / pronto com ressalvas / não pronto.
2. **Problemas**, do mais grave ao menos grave: o que é, onde (arquivo ou seção + largura), por que importa, correção proposta.
3. **O que foi verificado e como** (navegador, larguras, ferramentas) e **o que não foi verificado**.
4. **Decisões do dono do produto**, se houver (posicionamento, conteúdo real que falta).

Corrigir diretamente os problemas técnicos e de execução (contraste, token errado, layout quebrado). Não alterar posicionamento, copy de marca ou estrutura do produto sem consultar o usuário.
