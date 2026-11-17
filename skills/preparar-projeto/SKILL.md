---
name: preparar-projeto
description: Instala e confere a stack de design que este plugin orquestra - plugins e skills complementares (taste-skill, frontend-design, gsap-skills, shadcn, web-design-guidelines, Motion AI Kit) uma vez por máquina, e registries do shadcn, dependências e DESIGN.md em cada projeto. Use quando o usuário disser "prepara o projeto", "configura o design", "instala a stack", "o que falta instalar", "setup do plugin", ou quando outra skill do plugin depender de algo ausente.
---

# Preparar projeto

Duas camadas: o que se instala **uma vez por máquina** e o que se configura **em cada projeto**. Verificar antes de instalar; não reinstalar o que existe.

## Camada 1: uma vez por máquina (Claude Code)

Conferir o que já existe com `claude plugin list` e `claude plugin marketplace list`, e as skills em `~/.claude/skills/`. Instalar só o que falta.

| Item | Para quê | Instalação |
|---|---|---|
| **taste-skill** (`design-taste-frontend`, MIT) | Paleta e tipografia por tipo de página, layouts de hero testados, verificação no navegador e gate de conclusão | `claude plugin marketplace add Leonxlnx/taste-skill` → `claude plugin install taste-skill@taste-skill` |
| **frontend-design** (Anthropic) | Diretrizes oficiais de frontend com identidade | `claude plugin install frontend-design@claude-plugins-official` |
| **gsap-skills** (GreenSock, oficial) | Uso correto de GSAP, ScrollTrigger, plugins, React | `claude plugin marketplace add greensock/gsap-skills` → `claude plugin install gsap-skills@gsap-skills` |
| **shadcn** (skill oficial) | Contexto do projeto shadcn, add/compose/fix corretos | `npx skills add shadcn/ui` |
| **web-design-guidelines** (Vercel) | Auditoria de UI contra 100+ regras de interface | `npx skills add vercel-labs/agent-skills --skill web-design-guidelines` |
| **Motion AI Kit** | Documentação atual do Motion e boas práticas | `npx motion-ai` (interativo: deixar o usuário rodar) |

Requisitos da taste-skill: Node 22+ e Chrome/Edge/Chromium. Conferir com `node -v`.

Se o comando `claude` não estiver disponível (por exemplo, dentro do Cowork), listar para o usuário os comandos equivalentes de barra (`/plugin marketplace add ...`, `/plugin install ...`) para ele rodar no Claude Code, em vez de tentar outro caminho.

### Conectores opcionais (pagos ou com chave)

Não instalar sem o usuário confirmar que tem acesso:

- **Mobbin MCP** (planos Pro/Team/Enterprise): `claude mcp add --transport http --scope user mobbin https://api.mobbin.com/mcp`. Autoriza por OAuth no primeiro uso.
- **Refero MCP** (plano pago): `claude mcp add --transport http --scope user refero https://api.refero.design/mcp`. OAuth ou `--header "Authorization: Bearer <token>"`.
- **21st MCP** (chave em 21st.dev/mcp): `npx @21st-dev/cli@latest init --client claude`.

Nunca gravar chave de API em arquivo versionado.

## Camada 2: em cada projeto

1. **Detectar a stack**: `package.json`, framework (Next, Vite, Astro), Tailwind v3 ou v4, se já existe `components.json`.
2. **shadcn**: se não houver `components.json` e o projeto for React, perguntar antes de rodar `npx shadcn@latest init` (mexe em CSS global e config). Se já houver, só seguir.
3. **Registries**: adicionar ao `components.json` apenas os namespaces que o projeto vai usar (bloco em `../componentes/references/catalogo.md`, relativo a esta skill).
4. **Dependências de movimento**: só instalar `motion`, `gsap`, `three`/`@react-three/fiber`, `@splinetool/react-spline` ou `@lottiefiles/dotlottie-react` quando a direção visual pedir. Não instalar "por garantia".
5. **DESIGN.md**: se não existir, rodar a skill `direcao-visual`.
6. **CLAUDE.md do projeto**: adicionar uma linha apontando para o DESIGN.md e dizendo que toda UI passa por `revisao-visual` antes de ser dada como pronta. Não duplicar o conteúdo do DESIGN.md ali.

## Relatório

Informar em lista curta: instalado agora, já existia, não instalado e por quê (pago, sem chave, precisa de ação do usuário), e qualquer comando que o usuário precise rodar ele mesmo.
