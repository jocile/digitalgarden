---
{"dg-publish":true,"permalink":"/formacao/java-script/condicionais-com-java-script/","metatags":{"description":"Exemplos de scripts com tomada de decisão"},"noteIcon":2,"updated":"2025-08-14T23:49:02.285-03:00"}
---

#JavaScript #Aulas

## Usando o IF

```html
<!DOCTYPE html>
<html>
<body>
<h1>Condicionais com JavaScript if</h1>

<p>Mostre "Bom dia!" se a hora for menos que 18:00:</p>

<h2>Hora atual: <spam id="hora"></spam></h2>
 <p id="demo">Bom dia!</p>
  
  <script>
    document.getElementById("hora").innerHTML = new Date().toLocaleTimeString();
    if (new Date().getHours() < 18) {
     document.getElementById("demo").innerHTML = "Bom dia!";
    }
</script>

</body>
</html>
```

## Usando o ELSE

```html
<!DOCTYPE html>
<html>
<body>
<h1>Condicionais com JavaScript if</h1>

<p>Mostre "Bom dia!" se a hora for menos que 18:00:</p>

<h2>Hora atual: <span id="hora"></span></h2>
<h3 id="demo">Bom dia!</h>
  
  <script>
  //var hora = new Date().toLocaleTimeString();
  var hora = prompt("Informe a hora");
    document.getElementById("hora").innerHTML = hora;
    if (hora < 12) {
     document.getElementById("demo").innerHTML = "Bom dia!";
    } else if (hora < 18) {
     document.getElementById("demo").innerHTML = "Boa tarde!";
    } else
    {
     document.getElementById("demo").innerHTML = "Boa noite!";
    }
</script>

</body>
</html>
```

### Usando uma função para organizar o código

```html
<!DOCTYPE html>
<html>
<body>
<h1>Condicionais com JavaScript if</h1>

<p>Mostre "Bom dia!" se a hora for menos que 18:00:</p>

<h2>Hora atual: <span id="hora"></span></h2>
<h3 id="demo">Bom dia!</h>
  
<script>
  function mostrar(onde, msg) {
    document.getElementById(onde).innerHTML = msg;
  }  
  var hora = prompt("Informe a hora");
  // mostra o texto hora e a variável hora
  mostrar("hora", hora); 
  if (hora < 12) {
    mostrar("demo", "Bom dia!");
  } else if (hora < 18) {
    mostrar("demo","Boa tarde!");
  } else {
    mostrar("demo","Boa noite!");
    }
</script>

</body>
</html>
```



## Referências

- [Expressões condicionais - Jocile](https://jocile.github.io/aulas/posts/expressoes-condicionais/)
- [Repetições com JavaScript](https://www.w3schools.com/js/js_loop_for.asp)
- [Percorrendo listas com JavaScript For In](https://www.w3schools.com/js/js_loop_forin.asp)
