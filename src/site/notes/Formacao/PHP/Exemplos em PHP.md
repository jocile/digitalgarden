---
{"dg-publish":true,"permalink":"/formacao/php/exemplos-em-php/","metatags":{"description":"exemplos de códigos de desenvolvimento web"},"noteIcon":2,"updated":"2025-08-22T08:14:27.667-03:00"}
---

#PHP

## Delimitadores de código

O código de um programa escrito em PHP deve estar contido entre os seguintes delimitadores:

```php
<?php
// código;
// código;
// código;
?>
```

## Comentários

Para comentar uma única linha:

```php
// echo "a";
# echo "a";
```

Para comentar muitas linhas:

```php
/* echo "a";
echo "b" */
```

## Saída

`echo`\
É um comando que imprime uma ou mais variáveis no console. Exemplo:\
`echo 'a','b','c'`\
Resultado:\
abc

`print`\
É uma função que imprime uma string no console. Exemplo:\
`print('abc');`

`var_dump`
Imprime o conteúdo de uma variável de forma explanativa, muito comum para se realizar debug. Se o parâmetro for um objeto, ele imprimirá todos os seus atributos; se for um array de várias dimensões, imprimirá todas elas, com seus respectivos conteúdos e tipos de dados. Exemplo:

```php
$vetor = array('Palio', 'Gol', 'Fiesta', 'Corsa');
var_dump($vetor);
```

Resultado:

```shell
array(4) {
	[0]=>
	string(5) "Palio"
	[1]=>
	string(3) "Gol"
	[2]=>
	string(6) "Fiesta"
	[3]=>
	string(5) "Corsa"
}
```

`print_r` 
Imprime o conteúdo de uma variável de forma explanativa, assim como a `var_dump()`, mas em um formato mais legível para o programador, com os conteúdos alinhados e suprimindo os tipos de dados. Exemplo:

```php
$vetor = array('Palio', 'Gol', 'Fiesta', 'Corsa');
print_r($vetor);
```

Resultado:

```shell
Array
(
[0] => Palio
[1] => Go1
[2] => Fiesta
[3] => Corsa
)
```

## Variáveis

Variáveis são identificadores utilizados para representar valores mutáveis e voláteis, que só existem durante a execução do programa. Elas são armazenadas na memória RAM e seu conteúdo é destruído após a execução do programa. Para criar uma variável em PHP, precisamos atribuir-lhe um nome de identificação, sempre precedido pelo caractere cifrão ($). Veja os exemplos a seguir:

```php
<?php
$nome = "João";
$sobrenome = "da Silva";
echo "$sobrenome, $nome";
?>
```

### Exemplo de variantes

```php
<?php
// define o nome da variável
$variavel = 'nome';
// cria variável identificada pelo conteúdo de $variavel
$variavel = 'maria';
// exibe variável $nome na tela
echo $nome; // resultado = maria
?>
```

### Referências a variáveis

Quando uma variável é atribuída a outra, sempre é criada uma nova área de armazenamento na memória. Veja neste exemplo que, apesar de $b receber o mesmo conteúdo de $a, após qualquer modificação em $b, $a continua com o mesmo valor.

```php
<?php
$a = 5;
$b = $a;
$b = 10;
echo $a; // resultado = 5
echo $b; // resultado = 10
?>
```

Para criar referência entre variáveis, ou seja, duas variáveis apontando para mesma região da memória, a atribuição deve ser precedida pelo operador &. Assim, qualquer alteração em qualquer uma das variáveis reflete na outra.

```php
<?php
$a = 5;
$b = &$a;
$b = 10;
echo $a; // resultado = 10
echo $b; // resultado = 10
?>
```

### Tipo booleano
Um booleano expressa um valor lógico que pode ser verdadeiro ou falso. Para especificar um valor booleano, utilize as palavras-chave TRUE ou FALSE. No exemplo a seguir, declaramos a variável booleana $exibir_nome, cujo conteúdo é TRUE (verdadeiro). 

```php
<?php
// declara variável com valor TRUE
$exibir_nome = TRUE;
// testa se $exibir_nome é TRUE
if ($exibir_nome)
{
	echo 'José da Silva';
}
?>
```

Também são considerados valores falsos em comparações booleanas:
- Inteiro 0
- Ponto flutuante 0.0
- Uma string vazia "" ou "0"
- Um array vazio
- Um objeto sem elementos
- Tipo NULL

### Tipo numérico

Números podem ser especificados em notação decimal (base 10), hexadecimal (base 16) ou octal (base 8), opcionalmente precedido de sinal (ou +).

```php
<?php
// número decimal
$a = 1234;
// um número negativo
$a =-123;
// número octal (equivalente a 83 em decimal)
$a = 0123;
// número hexadecimal (equivalente a 26 em decimal)
$a = 0x1А;
// ponto flutuante
$a = 1.234;
// notação científica
$a = 4e23;
?>
```

### Tipo string 

Uma string é uma cadeia de caracteres alfanuméricos. Para declará-la podemos utilizar aspas simples'' ou aspas duplas "".

```php
<?php
$variavel = 'Isto é um teste';
$variavel = "Isto é um teste";
?>
```

### Tipo Array

Array é uma lista de valores armazenados na memória, os quais podem ser de tipos diferentes (números, strings, objetos) e podem ser acessados a qualquer momento, pois cada valor é relacionado a uma chave. Um array também pode crescer dinamicamente com a adição de novos itens. Veja na seção Manipulação de arrays como manipular arrays.

```php
<?php
$carros = array('Palio', 'Corsa', 'Gol');
echo $carros [1]; // resultado = 'Corsa'
?>
```

### Tipo objeto 

Um objeto é uma entidade com um determinado comportamento definido por seus métodos (ações) e propriedades (dados). Para criar um objeto deve-se utilizar o operador new.

```php
<?php
class Computador
{
	var $cpu;
	function ligar()
	{
		echo "Ligando computador a {Sthis->cpu}...";
	}
}
Sobj = new Computador;
$obj->cpu = "500Mhz";
$obj->ligar();
// Resultado: Ligando computador a 500Mhz...
?>
```

### Constantes

Uma constante é um valor que não sofre modificações durante a execução do programa. Ela é representada por um identificador, assim como as variáveis, com a exceção de que só pode conter valores escalares (boolean, inteiro, ponto flutuante e string). Um valor escalar não pode ser composto de outros valores, como vetores ou objetos. As regras de nomenclatura de constantes seguem as mesmas regras das variáveis, com a exceção de que as constantes não são precedidas pelo sinal de cifrão ($) e geralmente utilizam-se nomes em maiúsculo.

Definimos uma constante utilizando a função `define()`. Quando uma constante é definida, ela não pode mais ser modificada ou anulada. Exemplo:

```php
<?php
  define("MAXIMO_CLIENTES", 100);
  echo MAXIMO_CLIENTES;
?>
```

### Variáveis globais

Todas as variáveis declaradas dentro do escopo de uma função são locais. Para acessar uma variável externa ao contexto de uma função sem passá-la como parâmetro, é necessário declará-la como global. Uma variável global é acessada a partir de qualquer ponto da aplicação.

```php
<?php
$total = 0;
function km2mi($quilometros) {
  global $total;
  $total += $quilometros;
  return $quilometros * 0.6;
}
echo 'percorreu'. km2mi(100). " milhas \n";
echo 'percorreu'. km2mi (200)."milhas \n";
echo 'percorreu no total'. $total. " quilometros \n";
/* Resultado:
percorreu 60 milhas
percorreu 120 milhas
percorreu no total 300 quilometros 
*/
?>
```

### Variáveis estáticas 

Dentro do escopo de uma função podemos armazenar variáveis de forma estática. Assim, elas mantêm o valor que lhes foi atribuído na última execução. Declaramos uma variável estática com o operador static.

```php
function percorre($quilometros)
{
  static $total;
  $total += $quilometros;
  echo "percorreu mais Squilometros do total de Stotal\n";
}
percorre(100);
percorre (200);
percorre(50);
/* Resultado:
percorreu mais 100 do total de 100
percorreu mais 200 do total de 300
percorreu mais 50 do total de 350 
*/
?>
```

## Operadores

```php
<?php
$var = 5; // Atribui o valor 5 a $var;
$var++;   // Soma +1 ao valor de $var;
$var += 5: // Soma 5 em $var;
$var -= 5; // Subtrai 5 em $var;
$var *=5; // Multiplica $var por 5;
$var /= 5; // Divide $var por 5;
?>
```

### Aritméticos

```php
<?php
$a = 2;
$b = 4;
echo $a+3*4+5*$b; // resultado = 34
echo ($a+3)*4+(5*$b); // resultado = 40
?>
```

Conversão de tipos automática:

```php<?php
// declaração de uma string contendo 10
$a = '10';
// soma + 5
echo $a + 5; // resultado = 15
?>
```

### Relacionais

| Comparadores | Descrição                                                                                   |
| -----------: | ------------------------------------------------------------------------------------------- |
|           == | Igual. Resulta verdadeiro (TRUE) se expressões forem iguais.                                |
|          === | Idêntico. Resulta verdadeiro (TRUE) se as expressões forem iguais e do mesmo tipo de dados. |
|    ! = ou <> | Diferente. Resulta verdadeiro se as variáveis forem diferentes.                             |
|            < | Menor.                                                                                      |
|            > | Maior que.                                                                                  |
|           <= | Menor ou igual.                                                                             |
|           >= | Maior ou igual.                                                                             |

```php
<?php
$a = 1234;
$b = '1234';
if ($a == $b)
}
	echo '$a e $b são iguais';
}
else if ($a != $b)
{
	echo '$a e $b são diferentes';
} // Resultado: $a e $b são iguais
?>
```


```php
<?php
$c = 1234:
$d = '1234';
if ($c === $d)
{
	echo '$c e $d são iguais e do mesmo tipо';
}
if ($c !== $d)
{
	echo '$c e $d são de tipos diferentes';
}
?> // Resultado: $c e $d são de tipos diferentes
```

### Lógicos

Operadores lógicos são utilizados para combinar expressões lógicas entre si, agrupando testes condicionais.

```
| Operador   | Descrição 
| ($a and $b)| E: Verdadeiro (TRUE) se tanto $a quanto $b forem verdadeiros.
| ($a or $b) | OU: Verdadeiro (TRUE) se $a ou $b forem verdadeiros.
| ($a xor $b)| XOR: Verdadeiro (TRUE) se $a ou $b forem verdadeiros, de forma exclusiva.
| (! $a)     | NOT: Verdadeiro (TRUE) se $a for FALSE.
| ($a && $b) | E: Verdadeiro (TRUE) se tanto $a quanto $b forem verdadeiros.
| ($a || $b) | OU: Verdadeiro (TRUE) se $a ou $b forem verdadeiros.
```

```php
<?php
$vai_chover = TRUE;
$esta_frio = TRUE;
if ($vai_chover and Sesta_frio)
{
	echo "Não vou sair de casa";
} // Resultado: Não vou sair de casa
?>
```

```php
<?php
$vai_chover = FALSE;
$esta_frio = TRUE;
if ($vai_chover xor $esta_frio)
{
	echo "Vou pensar duas vezes antes de sair";
}
?> // Resultado: Vou pensar duas vezes antes de sair
```

## Estruturas de controle

O IF é uma estrutura de controle que introduz um desvio condicional, ou seja, um desvio na execução natural do programa. Caso a condição dada pela expressão seja satisfeita, então serão executadas as instruções do bloco de comandos.

```
if (expressão)
{
	comandos se expressão é verdadeira;
}
else
{
	comandos se expressão é falsa;
}
```

```php
<?php
$a = 1;
if ($a==5)
{
	echo "é igual";
}
else
{
	echo "não é igual";
} // Resultado: não é igual
?>
```

```php
<?php
$a = 'conteúdo';
if ($a)
{
	echo '$a tem conteúdo';
}
if ($b)
{
	echo '$b tem conteúdo';
?> // Resultado: $a tem conteúdo
```

### if resumido

```php
if (Svalor_venda > 100)
{
	$resultado = 'muito caro';
}
else
{
	$resultado = 'pode comprar';
}
```

O mesmo código poderia ser escrito em uma única linha da seguinte forma:

`$resultado = (Svalor_venda > 100) ? 'muito caro' : 'pode comprar';`

### Faça enquanto

O WHILE é uma estrutura de controle similar ao IF. Da mesma forma, possui uma condição para executar um bloco de comandos. A diferença primordial é que o WHILE estabelece um laço de repetição, ou seja, o bloco de comandos será executado repetitivamente enquanto a condição de entrada dada pela expressão for verdadeira. Este comando pode ser interpretado como "ENQUANTO (expressão) FAÇA {comandos... }..

```php
<?php
$a = 1;
while ($a < 5)
{
  print Sa;
  $a ++;
} // Resultado: 1234
?>
```

### FOR

O FOR é uma estrutura de controle que estabelece um laço de repetição baseado em um contador;

```php
<?php
for ($i = 1; $i <= 10; $i++)
{
print Si;
?> // Resultado: 12345678910
```

### SWITCH 

O comando switch é uma estrutura que simula uma bateria de testes sobre uma variável. É similar a uma série de comandos IF sobre a mesma expressão.

```php
<?php
$i = 1;
switch ($i)
{
case 0:
  print "i é igual a 0";
  break;
case 1:
  print "i é igual a 1";
  break;
case 2:
  print "i é igual a 2";
  break;
default:
  print "i não é igual a 0, 1 ou 2";
} // Resultado: i é igual a 1
?>
```

### FOREACH 

O foreach é um laço de repetição para iterações em arrays ou matrizes.

```php
<?php
$fruta = array("maçã", "laranja", "pêra", "banana");
foreach ($fruta as $valor)
{
print "$valor -";
} // Resultado: maçă - laranja - pêra - banana
?>
```

## Requisição de arquivos

Podemos incluir dentro de nossos programas outros arquivos com definições de funções, constantes, configurações, ou mesmo carregar um arquivo contendo a definição de uma classe.

### include

A instrução include() inclui e avalia o arquivo informado. Se o arquivo não existir, produzirá uma mensagem de advertência (warning).

Arquivo biblioteca.php:

```php
<?php
/*
* função quadrado
* retorna o quadrado de um número
*/
function quadrado ($numero)
{
return Snumero * $numero;
}
?>

```

Programa que carrega o arquivo:

```php
<?php
// carrega arquivo com a função necessária
include 'biblioteca.php';
// imprime o quadrado do número 4
echo quadrado(4);
?>
```

#### include_once

Funciona da mesma maneira que o comando include, a não ser que o arquivo informado já tenha sido incluído, não refazendo a operação (o arquivo é incluído apenas uma vez).


### require

Idêntico ao include. Difere somente na manipulação de erros. Enquanto o include produz uma warning, o require produz uma mensagem de Fatal Error caso o arquivo não exista.

#### require_once 

Funciona da mesma maneira que o comando require, a não ser que o arquivo informado já tenha sido incluído, não refazendo a operação (o arquivo é incluído apenas uma vez).

## Funções

Para declarar uma função em PHP, utiliza-se o operador function seguido do nome.

```php
<?php
function calcula_obesidade ($peso, $altura)
{
	return Speso / ($altura * $altura);
}
echo calcula_obesidade(70, 1.85);
// Resultado: 20.45288531775
?>
```

### Passagem de parâmetros 

Existem dois tipos de passagem de parâmetros: por valor e por referência.

```php
<?php
function Incrementa($variavel, $valor)
{
  $variavel += $valor;
}
$a = 10;
Incrementa($a, 20);
echo $a;
// Resultado: 10
?>
```

Para efetuar a passagem de parâmetros by reference para as funções, basta utilizar o operador & na frente do parâmetro:

```php
<?php
function Incrementa(&$variavel, $valor)
{
  $variavel += $valor;
}
$a = 10;
Incrementa($a, 20);
echo $a;
// Resultado: 30
?>
```

### Valores default

Podemos definir valores default para parâmetros, para o caso do programador executar a função sem especificar o parâmetro.

```php
<?php
function Incrementa(&$variavel, $valor = 40)
{
  $variavel += $valor:
}
$a = 10;
Incrementa($a);
echo $a;
// Resultado: 50
?>
```

### Argumentos dinâmicos

Podemos definir uma função com o número de argumentos variáveis, ou seja, permite obtê-los de forma dinâmica, mesmo sem saber quais são ou quantos são.

```php
<?php
function Ola()
{
  $argumentos = func_get_args();
  $quantidade = func_num_args();
  for($n=0; $n<$quantidade; $n++)
  {
    echo 'Olá '. Sargumentos[$n] . "\n";
  }
}
Ola('João', 'Maria', 'José', 'Pedro');
/* Resultado:
Olá João 
Olá Maria 
Olá José 
Olá Pedro
*/
?>
```

### Recursão

```php
<?php
function Fatorial (Snumero)
{
  if ($numero == 1)
    return $numero;
  else
    return $numero * Fatorial($numero -1);
}
echo Fatorial(5). "\n";
echo Fatorial(7) . "\n";
/*
Resultado:
120 
5040
*/
?>
```


[[Formacao/Formacao em PHP\|Formacao em PHP]]
