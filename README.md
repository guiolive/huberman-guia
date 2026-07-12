# huberman-guia

Guia de estudo (pt-BR) sobre **Neuroplasticidade & Dopamina**, baseado no Huberman Lab.
Página única, sem build: é só abrir `index.html`.

## Arquivos
```
huberman-guia/
├── index.html              ← o guia (HTML + CSS + JS inline). Está completo e funcional.
├── CLAUDE.md               ← contexto do projeto + tarefa atual (reskin Medium). LEIA PRIMEIRO.
├── PROMPT.md               ← prompt pronto pra colar no Claude Code.
├── README.md               ← este arquivo.
└── reference/
    ├── medium-theme.md     ← especificação do tema Medium (cores, fontes, botões).
    └── sources.md          ← episódios e estudos verificados.
```

## Como começar no Claude Code
1. Baixe e descompacte esta pasta em algum lugar, ex.: `~/projetos/huberman-guia`.
2. Instale o Claude Code (se ainda não tiver) — requer Node.js 18+:
   ```bash
   npm install -g @anthropic-ai/claude-code
   ```
   (Se algo mudou na instalação, confira a doc oficial em https://docs.claude.com .)
3. Entre na pasta e abra:
   ```bash
   cd ~/projetos/huberman-guia
   claude
   ```
4. Cole o conteúdo de `PROMPT.md` como primeira mensagem. O Claude Code vai ler o `CLAUDE.md`
   automaticamente e seguir daí.

## Pré-visualizar a qualquer momento
```bash
python3 -m http.server 8000     # http://localhost:8000
# ou só abrir index.html no navegador
```
