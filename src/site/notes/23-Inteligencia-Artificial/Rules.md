---
{"dg-publish":true,"permalink":"/23-inteligencia-artificial/rules/","metatags":{"description":"são pacotes de conhecimento sob demanda, as regras funcionam como um código de conduta ou uma placa arquitetônica que o agente consulta antes e durante a escrita de código"},"noteIcon":2,"updated":"2026-04-01T14:55:51.655-03:00","dg-note-properties":{"topics":["Live coding","Automação"]}}
---

#Inteligencia-artificial  #Projeto #Antigravity

# Regras

No ecossistema do Google [[23-Inteligencia-Artificial/Ferramentas de IA/Antigravity/Antigravity\|Antigravity]] e Cursor, as **rules (regras, papéis, preferências, [[35-Webdesign/UX design/requisitos\|requisitos]])** são definidas como **guardrails (trilhos de proteção) passivos e sempre ativos** que residem no prompt de sistema do agente. Diferente das [[23-Inteligencia-Artificial/Skills\|Skills]], que são pacotes de conhecimento sob demanda, as regras funcionam como um código de conduta ou uma placa arquitetônica que o agente consulta antes e durante a escrita de código para garantir que nenhum padrão do projeto seja violado.

## Definições

### Diferenciação e Escopo

As regras operam em dois níveis de escopo:

- **Global Rules:** Aplicam-se a todos os projetos desenvolvidos na máquina do usuário e são ideais para definir a persona do agente (seu papel ou função), o estilo de comunicação e stacks preferenciais (como Next.js ou FastAPI).
- **Workspace Rules:** São específicas para os [[35-Webdesign/UX design/requisitos\|requisitos]] de um projeto atual, geralmente armazenadas em arquivos como `.wgrad/rules.md` ou na pasta `.AGENTS/rules/` na raiz do projeto.

Ao contrário dos [[23-Inteligencia-Artificial/Workflows\|Workflows]], que são macros acionadas manualmente pelo usuário via comando `/`, as regras são **acionadas automaticamente por gatilhos de contexto**.

### Anatomia de uma Regra Eficaz

Para que uma regra funcione bem, ela deve seguir uma estrutura clara:

1. **Motivo:** Explicação do porquê a regra existe.
2. **Gatilho:** Quando ela deve ser aplicada (ex: ao modificar arquivos na pasta `/api`).
3. **Exemplos (Few-shot):** Fornecer exemplos de código correto e incorreto pode melhorar a performance da IA em até **70%**.
4. **Exceções:** Documentar casos onde a regra não se aplica para evitar que o agente fique travado.

### Benefícios e Exemplos Práticos

O uso estratégico de regras garante **consistência em projetos grandes**, reduz a necessidade de code review manual e ajuda a evitar vulnerabilidades de segurança. Alguns exemplos de regras essenciais incluem:

- **Isolamento de Segurança:** Proibir estritamente a exposição de chaves administrativas (_Service Role Keys_) no front-end.
- **Performance Assíncrona:** Garantir que comunicações com bancos de dados ou APIs externas sejam sempre não bloqueantes (`async/await`).
- **Multitenant Shield:** Forçar a inclusão de filtros por `company_id` em todas as queries para garantir o isolamento de dados entre clientes.
- **Higiene de Dependências:** Instruir o agente a sugerir apenas pacotes com manutenção ativa (ex: lançados há menos de 12 meses) e rejeitar bibliotecas com vulnerabilidades conhecidas.

### Limitações e Estratégia

É fundamental trabalhar as regras com inteligência, pois o uso excessivo (como 50 regras em um único projeto) pode causar **saturação de contexto**. Isso resulta em queima desnecessária de tokens, aumento da latência e pode levar à "context rot" (podridão de contexto), onde o modelo se confunde com instruções irrelevantes para a tarefa atual. Portanto, recomenda-se ser estratégico e incluir apenas o que é realmente essencial para a fundação do projeto.

## Referências

- [Google Antigravity Documentation](https://antigravity.google/docs/rules-workflows)
- [14 Rules que salvam seu código no Cursor e Antigravity - YouTube](https://www.youtube.com/watch?v=km5EaBJZfUQ)
