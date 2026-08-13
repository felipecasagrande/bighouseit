# Implantação no GitHub Pages

## Opção recomendada: publicar a partir da branch `main`

1. No GitHub, crie um repositório, por exemplo:
   - `bighouseit-site`

2. Faça upload de **todos os arquivos e pastas deste pacote**, preservando a pasta `assets`.

3. Confirme que `index.html` está na raiz do repositório.

4. No repositório:
   - `Settings`
   - `Pages`
   - em `Build and deployment`, selecione `Deploy from a branch`
   - branch: `main`
   - folder: `/(root)`
   - clique em `Save`

5. Aguarde o primeiro deploy. O GitHub mostrará a URL pública na própria tela de Pages.

## Atualizações futuras

Edite qualquer arquivo e faça commit na branch `main`.
O Pages republicará automaticamente o conteúdo da branch configurada.

---

# Domínio personalizado: bighouseit.com

Recomendo primeiro confirmar que o site funciona no endereço do GitHub Pages. Depois configure o domínio.

## 1. Dentro do GitHub

No repositório:

- `Settings`
- `Pages`
- `Custom domain`
- informe: `bighouseit.com`
- salve

O GitHub poderá criar o arquivo `CNAME` automaticamente quando a publicação é feita por branch.

## 2. No provedor DNS

Para o domínio raiz (`bighouseit.com`), use registros A apontando para os endereços oficiais do GitHub Pages:

- `185.199.108.153`
- `185.199.109.153`
- `185.199.110.153`
- `185.199.111.153`

Nome/Host: `@`

Para `www`, crie um registro CNAME:

- Nome/Host: `www`
- Destino: `SEU-USUARIO.github.io`

Troque `SEU-USUARIO` pelo seu usuário real do GitHub.

## 3. Não altere os registros de e-mail

Ao configurar o site, altere apenas os registros necessários para web (`A` do domínio raiz e `CNAME` do `www`).

Não apague registros de:
- MX
- SPF
- DKIM
- DMARC
- validações de e-mail

Isso evita interferir no serviço de e-mail do domínio.

## 4. HTTPS

Depois que o DNS estiver validado pelo GitHub:
- volte em `Settings > Pages`
- ative `Enforce HTTPS`

A emissão do certificado pode levar algum tempo após a alteração do DNS.

## 5. Arquivo CNAME.example

O pacote contém `CNAME.example` somente como referência.
Não é necessário renomeá-lo manualmente se você configurar o domínio pelo painel `Settings > Pages`.

---

# Teste local

No Windows, você pode abrir `index.html` diretamente no navegador.

Para testar com um servidor local simples, se tiver Python instalado:

```bash
python -m http.server 8080
```

Depois abra no navegador:

```text
http://localhost:8080
```

---

# Estrutura esperada no GitHub

```text
bighouseit-site/
├─ index.html
├─ styles.css
├─ script.js
├─ 404.html
├─ robots.txt
├─ sitemap.xml
├─ site.webmanifest
├─ .nojekyll
├─ README.md
├─ DEPLOY_GITHUB_PAGES.md
└─ assets/
   ├─ logo-neon.webp
   ├─ banner-linkedin.webp
   ├─ og-cover.jpg
   └─ favicon.png
```
