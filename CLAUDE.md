# Biblioteca de guias de estudo (Huberman Lab)

## O que é este projeto
Uma **biblioteca editável** de guias visuais de estudo, em **pt-BR**, baseada em episódios do
*Huberman Lab*. Cada guia é um **capítulo** longo, em prosa editorial, que o próprio usuário pode
criar, editar, reordenar e excluir direto no navegador.

Tudo vive num só arquivo: **`index.html`** (HTML + CSS + JS inline, sem build, sem dependências
além de Google Fonts). Abrir no navegador já funciona. `.nojekyll` na raiz → serve como site
estático (ex.: GitHub Pages).

## Estado atual
- `index.html` está **completo e funcional** (~1300 linhas). Não é mais o guia single-page antigo:
  virou uma **Biblioteca** com sidebar de capítulos, busca, scroll-spy, barra de progresso,
  marcador de "lido" e um **editor WYSIWYG** por capítulo.
- Visual = **tema editorial estilo Medium** (creme + serifa preta). O reskin do Medium **já foi
  feito** — não é mais uma tarefa pendente. Ver `reference/medium-theme.md` para o brief original.
- O tema neon antigo **foi removido** do projeto (só sobra menção histórica no git).

## Arquitetura (como funciona por dentro)
- **Semente → localStorage.** O conteúdo inicial fica num `<template id="seed">` no HTML. Na
  primeira carga ele é lido uma vez e movido para o `localStorage`; a partir daí **a fonte da
  verdade é o `localStorage`**, não o HTML. Editar o `<template>` só afeta quem ainda não tem
  dados salvos (ou capítulos-semente novos, via merge por chave — ver abaixo).
- **Chaves do `localStorage`:**
  | Chave | Conteúdo |
  |-------|----------|
  | `biblioteca:chapters` | array de capítulos (o modelo de dados) |
  | `biblioteca:seedkeys` | `data-key`s de semente já importados — permite publicar capítulos novos sem apagar edições nem ressuscitar excluídos |
  | `biblioteca:last` | último capítulo aberto |
  | `biblioteca:read` | ids marcados como lidos (pontinho verde na TOC) |
- **Modelo de um capítulo:** `{ id, key, kicker, num, tag, title, html }` (o corpo é HTML rico).
- **CRUD:** editor com toolbar (`data-cmd` → `runCmd`): H2/H3/¶, negrito, itálico, lista, citação,
  callouts (Nota/Aplicar/Cuidado), linha divisória, link. Botões por capítulo: Editar, ↑/↓
  (reordenar), Excluir. `+ Novo capítulo` na sidebar.
- **Navegação:** sidebar sticky com scroll-spy, busca que filtra a TOC, barra de progresso no topo,
  drawer no mobile (`.topbar` + overlay), `#hash` por capítulo, `Esc` fecha o editor.

## Capítulos-semente atuais
| Nº | `data-key` | Título | Base |
|----|-----------|--------|------|
| 01 | `neuroplasticidade` | Neuroplasticidade | Huberman (foco & atenção) |
| 02 | `dopamina` | Dopamina & Motivação | Huberman (busca & impulso) |
| 03 | `aprendizado` | Como o cérebro aprende | Sejnowski (prática & memória) |
| 04 | `autocontrole` | Autocontrole & motivação | Fujita (autocontrole & metas) |

## Sistema de design (o que NÃO pode se perder no significado)
Tema **creme + serifa preta**, seguindo a **rota 1** do brief do Medium: corpo preto-sobre-creme,
com as 4 cores funcionais traduzidas para **acentos terrosos/dessaturados**, usados só em detalhes
pequenos (filete de callout, número de seção, traço de SVG, termos marcados). A cor ainda codifica
função — não é decoração:

| Papel | Var CSS | Cor |
|-------|---------|-----|
| Ideia-chave / marcação (roxo) | `--f-key` | `#6E5A8F` |
| Aplicar / alerta (ocre) | `--f-apply` | `#A8632E` |
| Foco / termo (verde-azulado) | `--f-focus` | `#3E7D74` |
| Cuidado / dopamina (argila-rosa) | `--f-warn` | `#A85570` |

Tokens base: `--bg #F7F4EC`, `--surface #FFF`, `--ink #242424`, `--title #191919`,
`--muted #6B6B6B`, `--rule #E6E3DA`, `--accent #1A8917` (verde "lido"). Fontes:
**Fraunces** (display/serif de título), **Source Serif 4** (corpo), **Inter** (rótulos/UI sans).

**Elementos-assinatura** (repensados no vocabulário editorial, sem neon): a **"equação química"**
da plasticidade (cap. 01) e as **curvas SVG** de abertura — pico↔linha-de-base da dopamina (02),
o laço prever→agir→comparar→atualizar (03) e as curvas "por quê × como" que se cruzam (04). São
tipográficos/em linha, não brilhantes.

Classes úteis: `.chapter`, `.ch-kicker`, `.ch-sub`, `.ch-actions`; `.equation`/`.term`/`.op`;
`.curve` (wrapper de SVG) + `.c-cap` (legenda); `.duo`/`.d-card` (`.plastic`/`.fixed`);
callouts via classe (`key`/`apply`/`warn`/`term`); `.lead`. A sidebar usa `.toc` (`.t-num`,
`.t-title`, `.t-tag`, `.t-read`).

## Regras ao mexer aqui
- É um **artefato editável pelo usuário final**, não só um documento. Preserve o CRUD, o scroll-spy,
  a busca, o progresso e o merge de semente — não quebre o contrato do `localStorage`.
- Mantenha acessível: responsivo até mobile, foco de teclado visível, `prefers-reduced-motion`,
  `aria-label` nos SVGs.
- Mantenha o tema editorial (creme + serifa). Se for mudar visual, é *reskin* — não reescrita.
- **Conteúdo novo ou editado no `<template id="seed">` só aparece pra quem não tem `localStorage`
  salvo** (ou como capítulo-semente novo com `data-key` inédito). Ao testar mudanças de conteúdo,
  limpe o `localStorage` do site ou use aba anônima.

## Como pré-visualizar
```bash
python3 -m http.server 8000      # http://localhost:8000
# ou apenas abra index.html no navegador
```
Peça ao Claude Code para tirar screenshots enquanto itera (ele roda um headless).

## Fontes / precisão
Números e estudos estão conferidos e embutidos no conteúdo (ver `reference/sources.md` e as
transcrições em `reference/transcripts/`). **Não invente dados novos**; se precisar acrescentar,
verifique.
