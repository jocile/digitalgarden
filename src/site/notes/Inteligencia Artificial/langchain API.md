---
{"dg-publish":true,"permalink":"/inteligencia-artificial/langchain-api/","title":"langchain API","metatags":{"description":"As APIs permitem que seu agente se conecte ao mundo exterior, acesse informações em tempo real, e execute ações"},"tags":["Inteligencia-artificial/Langchain"],"updated":"2025-01-18T18:55:21.990-03:00"}
---

## LangChain API

O LangChain oferece diversas formas de interagir com APIs, permitindo que você crie aplicações de IA mais dinâmicas e versáteis. As APIs permitem que seu agente se conecte ao mundo exterior, acesse informações em tempo real, e execute ações que vão além da simples geração de texto.

Aqui estão alguns pontos chave sobre como o LangChain usa APIs:

- **Integração com diversas APIs**: O LangChain facilita a conexão com uma variedade de APIs, incluindo as da OpenAI, Google, e outras plataformas. Isso permite que você use diferentes modelos de linguagem e serviços em suas aplicações.
- **Ferramentas (Tools) e Funções**: O LangChain permite que você defina ferramentas que podem ser acessadas pelos agentes. Estas ferramentas podem ser funções que chamam APIs externas. Por exemplo, você pode ter uma ferramenta para buscar informações na web, outra para acessar um banco de dados, ou até mesmo uma para enviar um e-mail.
- **Function Calling**: O LangChain possibilita o uso de "function calling" que permite que o agente gere chamadas de API com os parâmetros corretos. Isso permite que o agente interaja com APIs de forma mais estruturada e eficiente. O agente pode usar o resultado da API para continuar o seu fluxo de trabalho, tomar decisões ou apresentar informações ao usuário.
- **Agentes que interagem com APIs**: Os agentes do LangChain podem usar as ferramentas e APIs de forma autônoma. O agente decide qual ferramenta usar com base no prompt do usuário. Isso permite que o agente realize tarefas complexas e adapte sua estratégia dependendo do contexto.
- **Criação de APIs com LangServe**: O LangChain facilita a criação de APIs para seus modelos de linguagem com o LangServe. Você pode criar rotas (routes) para diferentes funcionalidades e modelos, e disponibilizar essas APIs para serem consumidas por outras aplicações. O LangServe usa Fast API para criar APIs de forma eficiente e rápida.
- **Uso de LangServe com Fast API**: O LangServe usa a biblioteca Fast API para criar APIs de forma eficiente, com documentação Swagger UI. Isso significa que você pode disponibilizar seus modelos e chains como APIs que podem ser facilmente integradas com outras aplicações.
- **Flexibilidade e escalabilidade**: O LangChain oferece flexibilidade para usar diferentes modelos e ferramentas, permitindo que você crie aplicações personalizadas. A arquitetura do LangChain, com o uso de chains e agentes, permite que você crie fluxos de trabalho complexos e escaláveis.

### Exemplos práticos de uso de APIs no LangChain

- **Busca na Web**: Um agente pode usar a API do Google Search para obter informações em tempo real.
- **Acesso a bancos de dados**: Um agente pode usar uma API para consultar dados em um banco de dados, como o Supabase, para responder perguntas ou obter informações específicas.
- **Automação de tarefas**: Um agente pode usar APIs para automatizar tarefas como envio de e-mails, agendamento de reuniões ou criação de registros em um sistema.
- **Integração com WhatsApp**: Um agente pode ser integrado com o WhatsApp por meio de APIs, permitindo que usuários interajam com o agente em um ambiente familiar.
- **Geração de texto**: Um agente pode usar uma API de um modelo de linguagem para gerar texto, seja para escrever um artigo, criar um poema, ou traduzir um texto.

Em resumo, o LangChain oferece as ferramentas necessárias para criar aplicações de IA que interagem com APIs externas, permitindo que seus agentes executem tarefas complexas e acesse informações em tempo real. Você pode usar o LangChain para construir tanto APIs personalizadas quanto para integrar APIs de terceiros em suas aplicações.

### Referências

- [LangChain Academy](https://academy.langchain.com/)
- [GitHub - langchain-ai/langchain-academy](https://github.com/langchain-ai/langchain-academy)
- [LangChain Python API Reference — 🦜🔗 LangChain documentation](https://python.langchain.com/api_reference/)
- [Complete Langchain Course For Generative AI In 3 Hours - YouTube](https://www.youtube.com/watch?v=swCPic00c30)
