---
name: direcao-visual
description: Define a direção visual de uma interface antes de qualquer código - classifica o produto, pesquisa referências reais (Mobbin, Refero, Awwwards, Godly, Land-book, Dribbble) e grava um DESIGN.md com tokens, tipografia, paleta, orçamento de movimento e referências justificadas. Use quando o usuário disser "cria uma landing", "faz a tela de X", "redesenha", "quero um visual para", "qual estilo usar", "me mostra referências", ou ao começar qualquer UI nova sem DESIGN.md no projeto.
---

# Direção visual

Nenhuma tela começa sem direção. Esta skill produz o `DESIGN.md` do projeto, que todas as outras skills do plugin leem antes de agir.

## 1. Verificar o que já existe

1. Procurar `DESIGN.md`, `design.md`, `docs/design*`, `tailwind.config.*`, `app/globals.css`, `components.json`. Se já houver tokens e um DESIGN.md coerente, respeitar e só complementar.
2. Em redesign de algo existente: abrir a página atual no navegador (preview local ou URL), tirar screenshots em 1440, 768 e 390 de largura e listar o que funciona antes de propor mudança. Não redesenhar o que não está quebrado.

## 2. Classificar antes de desenhar

Responder, por escrito no DESIGN.md:

- **Tipo**: software/SaaS, ferramenta interna/dashboard, tech/dev, produto físico/loja, serviço profissional (jurídico, contábil, saúde), lugar/hospitalidade, conteúdo/editorial, infantil/educação.
- **Público e contexto de uso**: quem usa, em que dispositivo, com que pressa. Um painel usado 8h/dia pede densidade e calma; uma landing de lançamento pode arriscar.
- **Uma frase de posicionamento visual**: o que esta interface deve transmitir que a do concorrente não transmite. Se a frase serve para qualquer produto, reescrever.
- **Conteúdo real disponível**: screenshots do produto, fotos, dados, depoimentos verdadeiros. Interface se desenha em torno de conteúdo, não de placeholders.

Se o tipo ou o público não puderem ser inferidos do repositório e da conversa, perguntar uma vez. É decisão de negócio.

## 3. Pesquisar referências reais

Ler `references/fontes-de-inspiracao.md` para saber o que cada fonte faz bem e como acessá-la. Ordem de preferência:

1. **MCP do Mobbin ou do Refero**, se estiverem conectados (verificar com as ferramentas disponíveis na sessão). São as melhores fontes para telas de produto e fluxos reais.
2. **Galerias públicas via navegador ou WebFetch**: Godly e Awwwards para landing/marketing ousado; Land-book para landing de SaaS/produto; Dribbble só para exploração de estilo (muito conceito que nunca foi a produção).
3. **Produtos reais do mesmo segmento** (concorrentes diretos e referências de categoria vizinha).

Regras da pesquisa:

- Coletar de 5 a 8 referências, nunca uma só. Para cada uma registrar: link, **o princípio** que se aproveita (hierarquia, ritmo, tipografia, uso de espaço, densidade, movimento) e o que **não** copiar.
- Combinar princípios de referências diferentes. Nunca reproduzir layout, marca, ilustração ou copy de um site específico.
- Desconfiar de referência que só impressiona em screenshot: verificar se funciona com conteúdo real e em mobile.

## 4. Decidir o sistema

Se a taste-skill (`design-taste-frontend`) estiver instalada, usar os scripts dela para sortear paleta e par tipográfico por tipo de página (`start.mjs`) e layout de hero (`deal.mjs`) e tratar o resultado como ponto de partida, não como verdade. Ajustar ao posicionamento definido no passo 2.

Definir no DESIGN.md:

- **Tokens**: cores semânticas (fundo, superfície, texto, texto-suave, borda, acento, sucesso, alerta, erro) em OKLCH ou HSL, com contraste AA verificado; escala de espaçamento; raio (um ou dois valores, não cinco); sombra (no máximo dois níveis, ou nenhuma).
- **Tipografia**: no máximo duas famílias, com motivo da escolha ligado ao posicionamento; escala de tamanhos; comprimento de linha de 60 a 75 caracteres para texto corrido.
- **Grid e ritmo**: largura máxima, colunas, como as seções alternam densidade. Variar a estrutura entre seções de acordo com o conteúdo, sem repetir título + três cards.
- **Orçamento de movimento**: nível 0 (nenhum além de transições de estado), 1 (micro-interações), 2 (revelações de scroll pontuais) ou 3 (cena 3D/WebGL). Painéis e ferramentas internas ficam em 0 ou 1. Nível 3 só com justificativa escrita. Detalhes na skill `movimento-3d`.
- **Fontes de componentes permitidas** neste projeto (ver skill `componentes`).
- **Referências** com o princípio extraído de cada uma.
- **Lista de proibições do projeto**: o que deixaria esta interface genérica (ver `references/anti-slop.md`).

Usar `references/modelo-design-md.md` como estrutura do arquivo.

## 5. Mostrar antes de construir

Apresentar ao usuário em poucas linhas: classificação, frase de posicionamento, 3 referências principais com o princípio de cada, paleta e tipografia. Decisões de marca e posicionamento são do usuário: se ele não tiver dado direção, recomendar uma opção e seguir, deixando claro que é recomendação. Depois disso, seguir para a construção usando `componentes` e `movimento-3d`, e fechar com `revisao-visual`.
