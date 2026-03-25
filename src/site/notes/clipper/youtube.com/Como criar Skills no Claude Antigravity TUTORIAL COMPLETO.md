---
{"dg-publish":true,"permalink":"/clipper/youtube-com/como-criar-skills-no-claude-antigravity-tutorial-completo/","title":"Como criar Skills no Claude/Antigravity: TUTORIAL COMPLETO","noteIcon":2,"updated":"2026-03-25T08:27:26.917-03:00","dg-note-properties":{"created":"2026-03-14T15:55:45-03:00","url":"https://www.youtube.com/watch?v=2Zi3rGxWxDk?start=234","title":"Como criar Skills no Claude/Antigravity: TUTORIAL COMPLETO","channel":"Well Pires","related":["[[Tecnico/ai/Skills\|Skills]]"],"published":"2026-02-27","thumbnailUrl":"https://i.ytimg.com/vi/2Zi3rGxWxDk/maxresdefault.jpg","duration":"0:28:29","watched":null}}
---

# Como criar Skills no Claude/Antigravity: TUTORIAL COMPLETO

<div class="youtube-embed"><iframe src="https://www.youtube.com/embed/2Zi3rGxWxDk" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe></div>

## Resumo

Neste tutorial completo, Well Pires explica como criar e gerenciar **[[Tecnico/ai/Skills\|Skills]]** dentro do ambiente **Antigravity/Claude**, transformando-as em agentes de IA especializados para automatizar tarefas complexas (0:00-1:19). O objetivo é aumentar a eficiência, reduzindo a carga de informações no prompt do sistema (_system prompt_) para evitar que a IA perca o foco (2:33-3:35).

**Pontos chave abordados:**

- **Anatomia das Skills:** Elas não são apenas prompts, mas estruturas de pastas contendo o prompt do sistema (`skills.md`), arquivos de referência (_assets_) e scripts de execução (`execution scripts`) (4:03-6:45).
- **Fluxos Agênticos:** A transição de agentes simples para fluxos que cobrem tarefas operacionais, táticas e estratégicas, utilizando códigos em Python para resultados determinísticos (8:02-10:44).
- **Controle de Contexto:** A habilidade mais importante hoje é gerenciar a janela de contexto para manter a eficiência da IA, evitando o desespero de adicionar documentos desnecessários (12:46-13:58).
- **Demonstração Prática:** O autor utiliza o Claude no terminal para criar uma skill de **Thumbnail Designer** do zero, que se conecta via API a ferramentas como o _Nano Banana_ para gerar imagens de alto impacto baseadas em referências predefinidas (21:39-25:31).

## Como criar uma Skill

Criar uma **Skill** no _Antigravity_ envolve estruturar agentes especializados para automatizar tarefas. O processo fundamental consiste em definir instruções claras e organizar recursos para que a IA execute a ação sem desperdiçar contexto (1:00-3:35).

**Passo a passo para criar uma Skill:**

1. **Definir a Estrutura (Pastas):** As Skills funcionam como pastas no seu projeto. Comece abrindo um novo projeto no _Antigravity_ e crie uma pasta para sua Skill (ex: _thumbnail-generator_) (21:40-22:00).
2. **Criar o `skills.md` (System Prompt):** Este arquivo é o cérebro da sua skill. Ele deve ser enxuto e conter:
    - **Nome e Gatilho:** Quando a skill deve ser usada (16:00-16:25).
    - **Objetivo:** O que ela deve alcançar (16:25-16:40).
    - **Ferramentas:** Quais APIs ou ferramentas ela precisa acessar (17:40-19:00).
    - **Passo a Passo ([[Tecnico/ai/Workflows\|Workflows]]):** Instruções lógicas sequenciais para a execução (20:45-21:30).
3. **Configurar Arquivos de Referência (`references`):** Coloque documentos, imagens ou playbooks na pasta para guiar a IA, permitindo que ela siga um padrão tático ou estratégico (16:40-17:40).
4. **Criar Scripts de Execução (`scripts`):** Adicione códigos em _Python_ ou _JavaScript_ para ações determinísticas, como conectar-se a APIs de terceiros (ex: geradores de imagem) (6:40-8:00).

**Dica Pro:** Utilize o próprio _Claude_ no terminal do _Antigravity_ para ajudar a estruturar e criar esses arquivos automaticamente, pedindo: "Crie uma skill chamada [Nome] para [Objetivo]" (23:30-24:30).

## Descrição

As [[Skills]] são seus novos Agentes de IA para construir projetos dentro do [[Tecnico/Ferramentas/ferramentas de IA/Antigravity/Antigravity\|Antigravity]]! Usando ferramentas como Claude Code e API's você consegue construir skills que automatizam horas de trabalho em poucos minutos! Nesse vídeo, vou te entregar uma masterclass completa de como funcionam as skills, o que são skills e como criar skills dentro do Antigravity. Espero que curtam!

Entre na AI Makers e consiga seu 1º cliente + todos meus templates ⤵️
https://aimakersclub-teal.vercel.app/

Me contrate para automatizar seu negócio com Agentes de IA ⤵️
https://calendly.com/wellpires/discovery-call

VPS da Hostinger usando o cupom WELLPIRES para obter + desconto (por tempo limitado): 🔗 https://www.hostg.xyz/SHIvJ

Agents.md:
https://docs.google.com/document/d/1MQHF01jroAWSF5dIsI55eu3sJPUh6UwxSL8yAocmkjc/edit?tab=t.0

#vibecode #agentic-skills #Antigravity #video 

- [Specification - Agent Skills](https://agentskills.io/specification)
