---
{"dg-publish":true,"permalink":"/formacao/react/nextjs/novo-projeto-nextjs/","metatags":{"description":"Como transformar uma ideia em uma aplicação web funcional, moderna e pronta."},"noteIcon":2,"updated":"2025-09-26T16:37:56.803-03:00"}
---

#JavaScript #Webdesign #React #Nextjs

O Next.js é o _framework_ React full stack **mais famoso da atualidade** e **oficialmente recomendado** pela própria documentação do React. Ele utiliza o React por baixo dos panos, mas adiciona recursos e otimizações, tornando-o o caminho preferencial para iniciantes que desejam criar aplicações web modernas.

A seguir, um guia passo a passo para criar um projeto React utilizando o Next.js, com base nos fundamentos essenciais da biblioteca e do _framework_:

## Passo 1: Configuração do Ambiente (Pré-requisitos)

Antes de começar, você deve ter duas ferramentas instaladas em sua máquina:

1. **Node.js:** É essencial para executar código JavaScript fora do navegador e para instalar pacotes. A versão mínima recomendada do Node.js para Next.js é **18.17.0**. A instalação do Node.js também fornece o **npm** (Node Package Manager).
2. **Editor de Código:** O **Visual Studio Code (VS Code)** é o editor mais utilizado e recomendado.

## Passo 2: Criação do Projeto Next.js

Para iniciar o projeto, abra o terminal (ou Prompt de Comando/PowerShell):

1. **Comando de Iniciação:** Execute o comando `npx create-next-app@latest`.
    - O `npx` é um gerenciador de pacotes que executa comandos de criação, facilitando a inicialização.
2. **Configurações Iniciais:** O utilitário CLI fará algumas perguntas:
    - **TypeScript:** **Recomendado** (`Yes`) para adicionar tipagem estática e garantir a segurança do código.
    - **ESLint:** **Recomendado** (`Yes`) para verificar e padronizar o código.
    - **Tailwind CSS:** **Recomendado** (`Yes`). Este é um _framework_ CSS _utility-first_ muito popular no ecossistema React/Next.js.
    - **Diretório `src`:** **Recomendado** (`Yes`) para manter o código da aplicação separado dos arquivos de configuração.
    - **App Router:** **Recomendado** (`Yes`). Este é o sistema de roteamento mais moderno do Next.js.

## Passo 3: Execução e Estrutura Inicial

1. **Acessar e Rodar:** Navegue até a pasta do projeto e inicie o servidor de desenvolvimento com o comando:

    ```
    npm run dev
    ```

    Isso compilará o projeto e o servidor será executado em **`localhost:3000`**.
    
2. **Estrutura de Pastas:** O Next.js utiliza o **File-based Routing** (roteamento baseado em sistema de arquivos).
    
    - **`src/app`:** É a pasta mais importante, pois o roteamento é baseado nas pastas criadas dentro dela.
    - **`page.tsx`:** Este arquivo define o **conteúdo** que será exibido em uma rota específica (por exemplo, `app/page.tsx` é a página inicial).
    - **`layout.tsx`:** Define a **estrutura global** ou o _template_ que envolve as páginas (cabeçalhos, rodapés, etc.).

## Passo 4: Desenvolvimento com Fundamentos React

O coração do desenvolvimento React é o conceito de **Componentes**.

1. **Componentes e JSX:** Um componente é uma **função JavaScript** que retorna o que será exibido na interface do usuário.
    
    - **JSX:** É a sintaxe estendida utilizada nos componentes, que **mistura JavaScript e HTML**.
    - **Convenção:** Componentes devem ter a **primeira letra maiúscula** (PascalCase).
    - **Expressões JavaScript:** Para usar variáveis, lógica ou funções dentro do JSX, envolva o código em **chaves `{}`**.
2. **Propriedades (Props):** Permitem **passar dados** de um componente pai para um componente filho.
    
    - As _props_ são recebidas como um **objeto** no argumento da função do componente.
3. **Estado (State) e Interatividade:** O `State` (estado) é usado para gerenciar dados que mudam e adicionam **interatividade** à aplicação.
    
    - **Hooks:** Para gerenciar o estado, usa-se o **`useState` Hook**. Ele retorna o valor atual do estado e uma função para alterá-lo (função _setter_).
    - **Interatividade (Client Components):** Por padrão, no Next.js (App Router), os componentes são **Server Components**. Para que um componente use Hooks (`useState`, `onClick`, `useEffect`) e lide com interatividade, ele deve ser transformado em um **Client Component** adicionando a diretiva **`'use client'`** no topo do arquivo.

## Passo 5: Criando Rotas e Server Components

1. **Criação de Rotas:** Crie uma nova pasta dentro de `src/app` (ex: `app/dashboard`). Dentro dessa pasta, crie um arquivo **`page.tsx`**. A URL será automaticamente `/dashboard`.
2. **Rotas Dinâmicas:** Para rotas com segmentos variáveis (ex: `/produtos/[id]`), crie uma pasta com o nome do parâmetro entre colchetes (ex: `[id]`). O valor do parâmetro pode ser acessado em Server Components através da prop `params`.
3. **Server Components (Padrão):** Por padrão, um componente Next.js é um Server Component, executado no lado do servidor.
    - **Vantagem:** Permite que o componente seja **assíncrono** (`async` function) e busque dados diretamente (data fetching), sem a necessidade de Hooks como `useEffect`.
4. **Server Actions e Formulários:** O Next.js permite o uso de **Server Actions**, que são funções assíncronas executadas no servidor, mas chamadas a partir do cliente (por exemplo, em formulários).
    - **Diretiva:** Server Actions devem ser marcadas com `'use server'`.
    - **Uso:** Em formulários, a Server Action pode ser passada diretamente para o atributo `action` do `<form>`.

O Next.js (e o React moderno) permite misturar Server Components (para eficiência e SEO) e Client Components (para interatividade), aproveitando o melhor de ambos os mundos.

### Referências

- [Getting Started: Installation \| Next.js](https://nextjs.org/docs/app/getting-started/installation)
- [Publicando na Vercel](https://vercel.com/new?utm_source=create-next-app)
