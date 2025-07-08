---
{"dg-publish":true,"permalink":"/formacao/webdesign/markdown/","title":"Markdown","metatags":{"description":"é uma linguagem de marcação leve com sintaxe de formatação de texto simples"},"noteIcon":1,"updated":"2025-07-07T21:13:52.114-03:00"}
---

# Markdown

Markdown é uma linguagem de marcação leve com sintaxe de formatação de texto simples projetada para que ela possa ser convertida em HTML e muitos outros formatos usando uma ferramenta com o mesmo nome. Markdown é usado frequentemente para formatar arquivos readme, para escrever mensagens em fóruns de discussão on-line e para criar texto rico usando um editor de texto simples.

## Sintaxe do Markdown  

Toda a sintaxe pode ser encontrada [aqui](https://daringfireball.net/projects/markdown/syntax) . Seria necessário muito esforço para descrever a sintaxe no texto (eles serão formatados), então, considere esta tabela abaixo para toda a sintaxe básica.  

| Formato                              | Sintaxe                                                                                                                            | Exemplo                                                                                                              |     |
| ------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | --- |
| Itálico                              | \*Text\*                                                                                                                           | *Isto está em itálico*                                                                                               |     |
| Negrito                              | \*\*Bold\*\*                                                                                                                       | **Isto está em negrito**                                                                                             |     |
| Links Inline                         | \[texto\](url aqui)                                                                                                                | Um [link](http://www.github.com)                                                                                     |     |
| Imagens                              | \![Legenda\](url da img)                                                                                                           | Uma imagem ![image](http://i.imgur.com/hRLuez2.png)                                                                  |     |
| Link + Imagens                       | \[\![Legenda\](url da img)\](url para a pagina)\]                                                                                  | Me clique [![me](http://i.imgur.com/hRLuez2.png)](https://www.youtube.com)                                           |     |
| Quebras de Linha                     | Double space + enter                                                                                                               |                                                                                                                      |     |
| Listas Não Ordenadas                 | \* Item1     \*Item 2                                                                                                              | <ul><li>item1</li><li>item2</li>                                                                                     |     |
| Listas Ordenadas                     | 1. Item a    2. Item b                                                                                                             | <ol><li>itema</li><li>itemb</li>                                                                                     |     |
| Listas Mistas                        | 1. Item 1      * item 1a                                                                                                           | <ol><li>item1</li></ol><ul><li> item1a</li></ul>                                                                     |     |
| Citação                              | \> Texto citado                                                                                                                    | <blockquote>Stay Hungry Stay Foolish</blockquote>                                                                    |     |
| Preformatted                         | Comece cada linha com, dois espaços ou mais, faça o look do texto, e x a t a m e n t e, como, você, tipo i, s, t, o.               | Comece cada linha com, dois espaços ou mais, faça o look do texto, e x a t a m e n t e, como, você, tipo i, s, t, o. |     |
| Código                               | \`Insira o código\`                                                                                                                | `cout<<"Hello world";`                                                                                               |     |
| Bloco de Código/ Destaque de Sintaxe | \`\`\`Insira o código\`\`\`                                                                                                        | [Leia a nota abaixo desta tabela.](#^secao1)                                                                         |     |
| Títulos                              | \#, \##, \###, \####, \#####, \###### (from h1 to h6)                                                                              | <h3>Isso é um título h3</h3>                                                                                         |     |
| Riscado                              | \~~Insira o texto aqui\~~                                                                                                          | ~~Eu estou morto~~                                                                                                   |     |
| Tabelas                              | \| Tables   \|      Are      \|  Cool \|<br>\|\----------\|\:\----------\:\|------\:\| <br>\| col 1 is\|  left-aligned \| $1600 \| | ![](http://i.imgur.com/EItt7mh.png)                                                                                  |     |
| Notas de Rodapé                      | Notas de rodapé[\^1\] <br> [\^1\]: Refêrencia                                                                                      | Aqui está uma simples nota de rodapé[^1]. Com um texto adicional.                                                    |     |

[^1]: Minha Referencia favorita.

Nota: **Nota de rodapé** atualmente não renderiza direito na tabela, mas se parece com isso:
{ #secao1}


O mesmo vale para **Bloco de código/destaque de sintaxe**. Sua aparência é igual a da imagem abaixo: 

![](http://i.imgur.com/z8KrxAz.png).

[[Formacao/Webdesign/markdown notas\|markdown notas]]
