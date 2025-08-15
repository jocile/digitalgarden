---
{"dg-publish":true,"permalink":"/formacao/java-script/manipulando-elementos-com-java-script/","metatags":{"description":"Exemplos de manipulação de textos e cálculos"},"noteIcon":2,"updated":"2025-08-14T09:27:40.999-03:00"}
---

#JavaScript #Aulas 

## Manipulando o texto

```html
<!DOCTYPE html>
<html>
<body>

<h2 id="cima">O que o JavaScript faz?</h2>
<p id="demo">JavaScript pode mudar o conteúdo.</p>

<button type="button" onclick='document.getElementById("demo").innerHTML = "Bom dia!"'>Dia!</button>
<button type="button" onclick='document.getElementById("cima").innerHTML = "Boa tarde!"'>Tarde!</button>
<button type="button" onclick='document.getElementById("demo").innerHTML = "Boa noite!"'>Noite!</button>

</body>
</html>
```

## Manipulando o design

```html
<!DOCTYPE html>
<html>
<body>

<h2>O que JavaScript faz?</h2>

<p id="demo">JavaScript pode mudar o estilo de elementos HTML"</p>

<button type="button" onclick="document.getElementById('demo').style.fontSize='35px'">Aumentar o tamanho</button>
<button type="button" onclick="document.getElementById('demo').style.fontSize='16px'">Diminuir o tamanho!</button>
<button type="button" onclick="document.getElementById('demo').style.color='Blue'">Mudar a cor!</button>

</body>
</html>
```

## Ocultando elementos

```html
<!DOCTYPE html>
<html>
<body>

<h2>O que JavaScript faz?</h2>

<p>JavaScript pode mostrar ou ocultar elementos HTML!</p>

<p id="demo" style="display:none">Hello JavaScript!</p>

<button type="button" onclick="document.getElementById('demo').style.display='block'">Mostrar!</button>
<button type="button" onclick="document.getElementById('demo').style.display='none'">Ocultar!</button>

</body>
</html>
```

### Usando funções

```html
<!DOCTYPE html>
<!DOCTYPE html>
<html>
<body>

<h2 id="titulo">O que JavaScript faz?</h2>

<p>JavaScript pode mostrar ou ocultar elementos HTML!</p>
<p id="demo" style="display:none">Hello JavaScript!</p>
<button type="button" onclick="mostrar()">Mostrar!</button>
<button type="button" onclick="ocultar()">Ocultar!</button>

<script>

function mostrar(){
  document.getElementById('demo').style.display='block';
  document.getElementById('titulo').style.color='Red';
}

function ocultar(){
   document.getElementById('demo').style.display='none';
   document.getElementById('titulo').style.color='Black';
}

</script>

</body>
</html>
```

## Usando expressões aritméticas

```html
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript Expressions</h2>

<p>Expressões podem computar valores.</p>

<p>x = 5</p>
<p>x * 10 =
<span id="valores"></span></p>
<p id="demo"></p>

<script>
let x;
x = 5;
document.getElementById("valores").innerHTML = x * 10;
document.getElementById("demo").innerHTML = "Lucas" + " "  + "Gerson";
</script>

</body>
</html>
```

## Declarando variáveis

```html
<!DOCTYPE html>
<html>
<body>

<h2>Redeclarando uma Variavel usando var</h2>

<p id="demo"></p>

<script>
var  x = 10;
// Aqui o x é 10

{  
var x = 2;
// Aqui o x é 2
}

// Aqui x é 2
document.getElementById("demo").innerHTML = x;
</script>

</body>
</html>
```

```html
<!DOCTYPE html>
<html>
<body>

<h2>Redeclarando uma Variavel usando let</h2>

<p id="demo"></p>

<script>
let  x = 10;
// Aqui o x é 10

{  
let x = 2;
// Aqui o x é 2
}

// Aqui x é 10
document.getElementById("demo").innerHTML = x;
</script>

</body>
</html>
```

## Valores constantes e erros

Valores constantes não podem ser mudados, por exemplo veja o erro mostrado tentando mudar uma constante:

```html
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript const</h2>

<p id="demo"></p>

<script>
try {
  const PI = 3.141592653589793;
  PI = 3.14;
}
catch (err) {
  document.getElementById("demo").innerHTML = err;
  console.log(err);
}
</script>

</body>
</html>
```

## Operações aritméticas

```html
<!DOCTYPE html>
<html>
<body>

<h1>JavaScript Arithmetic</h1>
<h2>The += Operator</h2>

<p> x = 10</p>
<p> x = x + 5 ou x += 5</p>
<p> x = 
<span id="demo"></span></p>

<script>
var x = 10;
//x = x + 5;
x += 5;
document.getElementById("demo").innerHTML = x;
</script>

</body>
</html>
```

```html
<!DOCTYPE html>
<html>
<body>

<h1>JavaScript Arithmetic</h1>
<h2>O operador de resto %</h2>

<p> x = 4</p>
<p> y = x % 2</p>
<span id="par"></span></p>

<p> x = 5</p>
<p> y = x % 2</p>
<span id="impar"></span></p>


<script>
var x = 4;
var y = x % 2;
document.getElementById("par").innerHTML = "x é par com resto y = " + y;
x = 5;
y = x % 2;
document.getElementById("impar").innerHTML = "x é ímpar com resto y = " + y;
</script>

</body>
</html>
```


[JavaScript Introduction](https://www.w3schools.com/js/js_intro.asp)
