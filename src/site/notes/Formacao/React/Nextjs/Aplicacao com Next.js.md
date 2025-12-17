---
{"dg-publish":true,"permalink":"/formacao/react/nextjs/aplicacao-com-next-js/","metatags":{"description":"Como transformar uma ideia em uma aplicação web funcional, moderna e pronta."},"noteIcon":2,"updated":"2025-09-26T15:56:13.462-03:00"}
---

#JavaScript #Webdesign #React #Nextjs

## Tutorial: Criando sua Primeira Aplicação Full-Stack com Next.js

Como transformar uma ideia em uma aplicação web funcional, moderna e pronta para o mundo real. Ao final deste guia, você terá construído do zero e implantado uma aplicação full-stack, dominando as habilidades essenciais para criar seus próprios projetos com Next.js.

### 1. Introdução: Por que Next.js?

Next.js é um framework React que a própria equipe do React recomenda para construir aplicações full-stack. Mas o que isso significa na prática? Para entender o poder do Next.js, é crucial diferenciá-lo de uma abordagem mais tradicional como uma Single Page Application (SPA), popularizada por ferramentas como o `create-react-app`.

Em uma SPA, o navegador do usuário recebe um arquivo JavaScript massivo. Ele precisa baixar e executar todo esse código para só então exibir o conteúdo da página. Isso pode levar a um carregamento inicial lento e prejudicar a otimização para mecanismos de busca (SEO), já que os "robôs" do Google têm dificuldade em "ler" conteúdo que depende de JavaScript para ser exibido.

O Next.js resolve esses problemas com uma arquitetura que renderiza o conteúdo no servidor antes de enviá-lo ao cliente. O resultado é uma experiência de usuário mais rápida e uma aplicação amigável para os buscadores.

A tabela abaixo resume as diferenças fundamentais:

|   |   |   |
|---|---|---|
|Característica|SPA (Ex: Create React App)|Next.js (SSR/SSG)|
|**Renderização Inicial**|O cliente baixa um JavaScript pesado e executa para ver o conteúdo.|O servidor envia um HTML já com o conteúdo, melhorando a percepção de velocidade.|
|**SEO (Otimização para Buscadores)**|Ruim por padrão, pois os buscadores precisam executar JavaScript para indexar o conteúdo.|Excelente, pois o conteúdo já está no HTML inicial, facilitando a indexação.|
|**Complexidade de Código**|Todo o código (frontend e backend) fica em um único arquivo JavaScript massivo.|Permite a criação de componentes que rodam no servidor (Server Components), mantendo lógica sensível e acesso a banco de dados fora do cliente.|

Agora que você entende o "porquê", vamos ao "como". Vamos construir juntos uma aplicação completa para colocar esses conceitos em prática.

### 2. Planejamento e Stack de Tecnologia

Antes de escrever a primeira linha de código, um bom desenvolvedor planeja. É crucial entender o que vamos construir e quais ferramentas usaremos. Pense nisso como montar um quebra-cabeça: cada tecnologia é uma peça que se encaixa para formar a solução completa.

#### 2.1. O que Vamos Construir: App "Dragon Runner"

Nosso projeto será o "Dragon Runner", um aplicativo para atletas registrarem e acompanharem seus treinos de corrida. Os requisitos são claros:

- **Landing Page:** Uma página atrativa para os usuários se registrarem.
- **Autenticação:** Permitir que atletas criem uma conta e façam login.
- **Registro de Treinos:** Funcionalidade para registrar treinos com data/hora, distância, duração e calorias.
- **Visualização de Dados:** Consultar treinos passados em uma tabela e visualizar a evolução em um gráfico.

#### 2.2. Nossas Ferramentas (O Quebra-Cabeça Tecnológico)

Para construir o "Dragon Runner", selecionamos uma stack de tecnologia moderna e poderosa. Cada "peça" do nosso quebra-cabeça tem um papel específico:

- **Framework Full-Stack:** **Next.js** (usando **React**), que nos permite construir tanto o frontend quanto o backend em um único projeto.
- **Linguagem de Programação:** **TypeScript** no frontend e no backend. A grande vantagem é usar uma única linguagem para toda a aplicação, garantindo segurança de tipos e consistência.
- **Estilização:** **Tailwind CSS**, para uma abordagem _utility-first_ que nos permite criar interfaces bonitas e responsivas de forma rápida e eficiente.
- **Componentes de UI:** **ShadCN/UI**, uma coleção de componentes reutilizáveis, acessíveis e fáceis de customizar, que nos poupará tempo na construção da interface.
- **Banco de Dados:** **PostgreSQL**, através do **Neon**, um serviço de banco de dados serverless que facilita a configuração e o gerenciamento.
- **ORM (Mapeamento Objeto-Relacional):** **Prisma**, uma ferramenta incrível que simplifica a comunicação com o banco de dados, permitindo escrever queries de forma segura e intuitiva com TypeScript.
- **Autenticação e Autorização:** **Clerk**, um serviço que gerencia todo o fluxo de login, criação de contas e proteção de rotas, nos poupando de uma complexidade enorme.
- **Versionamento de Código:** **GitHub**, para mantermos um histórico do nosso código e colaborarmos de forma organizada.
- **Implantação (Deploy):** **Vercel**, a plataforma ideal para projetos Next.js, conhecida por sua simplicidade, performance e integração contínua com o GitHub.

Esta combinação de tecnologias é uma "receita" poderosa e moderna. Ao dominar essa stack, você estará preparado para construir aplicações web de alta qualidade, do conceito à produção.

Com o plano e as ferramentas em mãos, é hora de configurar nosso ambiente de desenvolvimento.

### 3. Configuração do Projeto e Ambiente

Vamos criar a estrutura inicial da nossa aplicação Next.js.

#### 3.1. Criando o Projeto

Abra seu terminal e execute o seguinte comando. O `create-next-app` é um assistente que fará algumas perguntas para configurar o projeto exatamente como precisamos.

```bash
npx create-next-app@latest
```

Responda às perguntas conforme a lista abaixo para mantermos o projeto alinhado com este tutorial:

- Would you like to use TypeScript? **Yes** - Para garantir segurança de tipos e um código mais robusto.
- Would you like to use ESLint? **Yes** - Para manter a qualidade e o padrão do nosso código.
- Would you like to use Tailwind CSS? **Yes** - Nossa escolha para estilização utility-first.
- Would you like to use `src/` directory? **Yes** - Para uma melhor organização dos arquivos do projeto.
- Would you like to use App Router? **Yes** - Este é o sistema de roteamento moderno e recomendado no Next.js que usaremos.
- Would you like to customize the default import alias? **Yes** - Para simplificar os caminhos de importação.

Após a instalação, entre na pasta do projeto e inicie o servidor de desenvolvimento com `npm run dev`. Acesse `http://localhost:3000` no seu navegador e você verá a página inicial padrão do Next.js.

#### 3.2. Entendendo a Estrutura de Pastas

A estrutura de pastas inicial pode parecer intimidadora, mas o conceito principal é simples. O foco está na pasta `app/`:

- **Roteamento Baseado em Pastas:** Com o App Router, cada pasta dentro de `app/` se torna uma rota na sua aplicação. Por exemplo, uma pasta `app/dashboard/` criará a rota `http://localhost:3000/dashboard`.
- **Arquivos Especiais:**
    - `layout.tsx`: Define um layout base que envolve todas as páginas. O conteúdo das páginas filhas é renderizado onde a prop `children` é colocada. É perfeito para adicionar elementos comuns como cabeçalhos e rodapés.
    - `page.tsx`: Define a interface de usuário (UI) específica de uma rota. É o conteúdo que será renderizado dentro do `layout.tsx`.
- **TSX (TypeScript com JSX):** Os arquivos com extensão `.tsx` são uma mistura de HTML e TypeScript. Isso permite criar componentes de forma declarativa e com a segurança de tipos do TypeScript, melhorando muito a experiência de desenvolvimento.

Agora que temos a estrutura base, o próximo passo lógico é garantir que apenas usuários autorizados possam acessar as partes principais da nossa aplicação. Vamos implementar a autenticação.

### 4. Autenticação de Usuários com Clerk

Adicionar autenticação do zero é um processo complexo e propenso a erros. Felizmente, serviços como o Clerk simplificam drasticamente essa tarefa.

#### 4.1. Configurando o Clerk

Siga estes passos para integrar o Clerk ao nosso projeto:

1. **Instalação:** Primeiro, instale a biblioteca do Clerk para Next.js.
2. **Variáveis de Ambiente:** Crie um arquivo chamado `.env.local` na raiz do seu projeto. Dentro dele, adicione as chaves de API que você obtém no dashboard do Clerk após criar uma nova aplicação.
3. **Envolver a Aplicação:** Vá para o arquivo `app/layout.tsx` e importe o `ClerkProvider`. Em seguida, envolva o elemento `<body>` com ele. Isso fará com que o contexto de autenticação do Clerk esteja disponível em toda a aplicação.

#### 4.2. Protegendo Rotas com Middleware

Middleware é um código que executa no servidor _antes_ de uma requisição ser completada. É o local perfeito para verificar se um usuário está autenticado antes de permitir o acesso a uma página.

1. Crie um arquivo chamado `middleware.ts` na raiz do seu projeto (fora da pasta `app/` ou `src/`).
2. Cole o seguinte código no arquivo. Ele usa o `clerkMiddleware` para proteger todas as rotas da aplicação, exceto as que definimos como públicas.
    - `createRouteMatcher`: Cria uma função que verifica se a rota da requisição corresponde a um dos padrões fornecidos.
    - `/`: Marcamos nossa página inicial como pública, para que novos usuários possam vê-la.
    - `auth().protect()`: Se a rota não for pública, esta função garantirá que o usuário esteja logado. Caso contrário, ele será redirecionado para a página de login.
    - `config`: O objeto `config` com a propriedade `matcher` informa ao Next.js em quais rotas o middleware deve ser executado, otimizando a performance.

Com a autenticação configurada, podemos agora construir a página principal da nossa aplicação, o dashboard, que estará devidamente protegida.

### 5. Roteamento e Construção da Página de Dashboard

Vamos criar a página `/dashboard`, que será o centro da nossa aplicação para usuários autenticados.

#### 5.1. Criando a Rota do Dashboard

Seguindo a convenção do App Router, criar uma nova rota é tão simples quanto criar uma pasta.

1. Dentro do diretório `app/`, crie uma nova pasta chamada `dashboard`.
2. Dentro da pasta `dashboard`, crie um arquivo `page.tsx`.
3. Adicione o seguinte código ao `app/dashboard/page.tsx`:
4. Agora, com o servidor rodando (`npm run dev`), tente acessar `http://localhost:3000/dashboard`. Como você ainda não está logado, o middleware do Clerk deve te redirecionar automaticamente para a página de login. Após criar uma conta e fazer login, você será levado ao dashboard.

#### 5.2. Construindo o Layout Básico do Dashboard

Agora, vamos começar a dar forma à interface do dashboard usando os componentes do ShadCN/UI.

1. Primeiro, vamos inicializar o ShadCN/UI no projeto e adicionar os componentes que usaremos. Execute os seguintes comandos no terminal:
2. Siga as instruções do assistente.
3. No arquivo `app/dashboard/page.tsx`, substitua o código anterior pela estrutura básica da página, com placeholders para as seções que construiremos.

Para que essas seções possam exibir e salvar dados reais, precisamos de um lugar para armazená-los. É hora de conectar nossa aplicação a um banco de dados.

### 6. Configurando o Banco de Dados com Prisma e Neon

Vamos usar o Prisma como nosso ORM para facilitar a interação com um banco de dados PostgreSQL serverless fornecido pelo Neon.

#### 6.1. Conectando ao Banco de Dados

1. Crie uma conta no [Neon](https://neon.tech/) e crie um novo projeto de banco de dados.
2. No dashboard do seu projeto Neon, localize a string de conexão do banco de dados (geralmente começa com `postgresql://...`).
3. Adicione essa string de conexão ao seu arquivo `.env.local` com a chave `DATABASE_URL`.

#### 6.2. Configurando o Prisma ORM

1. **Instalação:** Adicione o Prisma ao seu projeto.
2. **Inicialização:** Execute o comando de inicialização do Prisma.
3. Isso criará uma pasta `prisma` com um arquivo `schema.prisma`. Este arquivo é o coração da configuração do Prisma.
4. **Modelando os Dados:** Abra o arquivo `prisma/schema.prisma` e defina o modelo para a nossa tabela de treinos, a `TrainingSession`. O `externalUserId` será usado para vincular o treino ao usuário do Clerk.

#### 6.3. Sincronizando o Banco de Dados

Agora que nosso modelo está definido no `schema.prisma`, precisamos executar dois comandos essenciais:

1. **Sincronizar o Schema com o Banco de Dados:** Este comando lê seu `schema.prisma`, conecta-se ao banco de dados e cria as tabelas correspondentes. É a ponte entre seu código e a estrutura do banco.
2. **Gerar o Prisma Client:** Após sincronizar o banco, este comando gera um conjunto de tipos e funções TypeScript totalmente tipados com base no seu schema. É através deste "cliente" que nossa aplicação irá interagir com o banco de dados de forma segura e com autocomplete.

Com o banco de dados e o Prisma Client prontos, podemos criar a lógica de backend para salvar e buscar nossos dados.

### 7. Lógica de Backend com Server Actions

Server Actions são uma das funcionalidades mais poderosas do Next.js moderno. Elas são funções que você escreve e que rodam _exclusivamente no servidor_, mas que podem ser chamadas diretamente de seus componentes de frontend, como se fossem funções locais. Isso elimina a necessidade de criar APIs manualmente para tarefas de mutação de dados.

Primeiro, vamos garantir que estamos usando o Prisma da maneira correta, evitando criar múltiplas conexões com o banco de dados em ambiente de desenvolvimento.

1. Crie um arquivo `db.ts` dentro da pasta `app/lib/`.
2. Adicione o seguinte código para criar uma instância singleton do Prisma Client. Isso garante que apenas uma instância do cliente seja usada em toda a aplicação.

#### 7.1. Criando a Ação para Registrar um Treino ()

Agora, vamos criar as ações em um arquivo dedicado, usando nossa instância segura do Prisma.

1. Dentro de `app/lib/`, crie um arquivo `actions.ts`.
2. Adicione o seguinte código. Esta função receberá os dados do formulário e usará o Prisma Client para criar ou atualizar um registro no banco de forma segura.
    - `'use server';`: Marca todas as funções exportadas como Server Actions.
    - `auth()`: Obtém o ID do usuário de forma segura no servidor, vindo diretamente do Clerk. Isso impede que um usuário mal-intencionado tente se passar por outro.

#### 7.2. Criando a Ação para Buscar os Treinos ()

1. No mesmo arquivo `actions.ts`, adicione a função para buscar os treinos. Ela usará o ID do usuário autenticado para retornar apenas os treinos pertencentes a ele, de forma segura.

Com nossas ações de backend prontas, podemos finalmente construir a interface do usuário para interagir com elas.

### 8. Construindo a Interface do Dashboard (Frontend)

Agora vamos conectar as peças no frontend, criando componentes interativos que utilizam nossas Server Actions.

#### 8.1. O Formulário de Registro de Treinos

1. Dentro de `app/dashboard/`, crie uma pasta `_components/`. O sublinhado (`_`) no início do nome da pasta é uma convenção do Next.js App Router para indicar que ela não deve se tornar uma rota pública, permitindo organizar componentes sem afetar as URLs.
2. Dentro de `_components/`, crie o arquivo `DashboardForm.tsx`.
3. Marque o componente com `"use client"` no topo. Isso é necessário para componentes que usam hooks (como `useState`) ou interatividade do lado do cliente.
4. Construa o formulário usando os componentes do ShadCN. O ponto chave é a prop `action` no elemento `<form>`, que aponta diretamente para a nossa Server Action `upsertTrainingSession`.
5. Os nomes dos inputs (`name="distance"`) correspondem às chaves que a Server Action espera receber no `FormData`.

#### 8.2. A Tabela de Treinos

1. Crie o arquivo `DashboardTable.tsx` na mesma pasta `_components/`.
2. Este será um **Server Component assíncrono**. Isso nos permite chamar a função `getTrainingSessions` com `await` diretamente dentro do componente, buscando os dados no servidor antes de renderizar a UI.

#### 8.3. Visualização com Gráficos

1. Instale a biblioteca de gráficos do ShadCN/UI:
2. Crie o arquivo `DashboardChart.tsx` em `_components/`.
3. Este componente receberá os dados dos treinos como props e usará um gráfico de linha para mostrar a evolução da distância ao longo do tempo.

Aplicação desenvolvida! O último passo é compartilhar nossa criação com o mundo.

### 9. Implantação na Vercel

Implantar nosso projeto na Vercel é um processo surpreendentemente simples, graças à sua integração perfeita com Next.js e GitHub.

1. **Conectando ao GitHub:** Envie seu projeto para um novo repositório no GitHub.
2. **Configurando na Vercel:** Crie uma conta na Vercel e importe seu repositório do GitHub. A Vercel detectará automaticamente que é um projeto Next.js e aplicará as configurações padrão.
3. **Variáveis de Ambiente:** Vá para as configurações do seu projeto na Vercel e adicione todas as variáveis de ambiente que estão no seu arquivo `.env.local` (`NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY`, `CLERK_SECRET_KEY` e `DATABASE_URL`).
4. **Comando de Build:** Este é um passo crucial. Durante o processo de deploy, o ambiente de build da Vercel é limpo e precisa gerar o Prisma Client novamente a partir do schema. Para garantir que isso aconteça, edite seu arquivo `package.json` e adicione um script `postinstall`. A Vercel executa este script automaticamente após instalar as dependências.
5. Clique em "Deploy" na Vercel. A plataforma cuidará de todo o processo de build e, em poucos minutos, sua aplicação estará no ar, acessível por uma URL pública.

### 10. Conclusão

Parabéns! Você acaba de construir e implantar uma aplicação web full-stack completa com Next.js. Este projeto cobriu todo o ciclo de vida do desenvolvimento de software moderno.

Vamos recapitular o que você aprendeu:

- **Configuração de um projeto Next.js** com TypeScript e Tailwind CSS.
- **Autenticação e proteção de rotas** com Clerk e Middleware.
- **Conexão com um banco de dados PostgreSQL** usando Prisma de forma segura e eficiente, com o padrão Singleton.
- **Criação de lógica de backend** com Server Actions, garantindo que operações sensíveis e a verificação de identidade do usuário ocorram no servidor.
- **Construção de uma UI interativa** combinando o poder dos Server Components (para busca de dados) e Client Components (para interatividade).
- **Implantação contínua** com Vercel e GitHub, um fluxo de trabalho profissional para colocar seus projetos no ar.

O "Dragon Runner" é um ponto de partida. Sinta-se à vontade para expandi-lo, adicionar novas funcionalidades e experimentar. O conhecimento que você adquiriu aqui é a base para construir aplicações ainda mais complexas e impressionantes. Continue explorando e, acima de tudo, continue construindo!

### Referências

- [Construir uma Aplicação React do Zero – React](https://pt-br.react.dev/learn/build-a-react-app-from-scratch)
