---
{"dg-publish":true,"permalink":"/clipper/youtube-com/ai-studio-antigravity-supabase-criei-um-app-completo-do-zero-ao-deploy/","title":"AI Studio + Antigravity + Supabase: Criei um App COMPLETO do Zero ao Deploy (Tutorial)","noteIcon":2,"updated":"2026-03-12T21:32:58.621-03:00"}
---


# AI Studio + Antigravity + Supabase Criei um App COMPLETO do Zero ao Deploy (Tutorial)

<div class="youtube-embed"><iframe src="https://www.youtube.com/embed/LW_2JEG3enE" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></div>

## Description

🧪 Teste seu app com IA (1º mês grátis): https://www.testsprite.com/?via=matheus

Nesse vídeo eu crio um app completo do zero ao deploy usando o pipeline mais eficiente que existe hoje: AI Studio pra prototipar, Antigravity pra construir de verdade, Supabase pro banco de dados e autenticação, e TestSprite pra testar tudo com IA antes de publicar.

❇️ Garanta seu desconto na Formação Vibe Coding: https://app.horadecodar.com.br/lp/esquenta-vibe-coding

🟪 Hospedagem para n8n que eu indico: https://hostinger.com.br/battisti (use o cupom HORADECODAR para ter +10% de desconto)

📘 Guia Engenharia de Prompt: https://app.horadecodar.com.br/ebookpages/guia-engenharia-de-prompt

O app se chama Meu Chef IA. Você digita os ingredientes que tem na geladeira e a IA gera uma receita completa com nome criativo, ingredientes com quantidades, passo a passo, tempo de preparo e nível de dificuldade. Além disso tem catálogo de receitas com cards visuais, busca por nome, edição, exclusão e tudo salvo no banco de dados com login por usuário.

Começo no AI Studio Build Mode. Em poucos minutos já tenho o app visual funcionando com a IA de receitas integrada usando o Gemini embutido. Testo gerando uma receita com frango, batata, creme de leite e alho. Funciona. Mas quando recarrego a página, perdi tudo. Precisa de banco de dados.

Transfiro o projeto pro GitHub e abro no Antigravity. Aqui é onde o app vira produto de verdade. Com um prompt, o Antigravity via Supabase MCP cria o banco de dados com tabelas de receitas, configura autenticação com email e senha, implementa Row Level Security pra cada usuário só ver suas receitas, e cria uma Edge Function no Supabase pra chamar a API do Gemini sem expor a chave no frontend.

Mostro o resultado: tela de login bonita na paleta do app, cadastro, CRUD completo de receitas, geração com IA salvando direto no banco e o momento mais satisfatório: recarregar a página e os dados continuam lá. Depois peço ajustes finos: contador de receitas no header, confirmação antes de deletar, animações nos cards e responsividade no celular.

Antes de publicar, testo o app com TestSprite via MCP direto no Antigravity. O TestSprite é um agente de IA que testa o app automaticamente. Ele analisa o projeto, gera um plano de testes cobrindo login, cadastro, criação de receitas, edição, exclusão, geração com IA e tratamento de erros. Mostro o Test Progress Dashboard com status ao vivo de cada teste, vídeos da IA interagindo com o app e o passo a passo de cada teste. Quando um teste falha, uso o Modify Tests pra editar visualmente o step que deu problema, clicar na screenshot pra selecionar o elemento e re-rodar até passar. Tudo verde, confiança pra publicar.

Deploy como site estático. O projeto já tá no GitHub, conecto o repo no hosting, configuro as variáveis de ambiente do Supabase no build e pronto. App no ar, funcionando em produção. A chave do Gemini fica segura na Edge Function do Supabase, não precisa no hosting.

O pipeline completo: AI Studio prototipa rápido com IA funcionando, Antigravity constrói o app de verdade com banco e autenticação, TestSprite testa tudo com IA via MCP, e o deploy conecta o repo e publica automaticamente. De ideia a app publicado em um vídeo.


Entre no nosso servidor de Discord e me siga nas redes:

🟣 Discord Hora de Codar: https://discord.gg/Veq4mvsWwk
🔴 Instagram: https://www.instagram.com/horadecodar/
🔷 Telegram: https://t.me/horadecodar

TIMESTAMPS

00:00 A nova forma de criar projetos com Antigravity
01:10 Explicando o workflow do projeto (AI Studio + Antigravity)
03:55 Criando base do projeto no AI Studio
08:05 Colocando o projeto no GitHub pelo AI Studio
09:40 Clonando o projeto no Antigravity (GitHub MCP)
13:40 Integrando Antigravity com Supabase
15:08 Criando autenticação e banco de dados no projeto
20:40 Adicionando testes ao projeto
28:54 Adicionando novas funcionalidades
30:35 Deploy do projeto
35:03 Considerações finais sobre AI Studio, Antigravity e Supabase

#Antigravity #AIStudio #IA #DevIA  #Supabase #ProgramaçãoAI #AIcoders #gemini
