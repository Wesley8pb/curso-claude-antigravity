# Guia de Deploy — Netlify

## O que está nesta pasta

```
deploy/
├── index.html          ← site de divulgação (página principal)
├── netlify.toml        ← configuração de headers de segurança e cache
├── assets/
│   └── wesley-photo-clean.png
└── ementa/
    └── index.html      ← ementa completa do curso
```

---

## Antes de publicar — substitua os placeholders

Abra `index.html` e substitua:

| Placeholder | O que colocar |
|---|---|
| `[DATA 1]` | Data do Encontro 1 (ex: `12 jul. 2026`) |
| `[DATA 2]` | Data do Encontro 2 |
| `[DATA 3]` | Data do Encontro 3 |
| `#link-hotmart` | URL real da Hotmart (aparece 2× — no hero e no rodapé) |
| `R$ XXX,00` | Preço do curso |
| `https://SEUDOMINIO.netlify.app/` | URL após criar o site (aparece em `og:url` e `canonical`) |

Abra `ementa/index.html` e substitua:

| Placeholder | O que colocar |
|---|---|
| `https://SEUDOMINIO.netlify.app/ementa/` | URL da ementa após criar o site |

---

## Deploy via Netlify Drop (mais rápido)

1. Acesse **[app.netlify.com/drop](https://app.netlify.com/drop)**
2. Arraste a pasta **`deploy/`** para a área indicada
3. Aguarde o upload — o site já estará online em segundos
4. Copie a URL gerada (ex: `https://nome-aleatorio.netlify.app`)
5. Substitua os placeholders `https://SEUDOMINIO.netlify.app/` pela URL real
6. Faça novo upload da pasta para atualizar

> **Dica:** para ter uma URL personalizada (ex: `curso-claude-antigravity.netlify.app`), vá em **Site settings → Domain management → Options → Edit site name**.

---

## Deploy via GitHub + Netlify (recomendado para atualizações frequentes)

### 1. Criar repositório no GitHub

```bash
git init
git add .
git commit -m "deploy inicial"
gh repo create curso-claude-antigravity --public --push --source=.
```

### 2. Conectar ao Netlify

1. Acesse **[app.netlify.com](https://app.netlify.com)** → **Add new site → Import an existing project**
2. Escolha **GitHub** e selecione o repositório
3. Em **Build settings**:
   - Build command: *(deixar em branco)*
   - Publish directory: `.` *(ponto — a raiz do repositório)*
4. Clique em **Deploy site**

### 3. Atualizar o site no futuro

```bash
git add .
git commit -m "atualiza datas e preço"
git push
```
O Netlify detecta o push e republica automaticamente.

---

## Verificar após o deploy

- [ ] Site abre em `https://seudominio.netlify.app`
- [ ] Botão **GARANTIR MINHA VAGA** redireciona para a Hotmart
- [ ] Botão **Ver ementa completa** abre a ementa em nova aba
- [ ] Botão **← Voltar ao site do curso** (na ementa) retorna à página principal
- [ ] Foto do instrutor aparece corretamente
- [ ] Testar no celular (layout responsivo)
- [ ] Headers de segurança ativos — verificar em [securityheaders.com](https://securityheaders.com)
