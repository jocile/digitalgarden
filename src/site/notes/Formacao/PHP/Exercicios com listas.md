---
{"dg-publish":true,"permalink":"/formacao/php/exercicios-com-listas/","metatags":{"description":"exemplos de códigos de desenvolvimento web"},"noteIcon":2,"updated":"2025-08-25T20:23:20.245-03:00"}
---

#PHP #exemplos 

## Números

```php
<!DOCTYPE html>
<html>
<body>

<?php  
for ($x = 0; $x <= 10; $x++) {
  if ($x == 2 || $x == 3 || $x == 5 || $x == 7) {
     echo "$x é primo!<br>";
     continue;  
  if ($x % 2 == 1 ) {
     echo "O número $x é ímpar!<br>";
     continue;
  }
  
  }  
  echo "O número é: $x <br>";
}
?>  

</body>
</html>
```

## Exibindo itens da lista

```php
<!DOCTYPE html>
<html>
<body>
<?php
$lista = ["Fco Ant","Lucas", "Karla"];
  
for ($x = 0; $x < count($lista); $x++) {
  echo "Aluno: " . $lista[$x] . "<br>";
}
echo "----------------<br>";

foreach($lista as $item){
  echo "Aluno: " .$item . "<br>";
}

echo "----------------<br>";
$x = 0;
while ($x < count($lista)){
  echo "Aluno: " .$lista[$x] . "<br>";
  $x++;
}

?>  

</body>
</html>
```

## Lista bidimencional de alunos

```php
<!DOCTYPE html>
<html>
<body>

<?php
$alunos = [
            ["Lucas","Cleto F.","100","centro","Sobral"],      
            ["Fco Ant","Principal","150","centro","Sobral"],
            ["Karla","Cotovelo","15","centro","Sobral"]
          ];

for ($i = 0; $i < count($alunos); $i++) {
  echo "Aluno: " . $alunos[$i][0] . "<br>Endereço:<br>";
  echo "--------------------<br>";
  echo "  Rua: " . $alunos[$i][1] . "<br>";
  echo "  N.: " . $alunos[$i][2] . "<br>";
  echo "  Bairro: " . $alunos[$i][3] . "<br>";
  echo "  Cidade: " . $alunos[$i][4] . "<br>";
  echo "--------------------<br><br>";
}
?>  

</body>
</html>
```

```php
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Lista em PHP</title>
</head>
<body>
<h1>Lista em PHP</h1>
<form action="" method="POST">
Name: <input type="text" name="name"><br>
<input type="submit">
</form>

<?php
$lista = ["Tanuzia","Fco Ant","Lucas", "Karla"];
sort($lista);

for ($x = 0; $x < count($lista); $x++) {
  echo "Aluno: " . $lista[$x] . "<br>";
}
echo "----------------<br>";

foreach($lista as $item){
  echo "Aluno: " .$item . "<br>";
}

echo "----------------<br>";
$x = 0;
while ($x < count($lista)){
  echo "Aluno: " .$lista[$x] . "<br>";
  $x++;
}
if ($_SERVER["REQUEST_METHOD"] == "POST") {
  echo "----------------<br>";
  echo "Bem vindo " . $_POST['name'] . "<br>";
  array_push($lista, $_POST['name']);
  sort($lista);
  foreach($lista as $item){
    echo "Aluno: " .$item . "<br>";
  }
}
?>  

</body>
</html>
```

## Lista salvando em arquivo

```php
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Lista em PHP</title>
</head>
<body>
<h1>Lista em PHP</h1>
<form action="" method="POST">
Name: <input type="text" name="name"><br>
<input type="submit">
</form>

<?php
$arquivo = "lista.txt";
$listaPadrao = ["Tanuzia","Fco Ant","Lucas", "Karla"];

// Se o arquivo não existe, cria com a lista padrão
if (!file_exists($arquivo)) {
  file_put_contents($arquivo, implode("\n", $listaPadrao));
}

$lista = file($arquivo, FILE_IGNORE_NEW_LINES | FILE_SKIP_EMPTY_LINES);

if ($_SERVER["REQUEST_METHOD"] == "POST") {
  if (isset($_POST['name']) && !empty($_POST['name'])) {
    echo "----------------<br>";
    echo "Bem vindo " . $_POST['name'] . "<br>";
    $novoNome = trim($_POST['name']);
    if (!in_array($novoNome, $lista)) {
      $lista[] = $novoNome;
      file_put_contents($arquivo, implode("\n", $lista));
    }
  }
}
sort($lista);
echo "----------------<br>";
foreach($lista as $item){
  echo "Aluno: " .$item . "<br>";
}
?>  

</body>
</html>
```

