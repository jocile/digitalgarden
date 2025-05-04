---
{"dg-publish":true,"permalink":"/tecnico/inteligencia-artificial/modelos-locais-de-i-as/","title":"Modelos locais de IAs","metatags":{"description":"A principal vantagem em usar modelos locais é que além de não necessitar de internet, não ter os tradicionais limites pagos de uso, e ainda poder treinar e testar diferentes modelos de IAs."},"tags":["Inteligencia-artificial","Modelos","LLM","Ollama"],"noteIcon":"1","updated":"2025-01-20T20:42:31.677-03:00"}
---


## Modelos locais de IAs

A principal vantagem em usar modelos locais é que além de não necessitar de internet, não ter os tradicionais limites pagos de uso, e ainda poder treinar e testar diferentes modelos de IAs.

### O que é um modelo de linguagem

Um modelo de linguagem é um sistema de inteligência artificial que aprende a gerar ou processar texto com base em exemplos de treinamento. Ele é treinado em grandes quantidades de texto para aprender a prever a próxima palavra ou frase com base no contexto anterior. 

Os modelos de linguagem podem ser usados para diversas tarefas, como:

- Tradução automática
- Geração de texto
- Resumo automático 
- Resposta a perguntas
- Gerar e explicar códigos de programação.

Os modelos de linguagem mais recentes, como o GPT-4 da OpenAI, são baseados em redes neurais profundas e apresentam um desempenho impressionante em várias tarefas de processamento de linguagem.

Embora o termo não tenha uma definição formal, ele geralmente se refere a modelos de aprendizado profundo que possuem uma contagem de parâmetros da ordem de bilhões ou mais. Esses modelos de propósito geral se destacam em uma ampla gama de tarefas, em vez de serem treinados para uma tarefa específica.

Além de prever a próxima palavra, modelos de linguagem neural com treinamento e contagem de parâmetros suficientes são capazes de capturar grande parte da sintaxe e semântica da linguagem humana. Eles também demonstram considerável conhecimento geral sobre o mundo e são capazes de "memorizar" uma grande quantidade de fatos durante o treinamento.

Em contraste, a definição mais básica de um modelo de linguagem refere-se ao conceito de atribuir probabilidades a sequências de palavras, com base na análise de corpora de texto. Esses modelos podem variar de complexidade, desde modelos simples de n-gram até modelos de rede neural mais sofisticados.

### Usando os modelos locais de linguagem

Para usar os modelos de linguagem precisamos de uma interface de comunicação, foi por isso que o ChatGPT popularizou o uso dos modelos, por facilitar a interação como um chat.

#### Interfaces para usar os modelos locais

1. Primeiramente instale o Ollama e com ele execute os modelos locais:
 - [Ollama](https://ollama.com/): é uma plataforma que fornece acesso local a uma variedade de modelos de linguagem, incluindo o Llama 3, Gemma 2, CodeLlama e outros. Ela oferece uma interface por API para interagir com esses modelos de maneira fácil e acessível.

1. Em seguida instale uma interface para gerenciar os prompts e as notas geradas, a mais simples é um plugin no Chrome, e a mais moderna é a Msty:
 - [ollama-ui: Simple HTML UI para o Ollama](https://github.com/rtcfirefly/ollama-ui) - É uma interface Web para o Ollama que interage através de um plugin do Chrome.
 - [Open WebUI](https://docs.openwebui.com/): é uma interface web intuitiva e de código aberto que permite interagir com a API do Ollama para usar diversos modelos de linguagem, incluindo o Mistral, Llama 3 e outros. Ela fornece recursos avançados como geração de código, análise de texto e até mesmo integração com APIs externas.
 - Extensões: permitem acessar os modelos em editores de código, como o VsCode, de forma a interagir com a API do Ollama e auxiliar na programação, atuando de forma local de maneira similar ao Copilot do Windows. Exemplos de extensões são o [Cody](https://marketplace.visualstudio.com/items?itemName=sourcegraph.cody-ai) e o [⚡️ Continue](https://docs.continue.dev/quickstart).
 - [msty.app](https://msty.app/) - Interface para acessar o Ollama de fácil instalação, com ela monte sua base de conhecimento a partir de documentos e pastas, com gerenciamento de prompts, uso de modelos em paralelo, instrução personalizada de modelos, modo offline, auto update, simplesmente a melhor!

#### Como usar localmente os modelos

- **Ollama**: Na plataforma [Ollama](Ollama.md), você pode selecionar o modelo de linguagem desejado (como Llama 3, Gemma 2 ou CodeLlama) e então interagir com ele através do terminal do linux ou Prompt do Windows. Você pode enviar comandos, perguntas, solicitar tarefas de codificação, gerar texto e muito mais. A interface também fornece opções para ajustar parâmetros como o tamanho da saída.
- Em [github.com/ollama/ollama](https://github.com/ollama/ollama) podemos fazer o download e instalar conforme seu sistema operacional, e usar um modelo digitando no prompt:

```powershell
ollama run llama3
```

- Com este comando, o Ollama baixa e executa o modelo llama3, ou outros modelos, veja a lista em [library](https://ollama.com/library), isso simplifica o acesso e a interação com esses poderosos modelos de linguagem, permitindo que desenvolvedores, pesquisadores e usuários em geral possam aproveitar seus recursos de maneira intuitiva e acessível.
- Os principais comandos do Ollama são:
	- `ollama pull llama3` - atualiza o modelo;
	- `ollama rm llama3` - remove o modelo;
	- `ollama show llama3` - mostra informações do modelo;
	- `ollama list` - lista os modelos instalados.
- Para uma interface com mais recursos use o Msty, com gerenciamento de seus documentos como uma base de pesquisa, gerenciamento de prompts, personalização de modelos, etc.

### Principais diferenças entre os modelos de linguagem

#### Llama 3 vs Gemma 2

- O Llama 3 é um modelo de linguagem de grande porte (até 65 bilhões de parâmetros) desenvolvido pela Anthropic, enquanto o Gemma 2 é um modelo menor (9B e 27B) desenvolvido pela Google.
- O Llama 3 é focado em tarefas gerais de linguagem, enquanto o Gemma 2 é mais voltado para aplicações de código e programação.
- Apesar de menor, o Gemma 2 tem um desempenho comparável ao Llama 3 em algumas tarefas de codificação.

#### CodeLlama vs StarCoder

- O CodeLlama é um modelo de linguagem especializado em tarefas de programação, desenvolvido pela Anthropic.
- O StarCoder é um modelo similar, desenvolvido pelo projeto BigCode, que também se concentra em geração de código em diversas linguagens de programação.
- O CodeLlama 34B supera o desempenho de outros modelos open-source em benchmarks de codificação, como HumanEval e MBPP.
- Versões fine-tuned do CodeLlama, como o Phind-CodeLlama, alcançam resultados ainda melhores nesses benchmarks.

#### Mistral vs Claude

- O Mistral é um modelo open-source de 7 bilhões de parâmetros, desenvolvido com técnicas como Grouped Query Attention e Sliding Window Attention para melhorar a eficiência.
- O Claude é um modelo proprietário da Anthropic, com foco em tarefas gerais de linguagem, não sendo especializado em codificação como o Mistral.
- Apesar de menor, o Mistral tem um desempenho comparável ao CodeLlama 7B em tarefas de programação, mantendo bom desempenho em outras tarefas de linguagem.

Em resumo, os modelos diferem principalmente no tamanho, foco (codificação vs. linguagem geral) e desempenho em benchmarks específicos de programação. Modelos como CodeLlama, StarCoder e versões fine-tuned se destacam em tarefas de codificação, enquanto modelos como Llama 3, Gemma 2 e Mistral têm um escopo mais amplo.

### Tabela comparativa

Aqui está uma tabela comparando as principais diferenças entre os modelos de linguagem mencionados:

| Modelo | Tamanho | Foco | Destaques |
|--------|---------|------|-----------|
| Llama 3 | Até 65B parâmetros | Tarefas gerais de linguagem | Modelo de grande porte da Anthropic |
| Gemma 2 | 9B e 27B parâmetros | Aplicações de código e programação | Bom desempenho em tarefas de codificação, apesar de menor |
| CodeLlama | 34B parâmetros | Tarefas de programação | Supera outros modelos open-source em benchmarks de codificação como HumanEval e MBPP |
| StarCoder | - | Geração de código em diversas linguagens | Modelo do projeto BigCode, similar ao CodeLlama |
| Mistral | 7B parâmetros | Tarefas gerais de linguagem e codificação | Técnicas como Grouped Query Attention e Sliding Window Attention para eficiência; bom desempenho em tarefas de programação |
| Claude | - | Tarefas gerais de linguagem | Modelo proprietário da Anthropic, não especializado em codificação |

Observações adicionais:

- Versões fine-tuned do CodeLlama, como o Phind-CodeLlama, alcançam resultados ainda melhores em benchmarks de codificação.
- Apesar de menor, o Mistral tem um desempenho comparável ao CodeLlama 7B em tarefas de programação, mantendo bom desempenho em outras tarefas de linguagem.

### Referências

Gerado por [Perplexity IA](https://www.perplexity.ai/)

- [Processamento de Linguagem Natural - 15  Modelos de Linguagem](https://brasileiraspln.com/livro-pln/1a-edicao/parte7/cap15/cap15.html)
- [As diferenças nos modelos de linguagem](https://www.meioemensagem.com.br/proxxima/diferencas-modelos-de-linguagem)
- [Modelo de linguagem – Wikipédia, a enciclopédia livre](https://pt.wikipedia.org/wiki/Modelo_de_linguagem)
- [Modelos de linguagem de grande escala – Wikipédia, a enciclopédia livre](https://pt.wikipedia.org/wiki/Modelos_de_linguagem_de_grande_escala)
- [O Que São Large Language Models (LLMs)? - Data Science Academy](https://blog.dsacademy.com.br/o-que-sao-large-language-models-llms/)
- [Ollama library](https://ollama.com/library)
- [🏡 Home | Open WebUI](https://docs.openwebui.com/)
- [Streaming language models – Replicate](https://replicate.com/collections/streaming-language-models)
- [Top Open-Source LLMs for Coding](https://www.e2enetworks.com/blog/top-8-open-source-llms-for-coding)
- [Philipp Schmid no LinkedIn: Large-scale Near-deduplication Behind BigCode](https://www.linkedin.com/posts/philipp-schmid-a6a2bb196_large-scale-near-deduplication-behind-bigcode-activity-7064989685030215681-cjbo)
- [GitHub - continuedev/what-llm-to-use: 👀 What LLM to use?](https://github.com/continuedev/what-llm-to-use)
- [EvalPlus Leaderboard](https://evalplus.github.io/leaderboard.html)
