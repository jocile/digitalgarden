---
{"dg-publish":true,"permalink":"/tecnico/webdesign/css/flexbox/","title":"Flexbox","metatags":{"description":"permite a criação de layouts flexíveis de forma dinâmica e responsiva"},"tags":["Webdesign","Flexbox","CSS","editor"],"noteIcon":"1","updated":"2025-01-22T19:48:11.890-03:00"}
---

# Flexbox
# Layouts Flexbox com CSS

<iframe src="https://jocile.github.io/webdesigner/formacao-css/2-Trabalhando-com-layouts-no-css/flexbox.html" style="height: 1050px; width: 90%;"></iframe>

O CSS Flexbox é um recurso do CSS (Cascading Style Sheets) que permite a criação de layouts flexíveis para elementos HTML. Em outras palavras, ele ajuda a organizar os elementos em uma página da web de forma dinâmica e responsiva.

## **Como funciona o Flexbox**

1. **Contêiner**: Um elemento pai que deseja alinhar seus filhos.
2. **Filhos**: Os elementos filho do contêiner que precisam ser alinhados.
3. **Direção**: O flexbox pode trabalhar em duas direções: horizontal (row) ou vertical (column).
4. **Flex items**: Os filhos do contêiner são chamados de "flex items".

## **Propriedades básicas do Flexbox**

* `display`: Definir o contêiner como um flexbox.
* `flex-direction`: Especificar a direção dos flex itens (row ou column).
* `justify-content` e `align-items`: Alinhar os flex itens na direção horizontal ou vertical.

## **Alinhamento de Flex Itens**

Existem várias formas de alinhar os flex items no CSS Flexbox:

1. **justify-content**: Alinha os flex itens na direção horizontal.
	* Valor: "flex-start" (padrão), "center", "space-around", "space-between".
2. **align-items**: Alinha os flex itens na direção vertical.
	* Valor: "stretch" (padrão), "center", "baseline".

## **Exemplo de código HTML e CSS para ilustrar o alinhamento**

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Flexbox</title>
    <style>
        .container {
            display: flex;
            justify-content: space-between; /* Alinha os filhos horizontalmente */
            align-items: center; /* Alina os filhos verticalmente */
            width: 500px;
        }
        
        .flex-item {
            background-color: #ADD8E6;
            height: 50px;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="flex-item">Flex Item 1</div>
        <div class="flex-item">Flex Item 2</div>
        <div class="flex-item">Flex Item 3</div>
    </div>

    <!-- Mais exemplos de alinhamento -->

    <h4>justify-content:</h4>
    <button style="display: flex; justify-content: center;">Centro</button>
    <button style="display: flex; justify-content: space-around;">Espaçado</button>
    
    <h4>align-items:</h4>
    <div class="container2">
        <p style="background-color: #ADD8E6; height: 50px;">Flex Item Alinha Centro (default)</p>
        <p style="display: flex; align-items: center;">Alinhar Flex Items ao centro</p>
    </div>

</body>
</html>
```

Nesse exemplo, foi criado um contêiner com três filhos e aplicados diferentes valores para `justify-content` e `align-items`.

## Referências

- [Flexbox - Aprendendo desenvolvimento web | MDN](https://developer.mozilla.org/pt-BR/docs/Learn/CSS/CSS_layout/Flexbox)
- [CSS Flexbox Layout Guide | CSS-Tricks](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [W3schools - CSS Flexbox (Flexible Box)](https://www.w3schools.com/css/css3_flexbox.asp)
- [Guia completo de Flexbox - CSS - display: flex;](https://origamid.com/projetos/flexbox-guia-completo/)
- [Flexbox  |  web.dev](https://web.dev/learn/css/flexbox?hl=pt)
- [Flexbox Froggy - A game for learning CSS flexbox](https://flexboxfroggy.com/)
- [DIO \_ Módulo 02 \_ Flexbox.pdf](https://github.com/jocile/webdesigner/blob/main/formacao-css/2-Trabalhando-com-layouts-no-css/DIO%20_%20M%C3%B3dulo%2002%20_%20Flexbox.pdf)
- [Exemplos de alinhamento com Flexbox ](https://jocile.github.io/webdesigner/formacao-css/2-Trabalhando-com-layouts-no-css/flexbox-alinhamento.html)
