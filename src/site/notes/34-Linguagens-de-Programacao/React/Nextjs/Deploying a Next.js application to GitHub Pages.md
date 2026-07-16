---
{"dg-publish":true,"permalink":"/34-linguagens-de-programacao/react/nextjs/deploying-a-next-js-application-to-git-hub-pages/","metatags":{"description":"configuração do projeto Next.js para exportação estática e a configuração do GitHub Pages para servir os arquivos exportados."},"noteIcon":2,"updated":"2026-07-16T12:26:52.753-03:00","dg-note-properties":{"topics":["Aplicação Full-Stack","Nextjs"]}}
---


# Deploying a Next.js application to GitHub Pages

#Webdesign #Nextjs #github 

A implantação de um aplicativo Next.js no GitHub Pages envolve a configuração do projeto Next.js para exportação estática e a configuração do GitHub Pages para servir os arquivos exportados.

## 1. Configurar exportação Next.js

Modificar `next.config.js`: Adicionar configuração `output: 'export'` isto diz ao Next.js para exportar para HTML, CSS e arquivos JavaScript.

```javascript
    /** @type {import('next').NextConfig} */
    const nextConfig = {
      output: 'export',
      // Optional: Configure basePath and assetPrefix se GitHub tem URL repositório nome,
      // por exemplo, se sua URL é https://<username>.github.io/<repo-name>/
      // basePath: '/<repo-name>',
      // assetPrefix: '/<repo-name>/',
    };

    module.exports = nextConfig;
```

- Se seu GitHub Pages URL incluir um nome de repositório  (e.g., `https://<username>.github.io/<repo-name>/`), você precisará configurar a `basePath` e `assetPrefix` em `next.config.js` para garantir o correto asset loading.

## 2. Compilar (Build)

Executar comando: next.js gera arquivos estáticos no diretório de saída especificado (em `next.config.js`)

`npm run build` ou  `yarn build`

## 3 Deploy para o Github Pages

### Opção A - Manual (gh-pages package)

Instalar o pacote `ghpages`

`npm install gh-pages --save-dev`

adicionar deploy scripts para o  `scripts.json`:

```json
"scripts": {
          "predeploy": "npm run build",
          "deploy": "gh-pages -d out"
        }
```

Executar o deploy script:

`npm run deploy`

Isto irá fazer o build do seu projeto e o  push para o diretório de saída para a `gh-pages` branch em seu repositorio.

- **Configure GitHub Pages:** Na configurações do seu repositório, em Settings > Pages. Em "Source," selecione o `gh-pages` branche salve.

### **Option B: Automated Deployment (using GitHub Actions):**

- Crie um arquivo GitHub Actions workflow (e.g., `.github/workflows/deploy.yml`) em seu repositorio.
- Configure o workflow para build seu projeto Next.js e fazer o deploy para o diretório de saída `out` no GitHub Pages. GitHub mostra um modelo: template for Next.js deployments.

```json
name: Deploy Next.js to GitHub Pages

on:
  push:
	branches:
	  - main # Or your default branch

jobs:
  build-and-deploy:
	runs-on: ubuntu-latest
	steps:
	  - name: Checkout
		uses: actions/checkout@v4

	  - name: Setup Node.js
		uses: actions/setup-node@v4
		with:
		  node-version: '18' # Or your desired Node.js version

	  - name: Install dependencies
		run: npm install

	  - name: Build Next.js app
		run: npm run build

	  - name: Deploy to GitHub Pages
		uses: peaceiris/actions-gh-pages@v3
		with:
		  github_token: ${{ secrets.GITHUB_TOKEN }}
		  publish_dir: ./out # Or your custom output directory
```

- Configure o GitHub Pages: para as configurações do seu repositório em Settings > Pages. Em "Build and Deployment," selecione "GitHub Actions" como código (source). 

## 4. Verifique o Deployment

Depois de compilado (deploy), sua aplicação Next.js será accessível no GitHub Pages URL (e.g., https://<username>.github.io/<repository-name>/).

## Referências

- [Getting Started: Deploying \| Next.js](https://nextjs.org/docs/app/getting-started/deploying)
- [GitHub - nextjs/deploy-github-pages: Next.js template to deploy to GitHub Pages as a static site.](https://github.com/nextjs/deploy-github-pages)
- [An Extendable Obsidian Publish alternative using Next.JS \| Linked Blog Starter](https://linked-blog-starter.vercel.app/home)
- [Building and testing Node.js - GitHub Docs](https://docs.github.com/en/actions/tutorials/build-and-test-code/nodejs)
- [Dependabot updates in Github \| Next.js Documentation \| supastarter - SaaS starter kit & boilerplate](https://supastarter.dev/docs/nextjs/codebase/dependabot)
