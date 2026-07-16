---
{"dg-publish":true,"permalink":"/34-linguagens-de-programacao/react/nextjs/componentes-no-next-js/","metatags":{"description":"Guia completo sobre componentes no Next.js, abordando desde a base React até as diferenças entre App Router e Pages Router."},"noteIcon":2,"updated":"2026-07-16T12:09:01.081-03:00","dg-note-properties":{"topics":["Webdesign","Aplicação Full-Stack","React","Nextjs"]}}
---

# Componentes no NextJS

#JavaScript #Webdesign #React #Nextjs 

Este guia explica os componentes e conceitos fundamentais do Next.js. O Next.js é um framework React que permite criar aplicações web estáticas, dinâmicas e híbridas com alto desempenho e SEO nativo.

>[!info] **Nota importante:** O Next.js possui duas arquiteturas de roteamento: **App Router** (recomendada para projetos novos, introduzida no Next.js 13) e **Pages Router** (legada, mas ainda muito presente em sistemas existentes). Este artigo aborda ambas, destacando as diferenças.

---

## 1. A Base: Componentes React

No Next.js, tudo começa com componentes React. Eles são blocos reutilizáveis que compõem a interface.

```jsx
// components/Button.js
const Button = ({ onClick, children }) => (
  <button onClick={onClick} className="btn">
    {children}
  </button>
);

export default Button;
```

### Componentes Compostos

Você pode aninhar componentes dentro deles mesmos para criar estruturas complexas:

```jsx
const Card = ({ title, content }) => (
  <div className="card">
    <h2 className="card-title">{title}</h2>
    <p className="card-content">{content}</p>
  </div>
);
```

---

## 2. A Nova Era: App Router (Next.js 13+)

A **App Router** utiliza a pasta `app/` e introduz o conceito de **Server Components** e **Client Components**.

### Server Components vs. Client Components

-  **Server Components (Padrão):** Renderizados no servidor. Não interagem com o navegador (sem `useState`, `useEffect`). Melhor para performance e SEO.
-  **Client Components:** Adicione `'use client'` no topo do arquivo. Necessários para interatividade (eventos, hooks).

### Estrutura de Rotas e Layouts

No App Router, arquivos `page.js` definem a rota, e `layout.js` define estruturas comuns (header/footer).

```jsx
// app/layout.js
export default function RootLayout({ children }) {
  return (
    <html lang="pt-BR">
      <body>
        <header>Meu Header</header>
        <main>{children}</main>
      </body>
    </html>
  );
}
```

---

## 3. O Legado: Pages Router

Se você estiver trabalhando em um projeto antigo, a estrutura é baseada na pasta `pages/`.

### Páginas como Rotas

Cada arquivo na pasta `pages/` corresponde a uma rota (ex: `pages/home.js` → `/home`).

```jsx
// pages/index.js
export default function Home() {
  return <h1>Bem-vindo ao Next.js (Pages Router)!</h1>;
}
```

### Documentos (Customização do Head)

Para personalizar o `<html>` ou `<head>` globalmente na Pages Router, utiliza-se `pages/_document.js`.

---

## 4. Rotas Dinâmicas

Ambas as arquiteturas utilizam colchetes `[ ]` para capturar parâmetros na URL.

```jsx
// pages/users/[id].js ou app/users/[id]/page.js
import { useRouter } from 'next/router'; // No App Router, use hooks específicos

export default function UserPage({ params }) {
  // params.id estará disponível
  return <h1>Usuário ID: {params.id}</h1>;
}
```

---

## 5. API Routes e Middleware

-  **API Routes:** Crie endpoints rápidos na pasta `pages/api` (Pages Router) ou `app/api/.../route.js` (App Router).
-  **Middleware:** Intercepte requisições antes de chegarem às rotas. Útil para autenticação.

---

## 6. Styling e Performance

-  **CSS Modules:** Evite conflitos de estilo. Nomeie como `Nome.module.css`.
-  **Imagens:** Utilize o componente nativo `next/image` para otimização automática.

```jsx
import Image from 'next/image';

<Image src="/logo.png" alt="Logo" width={50} height={50} />
```

---

## 7. Comparativo de Renderização (Data Fetching)

| Técnica | Descrição | Uso |
| --- | --- | --- |
| **SSG** | Gerado no *build time*. | Conteúdo estático (blogs). |
| **SSR** | Renderizado a cada requisição. | Dados sensíveis (login). |
| **ISR** | Atualiza páginas em segundo plano. | Lojas, CMS. |

---

## Resumo

Os componentes no Next.js evoluíram para permitir aplicações modernas com:
1.  **Performance:** Server Components por padrão.
2.  **SEO:** Renderização otimizada.
3.  **Organização:** Estrutura clara entre Layouts e Páginas.

## Referências

- [Getting Started: Server and Client Components \| Next.js](https://nextjs.org/docs/app/getting-started/server-and-client-components)
- [Componentes React integrados – React](https://pt-br.react.dev/reference/react/components)
