---
{"dg-publish":true,"permalink":"/tecnico/programador/logica/repeticoes-em-python/","metatags":{"description":"criando algoritmos com repetições para programas de computador resolvendo problemas"},"noteIcon":1,"updated":"2026-01-30T07:18:51.617-03:00"}
---

#Lógica #exercícios #Python

Em Python, há três formas principais de repetição:

1. O loop for, que é usado para iterar sobre uma sequência de valores.
2. O loop while, que é usado para repetir um bloco de código enquanto uma condição é verdadeira.
3. O iterador, que é usado para acessar os elementos de uma sequência um a um.

A escolha de qual forma de repetição utilizar depende do problema que você está tentando resolver.

## Loop com for

Em geral, o loop for é mais utilizado quando você sabe exatamente quantas vezes deseja repetir um bloco de código.

Exemplo:

Usando o loop for com a função range para repetir um número fixo de vezes:

```python
for i in range(5):
    print(i)

```

Escreva um programa em Python que imprima todos os números pares de 0 a 100.

```python
for i in range(0, 101, 2):
    print(i)
```

Nesse algoritmo, usamos a função range() para criar uma sequência de números de 0 a 100 com um passo de 2 (para que apenas os números pares sejam incluídos). Em seguida, usamos um loop for para percorrer essa sequência e imprimir cada número.

## Loop com while

O loop while é mais utilizado quando você precisa repetir um bloco de código enquanto uma condição é verdadeira.
Usando o loop while para repetir um bloco de código enquanto uma condição for verdadeira:

Exemplo:

```python
# Usando o loop while para repetir um bloco de código
i = 0
while i < 5:
    print(i)
    i += 1

```

## Iterator de loop

O iterador é utilizado quando você precisa acessar os elementos de uma sequência de forma individual.

Exemplos:

```python
# Iterando sobre uma lista usando o loop for
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    print(num)

```

Escreva um programa em Python que calcule a média aritmética de uma lista de números.

```python
numeros = [3, 5, 8, 12, 15]

soma = 0
for numero in numeros:
    soma += numero

media = soma / len(numeros)

print("A média é:", media)

```

Nesse algoritmo, definimos uma lista de números e usamos um loop for para percorrer a lista e somar todos os números. Em seguida, dividimos essa soma pelo número de elementos na lista (usando a função len()) para calcular a média. Por fim, exibimos a média usando a função print().

> Lembre-se que repetição é uma parte fundamental da programação e é útil para tarefas como cálculos, filtragem de dados, busca, entre outros.
{: .prompt-info }

## Saindo do loop

Algumas vezes necessitamos sair do loop, para isso podemos usar o comando break:

Usando a instrução break para sair de um loop prematuramente:

```python
# Usando a instrução break para sair de um loop prematuramente
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    if num == 3:
        break
    print(num)

```

## Pulando a iteração

Usando a instrução continue para pular para a próxima iteração do loop:

```python
numbers = [1, 2, 3, 4, 5]
for num in numbers:
    if num == 3:
        continue
    print(num)

```

## Lista de exercícios com repetições

1. Escreva um programa que imprima todos os números pares de 0 a 20.
2. Escreva um programa que peça ao usuário para digitar um número inteiro positivo e calcule a soma de todos os números ímpares de 1 até esse número.
3. Escreva um programa que peça ao usuário para digitar uma frase e conte quantas vogais (a, e, i, o, u) ela possui.
4. Escreva um programa que peça ao usuário para digitar uma lista de números e imprima o maior número da lista.
5. Escreva um programa que peça ao usuário para digitar uma palavra e imprima a palavra invertida.
6. Escreva um programa que calcule a média aritmética de uma lista de números.
7. Escreva um programa que peça ao usuário para digitar um número inteiro e verifique se ele é um número primo.
8. Escreva um programa que peça ao usuário para digitar uma palavra e verifique se ela é um palíndromo (ou seja, se a palavra é igual quando lida de trás para frente).



## Referências

- [W3schools Python reference](https://www.w3schools.com/python/default.asp)
- [Colab - Introdução a programação com a linguagem Python](https://colab.research.google.com/drive/17DTWLVeBgIuwp-FYGIsAxlaj_mRNNMkK?usp=sharing#scrollTo=-F7LD5SJy2eq)
- [Livro na Biblioteca Virtual - Introdução à programação em Python - Sérgio Furgeri](https://bibliotecadigitalsenac.com.br/#/?contentInfo=3011)
