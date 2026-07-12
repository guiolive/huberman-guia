# Tema Medium — especificação (a partir da home medium.com)

Estética: minimalismo editorial, muito respiro, monocromático, serifa de alto contraste
para display, sem gradientes, sem sombras chamativas.

## Cores
- Fundo: creme quente `#F7F4EC` (aprox.). Alternativa de cartões/superfícies: branco `#FFFFFF`.
- Texto principal: quase-preto `#242424`. Títulos: `#191919`.
- Texto secundário/muted: `#6B6B6B`.
- Filetes/bordas: `#E6E3DA` (1px, discretos).
- Botão: preenchimento **preto** `#191919`, texto branco.
- Único acento de marca possível (usar com MUITA parcimônia, se usar): verde Medium `#1A8917`.

## Tipografia
- **Display (serifa):** o Medium usa GT Super (proprietária). Substituto Google Fonts fiel:
  **"Fraunces"** (variável, com `opsz`) ou **"Source Serif 4"**. Usar peso alto (600–800) e
  `letter-spacing` levemente negativo nos títulos grandes. Hero enorme, alinhado à esquerda.
- **Corpo:** o Medium usa serifa (Charter) para leitura. Para este guia, pode-se usar
  **"Source Serif 4"** no corpo (mais fiel) OU um sans limpo (**"Inter"**) — escolher uma e ser
  consistente. O subtítulo do hero na home é sans.
- **Utilitário/rótulos:** sans discreto (Inter) ou monoespaçado leve para captions.

Sugestão de import:
```html
<link href="https://fonts.googleapis.com/css2?family=Fraunces:opsz,wght@9..144,400;9..144,600;9..144,700;9..144,900&family=Source+Serif+4:opsz,wght@8..60,400;8..60,600&family=Inter:wght@400;500;600&display=swap" rel="stylesheet">
```

## Layout / componentes
- **Nav topo:** wordmark serifado "à la Medium" à esquerda; links à direita ("Nossa história",
  "Assinatura", etc. — adaptar para as seções do guia). Filete 1px embaixo. Fundo creme.
- **Hero:** título display gigante alinhado à esquerda + subtítulo curto sans + **botão pílula preto**
  ("Começar a ler" / "Ler o guia"). Muito espaço em branco.
- **Botão:** pílula totalmente arredondada, padding generoso (~14px 28px), preto sólido,
  texto branco, sem sombra. Hover: leve escurecer/opacidade.
- **Corpo das seções:** coluna de leitura estreita (~680–720px), tipografia grande e arejada,
  filetes finos separando blocos. Zero neon.

## O que remover do visual atual
- Fundo escuro e os `radial-gradient` do body.
- Brilhos/`drop-shadow` neon, `text-transparent` com gradiente forte.
- Pulsos animados fortes (suavizar para micro-interações discretas).

## O que manter
- Toda a estrutura semântica, IDs, seções, flashcards e scripts.
- A codificação funcional das 4 cores — porém **traduzida** (ver CLAUDE.md, "ponto de decisão").
