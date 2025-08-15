---
{"dg-publish":true,"permalink":"/formacao/java-script/repeticoes-com-java-script/","metatags":{"description":"Exemplos de scripts com loops"},"noteIcon":2,"updated":"2025-08-14T11:01:48.584-03:00"}
---

#JavaScript #Aulas

## Contando de 1 a 10

```html
<!DOCTYPE html>
<html>
<body>

<h2>JavaScript For Loop</h2>

<p id="demo"></p>

<script>
let text = "";

for (let i = 1; i <= 10; i++) {
  text += "O número é " + i + "<br>";
}

document.getElementById("demo").innerHTML = text;
</script>

</body>
</html>
```

## Mostrando os itens de uma lista

```html
<!DOCTYPE html>
<html>
<body>

<h2>Repetições com JavaScript</h2>

<p id="demo"></p>

<script>
const alunos = ["Tanuzia", "Fco Ant", "Karla", "Lucas", "Ant Lucas", "Fernanda", "João"];

let text = "";
for (let i = 0; i < alunos.length; i++) {
  text += alunos[i] + "<br>";
}

document.getElementById("demo").innerHTML = text;
</script>

</body>
</html>
```

###  Invertendo a ordem

```html
<!DOCTYPE html>
<html>
<body>

<h2>Repetições com JavaScript</h2>
<p id="demo"></p>

<script>
const alunos = ["Tanuzia", "Fco Ant", "Karla", "Lucas", "Ant Lucas", "Fernanda", "João"];

let text = "<h3>Ordem normal:</h3>";
for (let i = 0; i < alunos.length; i++) {
  text += (i+1) + " " + alunos[i] + "<br>";
}
text += "<h3>Ordem decrescente:</h3>"
for (let i = alunos.length - 1 ; i > -1 ; i = i - 1) {
  text += (i+1) + " " + alunos[i] + "<br>";
}

document.getElementById("demo").innerHTML = text;
</script>

</body>
</html>
```

- [Percorrendo listas com JavaScript For In](https://www.w3schools.com/js/js_loop_forin.asp)
