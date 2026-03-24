---
{"dg-publish":true,"permalink":"/clipper/youtube-com/duas-i-as-criaram-esse-app-sozinhas-eu-so-assisti/","title":"Duas IAs Criaram Esse App SOZINHAS: Eu só assisti (Google Stitch + Antigravity é INSANO)","metatags":{"description":"O vídeo apresenta um fluxo de trabalho de ponta a ponta para criar aplicativos usando duas IAs do Google."},"noteIcon":"2","updated":"2026-03-13T09:46:51.701-03:00","dg-note-properties":{"created":"2026-03-12T22:04:56-03:00","url":"https://www.youtube.com/watch?v=Mt4dH9MqYEw","title":"Duas IAs Criaram Esse App SOZINHAS: Eu só assisti (Google Stitch + Antigravity é INSANO)","channel":"Matheus Battisti - Hora de Codar","related":["[[Tecnico/Ferramentas/ferramentas de IA/Antigravity/Antigravity\|Antigravity]]","[[Formacao/UX design/Design System\|Design System]]","[[Tecnico/ai/Model Context Protocol\|Model Context Protocol]]"],"published":"2026-02-15","thumbnailUrl":"https://i.ytimg.com/vi/Mt4dH9MqYEw/maxresdefault.jpg","duration":"0:20:41","watched":null}}
---

# Duas IAs Criaram Esse App SOZINHAS: Eu só assisti (Google Stitch + Antigravity é INSANO)

<div class="youtube-embed"><iframe src="https://www.youtube.com/embed/Mt4dH9MqYEw" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></div>

## Resumo

O vídeo apresenta um fluxo de trabalho de ponta a ponta para criar aplicativos usando duas IAs do Google: _Google Stitch_ para design de interface e _Antigravity_ para geração de código.

Os pontos principais incluem:

- **Visão Geral do [[Tecnico/ai/Workflows\|Workflow]]** (1:13): O _Google Stitch_ atua como o "arquiteto", criando o design e o fluxo do aplicativo, enquanto o _Antigravity_ atua como o "engenheiro", construindo o código com base nesse design. A conexão entre as duas ferramentas é feita através do _MCP ([[Tecnico/ai/Model Context Protocol\|Model Context Protocol]])_, que permite que o _Antigravity_ leia o design do _Stitch_ em tempo real para gerar um código mais fiel ao [[Formacao/UX design/layout\|layout]].
- **Google Stitch** (3:11): A ferramenta foi atualizada e agora inclui um "Idea Agent" (3:47) que auxilia na ideação do produto, conversando com o usuário e fazendo perguntas para refinar o conceito antes de gerar qualquer design. O vídeo demonstra a criação de um aplicativo de resenhas de livros, o _BookTalk_, com várias telas e funcionalidades (4:18).
- **[[Tecnico/Ferramentas/ferramentas de IA/Antigravity/Antigravity\|Antigravity]]** (6:36): O _Antigravity_ é uma IDE gratuita do Google que gera código com IA. O vídeo mostra como conectar o _Antigravity_ ao _Stitch_ via _MCP Server_ (11:00) usando uma chave de API, permitindo que o _Antigravity_ acesse e interprete os projetos do _Stitch_.
- **Construção e Teste do Projeto** (12:56): O _Antigravity_ constrói o projeto inteiro, incluindo componentes React e Next.js, rotas, autenticação e banco de dados. O vídeo demonstra a execução do aplicativo, destacando a funcionalidade de login, feed, e páginas de livros (16:09).
- **Desafios e Dicas** (17:43): O apresentador observa que, embora o projeto seja funcional, o design final do _Antigravity_ nem sempre é 100% fiel ao design do _Stitch_, especialmente em projetos maiores com muitas telas. Ele recomenda aprimorar os [[Tecnico/ai/Prompts\|Prompts]] no _Stitch_ e utilizar a funcionalidade "Annotate" para refinar detalhes. O vídeo também sugere que o _MCP_ mantém a sincronização, permitindo que o _Antigravity_ leia as atualizações do _Stitch_.

## Descrição

Neste vídeo eu mostro o pipeline mais completo de vibe coding que existe hoje: Google Stitch desenhando o app inteiro e [[Tecnico/Ferramentas/ferramentas de IA/Antigravity/Antigravity\|Antigravity]] construindo tudo sozinho lendo o design via MCP. Sem copiar código, sem exportar arquivo. Uma IA desenha, outra constrói.

O app que criei se chama BookTalk, uma plataforma social de resenhas de livros com 7 telas completas: login com design clean, feed principal com cards de resenhas mostrando capa do livro, nota e autor da resenha, página individual do livro com sinopse, rating médio e lista de resenhas, editor de resenha com campo de texto, rating com estrelas e upload de foto, página de resenha completa com seção de comentários, perfil do usuário com bio, lista de resenhas e estatísticas de leitura, e tela de explorar com categorias de livros e barra de busca. Tudo isso funcionando com autenticação, banco de dados e responsividade.

Começo pelo Google Stitch, que é a ferramenta do Google Labs que transforma [[Tecnico/ai/Prompts\|Prompts]] em interfaces completas. O Google comprou o Galileo AI e rebatizou como Stitch, e agora roda com Gemini 3. Mostro as novidades mais importantes: o Idea Agent que faz um brainstorming de interfaces antes de gerar qualquer coisa, os Prototypes que conectam telas em fluxos interativos navegáveis, e o MCP Server que permite que outras ferramentas de IA leiam seu design em tempo real. E o Stitch é gratuito com 350 gerações por mês no modo Standard.

Mostro todo o processo de ideação ao vivo. Abro o Idea Agent, descrevo o conceito do BookTalk e ele sugere variações de conceito, paleta de cores e estrutura antes de gerar uma única tela. Depois gero as telas com [[Tecnico/ai/Prompts\|Prompts]] específicos usando o Gemini 3, faço ajustes pontuais com o Annotate e conecto todas as telas num protótipo interativo com os Prototypes.
Depois vem a parte mais insana do vídeo: conectar o Stitch no [[Tecnico/Ferramentas/ferramentas de IA/Antigravity/Antigravity\|Antigravity]] via MCP. MCP é o [[Model Context Protocol]], um canal de comunicação entre ferramentas de IA. O Stitch MCP Server expõe todo o [[Design System]] para o [[Tecnico/Ferramentas/ferramentas de IA/Antigravity/Antigravity\|Antigravity]]: telas, cores, tipografia, componentes. Mostro a configuração passo a passo e o momento em que o [[Tecnico/Ferramentas/ferramentas de IA/Antigravity/Antigravity\|Antigravity]] começa a ler cada tela do Stitch e construir componente por componente.

O [[Tecnico/Ferramentas/ferramentas de IA/Antigravity/Antigravity\|Antigravity]] constrói o projeto inteiro: estrutura de pastas, componentes React e Next.js seguindo o design, rotas para cada tela, feed de resenhas funcionando com dados, sistema de rating com estrelas, página do livro com resenhas, sistema de comentários, autenticação com login e cadastro, banco de dados para resenhas e comentários, upload de imagem e busca por livros. Faço a comparação lado a lado entre a tela do Stitch e a tela rodando no app real, que é o momento mais forte do vídeo.

No final compartilho dicas práticas: quanto mais detalhado o [[Tecnico/ai/Prompts\|prompt]] no Stitch, melhor o resultado no [[Tecnico/Ferramentas/ferramentas de IA/Antigravity/Antigravity\|Antigravity]]. Use o Annotate pra refinar detalhes antes de mandar pro MCP. Planeje suas telas antes de gastar gerações no Stitch. E o MCP mantém tudo sincronizado, se você mudar algo no Stitch o [[Tecnico/Ferramentas/ferramentas de IA/Antigravity/Antigravity\|Antigravity]] pode ler a atualização.

Se você quer criar apps completos sem escrever código, esse pipeline de Google Stitch + [[Tecnico/Ferramentas/ferramentas de IA/Antigravity/Antigravity\|Antigravity]] via MCP é o caminho mais eficiente que existe hoje.

Entre no nosso servidor de Discord e me siga nas redes:

🟣 Discord Hora de Codar: https://discord.gg/Veq4mvsWwk
🔴 Instagram: https://www.instagram.com/horadecodar/
🔷 Telegram: https://t.me/horadecodar

TIMESTAMPS

00:00 Porque [[Tecnico/Ferramentas/ferramentas de IA/Antigravity/Antigravity\|Antigravity]] e Stitch?
01:13 Como funciona o [[Tecnico/ai/Workflows\|Workflow]] de Google Stitch + [[Tecnico/Ferramentas/ferramentas de IA/Antigravity/Antigravity\|Antigravity]]
03:11 Acessando o Google Stitch e criando projeto com Ideate
06:36 Conhecendo o [[Tecnico/Ferramentas/ferramentas de IA/Antigravity/Antigravity\|Antigravity]]
07:25 Ajustes finais no projeto no Stitch
11:00 Conectando o [[Tecnico/Ferramentas/ferramentas de IA/Antigravity/Antigravity\|Antigravity]] ao Stitch via MCP
12:56 Criando o projeto no [[Tecnico/Ferramentas/ferramentas de IA/Antigravity/Antigravity\|Antigravity]] baseado no [[Formacao/UX design/layout\|layout]] do Stitch
16:09 Testando versão inicial do projeto
17:43 Pedindo ajustes ao [[Tecnico/Ferramentas/ferramentas de IA/Antigravity/Antigravity\|Antigravity]]
19:45 Conclusão e próximos passos com [[Antigravity]] e Google Stitch

#gemini #Antigravity  #IA  #vibecode  #Stitch
