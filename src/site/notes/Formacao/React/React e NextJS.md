---
{"dg-publish":true,"permalink":"/formacao/react/react-e-next-js/","metatags":{"description":"é uma escolha popular para construir interfaces de usuário dinâmicas e interativas, focando na programação declarativa."},"noteIcon":2,"updated":"2025-09-26T19:44:49.955-03:00"}
---

#JavaScript #Webdesign #React #Nextjs

## React e NextJS

O React é uma **biblioteca de JavaScript** amplamente popular e de código aberto, mantida pela Meta (empresa do Facebook). Ela é considerada uma ferramenta que **dividiu a história do desenvolvimento para a web** e é extremamente relevante para a construção de interfaces de usuário (UI).

O React é uma escolha popular para construir **interfaces de usuário dinâmicas e interativas**, focando na **programação declarativa**.

### Conceitos Fundamentais do React

Os três conceitos centrais para a construção de aplicações React são: **Componentes**, **Propriedades (Props)** e **Estado (State)**.

  #### 1. Componentes e JSX

O React é baseado em componentes, permitindo a construção de interfaces com **componentização e modularização**.

- **Componentes Funcionais:** Um componente é, fundamentalmente, uma função que retorna uma estrutura de marcação. Você pode pensar em um componente como um trecho da sua aplicação, como um cabeçalho, um rodapé ou uma tabela.
- **JSX:** O código dentro dos componentes é escrito em JSX (JavaScript XML), uma sintaxe estendida que permite misturar JavaScript com HTML ou xHTML. Para acessar parâmetros da função ou lógica JavaScript dentro da marcação JSX, você deve envolver o trecho em **chaves `{}`**.

#### 2. Propriedades (Props)

As propriedades são usadas para **exibir dados** e personalizar componentes, funcionando como uma forma de passar informações de um componente para outro.

#### 3. Estado (State) e Interatividade

O conceito de estado é crucial para adicionar **interatividade**.

- **Estado:** O estado (`State`) refere-se aos dados que pertencem a uma instância de componente e que podem evoluir.
- **Hooks:** Para gerenciar o estado, utiliza-se o **`useState` Hook**. Essa função retorna dois elementos: o primeiro é o valor do estado (o número, por exemplo) e o segundo é sempre a função que altera esse valor. Você não deve alterar o valor do estado diretamente.
- **Manipulação de Eventos:** A interatividade também é implementada com manipuladores de eventos (event handlers). Eventos são nomeados em `camelCase`, como `onClick`, `onChange` (para campos de input) ou `onSubmit` (para formulários).

### Next.js

O Next.js é um **Framework construído sobre o React** e é o framework full stack recomendado pela própria documentação do React. O Next.js utiliza o React por baixo dos panos e traz recursos que otimizam o desempenho e a produtividade.

O Next.js aproveita a arquitetura React introduzindo os conceitos de **Server Components** e **Client Components**.

|Tipo de Componente|Uso Principal|Características no Next.js|
|:--|:--|:--|
|**Server Component**|Busca de dados, lógica de negócio no servidor.|É o padrão quando você cria um componente. É executado no servidor (server-side rendering - SSR), o que geralmente resulta em menos JavaScript enviado para o cliente.|
|**Client Component**|Interatividade (cliques, estados), uso de Hooks (`useState`, `useEffect`), acesso a recursos do navegador (browser).|Deve ser explicitamente marcado com a diretiva **`'use client'`** no topo do arquivo.|

O uso do `'use client'` é necessário quando você precisa de interatividade, pois o Next.js tenta, por padrão, pré-renderizar a página no servidor.

Em termos de arquitetura, um **Server Component pode renderizar Client Components**, permitindo que você combine rotas rápidas e renderizadas no servidor com a interatividade do lado do cliente onde for estritamente necessário.

### Programação Declarativa

O React é uma biblioteca declarativa. A programação declarativa é o método preferido para construir interfaces de usuário, pois acelera o processo de desenvolvimento.

- **Programação Imperativa:** O desenvolvedor gasta tempo escrevendo instruções passo a passo sobre _como_ a interface deve ser atualizada.
- **Programação Declarativa:** O desenvolvedor descreve _o que_ ele quer mostrar (por exemplo, um `<H1>`) e o React se encarrega de descobrir _como_ atualizar o DOM (Document Object Model) por você.

A base do React, que permite que você aprenda uma vez e aplique em diferentes plataformas, é essencial para qualquer profissional de tecnologia que busca mobilidade entre tecnologias e frameworks.

### Referências

- [Introduction to React](https://www.w3schools.com/react/react_intro.asp)
- [Início rápido – React](https://pt-br.react.dev/learn)
- [Learn Next.js - The React Framework](https://nextjs.org/learn)

[[Webdesign\|Webdesign]] - [[Formacao/Formação React Developer\|Formação React Developer]]
