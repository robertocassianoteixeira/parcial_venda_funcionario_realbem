# 📊 Parcial de Vendas

Sistema web para consulta de parcial de vendas por filial.  
Funciona 100% no navegador — nenhum dado vai para servidores externos além do próprio GitHub.

---

## 🏗 Arquitetura

```
┌─────────────────────┐        GitHub Repo         ┌──────────────────────┐
│   admin.html        │  ──── publica dados.json ──▶│   index.html         │
│   (você acessa)     │                             │   (lojas acessam)    │
│                     │                             │                      │
│  • Upload da xlsx   │                             │  • Busca por filial  │
│  • Publica via API  │                             │  • Lê dados.json     │
└─────────────────────┘                             └──────────────────────┘
```

- **`admin.html`** → você faz upload da planilha → dados são salvos no repositório
- **`index.html`** → as filiais acessam → lê automaticamente o `dados.json` do repositório
- **`dados.json`** → gerado pelo admin, contém os dados convertidos da planilha

---

## 🚀 Configuração inicial (uma única vez)

### 1. Criar o repositório

1. Acesse [github.com](https://github.com) e faça login
2. **New repository** → nome: `parcial-vendas` → **Public** → **Create**

### 2. Subir os arquivos

No repositório, clique em **uploading an existing file** e envie os 3 arquivos:
- `index.html`
- `admin.html`
- `dados.json`

Clique em **Commit changes**.

### 3. Ativar GitHub Pages

1. **Settings** → **Pages**
2. Branch: `main` / pasta: `/ (root)` → **Save**
3. Aguarde ~1 min

Seus endereços ficam:
| Página | URL |
|--------|-----|
| Filiais | `https://SEU_USUARIO.github.io/parcial-vendas/` |
| Admin | `https://SEU_USUARIO.github.io/parcial-vendas/admin.html` |

### 4. Gerar o token do GitHub

1. Acesse: [github.com/settings/tokens/new](https://github.com/settings/tokens/new)
2. **Note**: `ParcialVendas`
3. Marque apenas o escopo: ✅ **repo**
4. **Generate token** → copie o token (começa com `ghp_...`)

### 5. Configurar o admin

1. Abra `admin.html` no seu navegador
2. Preencha: **Usuário GitHub**, **Nome do repositório** (`parcial-vendas`), **Token**
3. Clique em **Salvar configuração** — fica salvo no navegador, não precisa repetir

---

## 🔄 Uso diário

1. Abra `admin.html`
2. Arraste a planilha `.xlsx` atualizada
3. Clique em **Publicar dados**
4. Pronto — as filiais já veem os dados atualizados em `index.html`

---

## 📋 Formato da planilha esperado

| Linha | Conteúdo |
|-------|----------|
| 1 | Texto do período (ex: `acumulado até o dia 14/05`) |
| 2 | Cabeçalhos |
| 3+ | Dados |

**Colunas (em ordem):**

| Coluna | Conteúdo |
|--------|----------|
| A | Filial |
| B | Vendedor |
| C | Venda acumulada (R$) |
| D | Ticket médio acumulado |
| E | Qtd de vendas acumuladas |
| F | Venda de ontem (R$) |
| G | Ticket médio de ontem |
| H | Qtd de vendas de ontem |

---

## 🖨 Imprimir / exportar PDF

Na tela do relatório, clique em **🖨 Imprimir** e selecione **Salvar como PDF**.

---

## 🛠 Tecnologias

- HTML + CSS + JavaScript puro (sem frameworks)
- [SheetJS](https://sheetjs.com/) — leitura de `.xlsx` no navegador
- [GitHub API](https://docs.github.com/en/rest) — publicação do `dados.json`
- GitHub Pages — hospedagem gratuita 24/7
