---
{"dg-publish":true,"permalink":"/formacao/java-script/calculo-do-imc-com-java-script/","metatags":{"description":"é uma biblioteca JavaScript poderosa e amplamente adotada"},"noteIcon":2,"updated":"2026-02-13T09:20:03.787-03:00"}
---

#JavaScript #Webdesign

Para consolidar os conceitos de **variáveis, operadores, funções e manipulação do DOM**, vamos mostrar um exemplo prático de uma **Calculadora de IMC (Índice de Massa Corporal)**. Este projeto é frequentemente utilizado para demonstrar a integração da lógica com a interface web.

Siga os passos abaixo para construir a aplicação:

### 1. Estrutura HTML

Crie um formulário simples para capturar o peso e a altura. Utilizaremos o evento **`onchange`** para que o cálculo seja atualizado automaticamente sempre que o usuário terminar de digitar.

```html
<h3>Calculadora de IMC</h3>
<form>
    <label>Peso (kg):</label>
    <input type="number" id="peso" onchange="calcularIMC()">
    <br><br>
    <label>Altura (m):</label>
    <input type="number" id="altura" step="0.01" onchange="calcularIMC()">
</form>

<div id="resultado">
    <!-- O resultado aparecerá aqui -->
</div>
```

### 2. A Lógica de Programação (JavaScript)

Dentro da tag `<script>`, definiremos a função que processa os dados. Observe o uso de **variáveis**, **conversão de tipos** e **estruturas condicionais**.

```js
function calcularIMC() {
    // 1. Captura os valores dos elementos do DOM
    var pesoTxt = document.getElementById("peso").value;
    var alturaTxt = document.getElementById("altura").value;

    // 2. Converte o texto para números decimais (float)
    var peso = parseFloat(pesoTxt);
    var altura = parseFloat(alturaTxt);

    // 3. Validação: verifica se os campos não estão vazios ou zerados
    if (isNaN(peso) || isNaN(altura) || altura === 0) {
        return; // Sai da função se os dados forem inválidos
    }

    // 4. Lógica Matemática: IMC = peso / altura ao quadrado
    var imc = peso / (altura * altura);

    // Arredonda para duas casas decimais
    var imcFormatado = imc.toFixed(2);

    // 5. Estrutura de Controle: Classificação do resultado
    var classificacao = "";
    if (imc < 18.5) {
        classificacao = "Abaixo do peso (Magreza)";
    } else if (imc >= 18.5 && imc <= 24.9) {
        classificacao = "Peso Saudável";
    } else if (imc >= 25.0 && imc <= 29.9) {
        classificacao = "Sobrepeso";
    } else {
        classificacao = "Obesidade";
    }

    // 6. Saída de Dados: Escreve o resultado na página
    document.getElementById("resultado").innerHTML =
        "<strong>Seu IMC é:</strong> " + imcFormatado + "<br>" +
        "<strong>Classificação:</strong> " + classificacao;
}
```

### O que este exemplo ensina:

- **Interação com o DOM:** Como o JavaScript localiza elementos HTML e lê seus valores através do `document.getElementById()`.
- **Tipagem e Conversão:** A importância de usar `parseFloat()` ou `parseInt()`, pois dados vindos de formulários são inicialmente tratados como strings (texto).
- **Operadores Aritméticos:** O uso da barra (`/`) para divisão e o asterisco (`*`) para multiplicação no cálculo matemático.
- **Lógica Condicional:** O uso de `if...else if` para tomar decisões baseadas em faixas de valores numéricos.
- **Eventos:** O uso do `onchange` para disparar a lógica apenas quando o valor do campo é modificado e o foco é perdido.

Para testar, basta salvar o código acima em um arquivo `.html` e abri-lo em qualquer navegador moderno. O **Console JavaScript** (F12) pode ser usado para verificar se há erros de digitação ou lógica durante o desenvolvimento.

[JSFiddle - Code Playground](https://jsfiddle.net/)
