---
{"dg-publish":true,"permalink":"/tecnico/programador/logica/condicionais-em-python/","metatags":{"description":"criando algoritmos para programas de computador resolvendo problemas"},"noteIcon":1,"updated":"2026-02-01T22:07:12.179-03:00"}
---

#Lógica #exercícios #Python 

Em Python, existem duas formas principais de expressar condicionais: a estrutura if/elif/else e a expressão ternária.

## Estrutura if/else

A estrutura if/else permite executar um bloco de código se a condição for verdadeira, ou outro se for falsa. A sintaxe é a seguinte:

```python
if condicao:
    # bloco de código a ser executado se a condição for verdadeira
else:
    # bloco de código a ser executado se a condição anteriores for falsa

```

Exemplos: Usando a estrutura if-else para fazer escolhas:

```python
x = 10
if x > 0:
    print("x é positivo")
else:
    print("x é negativo ou zero")

```

Escreva um programa em Python que peça ao usuário para digitar uma palavra e verifique se a palavra é um palíndromo (ou seja, se ela é igual quando lida de trás para frente).

```python
palavra = input("Digite uma palavra: ")

if palavra == palavra[::-1]:
    print("A palavra é um palíndromo.")
else:
    print("A palavra não é um palíndromo.")

```

Nesse algoritmo, usamos a função input() para pedir que o usuário digite uma palavra. Em seguida, usamos um condicional if para verificar se a palavra é igual a ela mesma quando lida de trás para frente (usando a técnica de slicing com a notação [::-1]). Se a palavra for um palíndromo, exibimos uma mensagem indicando isso. Caso contrário, exibimos uma mensagem indicando que a palavra não é um palíndromo.

## Condicional aninhada if/elif/else

São condicionais seguidas ou dentro de outras condicionais. A estrutura if/elif/else permite executar diferentes blocos de código dependendo de uma ou mais condições. A sintaxe é a seguinte:

```python
if condicao1:
    # bloco de código a ser executado se a condicao1 for verdadeira
elif condicao2:
    # bloco de código a ser executado se a condicao1 for falsa e a condicao2 for verdadeira
else:
    # bloco de código a ser executado se todas as condições anteriores forem falsas

```

```python
# Fazendo escolhas múltiplas usando a estrutura if-elif-else
x = 10
if x < 0:
    print("x é negativo")
elif x == 0:
    print("x é zero")
else:
    print("x é positivo")

```

Exemplo: Elabore um algoritmo para checar se uma pessoa pode dirigir:

```python
idade = 18
tem_carteira = True

if idade >= 18:
    if tem_carteira:
        print("Pode dirigir")
    else:
        print("Não pode dirigir, pois não tem carteira de motorista")
else:
    print("Não pode dirigir, pois é menor de idade")

```

Nesse exemplo, temos duas condições aninhadas: a primeira checa se a pessoa é maior de idade, e a segunda checa se ela tem carteira de motorista. Se ambas as condições forem verdadeiras, o programa imprime a mensagem "Pode dirigir". Caso contrário, o programa imprime uma mensagem diferente.

>[!warning] Note que condicionais aninhadas podem ser úteis quando precisamos checar várias condições em sequência. No entanto, elas podem tornar o código mais difícil de ler e entender, especialmente se tivermos muitas condições aninhadas. Por isso, é importante avaliar cuidadosamente se essa é a melhor abordagem para o problema em questão.

## Expressão ternária

A expressão ternária é uma forma concisa de escrever uma condicional em uma única linha de código. A sintaxe é a seguinte:

```python
valor_se_verdadeiro if condicao else valor_se_falso
```

Exemplos:

```python
# Usando o operador condicional para simplificar o código
x = 10
result = "x é positivo" if x > 0 else "x é negativo ou zero"
print(result)

```

Exemplo: uma função que retorna a maior idade.

```python
idade = 18
status = "maior de idade" if idade >= 18 else "menor de idade"
print(status)
```

Nesse exemplo, a expressão idade >= 18 é avaliada primeiro. Se for verdadeira, a variável status receberá o valor "maior de idade". Caso contrário, status receberá o valor "menor de idade". O resultado impresso no console será "maior de idade", já que a idade é igual a 18, e portanto maior ou igual a 18.

>[!info] Note que a expressão ternária pode ser muito útil para simplificar o código em casos onde a condição é simples e não é necessário executar um grande bloco de código em cada caso. No entanto, em casos onde a condição é mais complexa ou é necessário executar várias instruções em cada caso, a estrutura if/elif/else é geralmente mais adequada.

## Exceções

Podemos fazer testes para evitar erros, e assim permitir que o programa se recupere e continue executando mesmo em situações inesperadas.

Por exemplo, o programa tenta ler dois números do usuário e realizar uma divisão entre eles. No entanto, como podemos ter vários tipos de erros nessa operação (o usuário pode digitar um valor que não é um número inteiro, ou pode tentar dividir por zero), utilizamos a estrutura try/except para capturar e tratar esses erros. Confira no seguinte código em Python:

```python
try:
    x = int(input("Digite um número: "))
    y = int(input("Digite outro número: "))
    resultado = x / y
    print("O resultado da divisão é:", resultado)
except ValueError:
    print("Erro: um dos valores digitados não é um número inteiro")
except ZeroDivisionError:
    print("Erro: divisão por zero")
except Exception as e:
    print("Ocorreu um erro inesperado:", e)

```

Neste exemplo, dentro do bloco try, tentamos ler os valores e realizar a divisão. Se algum erro ocorrer, o programa pula para o bloco except correspondente. Nesse caso, temos três blocos except: um para tratar erros de ValueError (que ocorre quando o usuário digita um valor que não é um número inteiro), um para tratar erros de ZeroDivisionError (que ocorre quando o usuário tenta dividir por zero) e um último bloco para tratar erros genéricos (usando a classe Exception).

>[!info] Se nenhum erro ocorrer durante a execução do bloco try, o programa segue em frente e imprime o resultado da divisão. Caso contrário, o programa imprime uma mensagem de erro apropriada para o tipo de erro capturado.

## Exercícios

1. Escreva um programa que peça ao usuário para digitar a sua idade e informe se ele é maior ou menor de idade.
2. Escreva um programa que peça ao usuário para digitar dois números e informe qual é o maior.
3. Escreva um programa que peça ao usuário para digitar uma letra e informe se ela é uma vogal ou uma consoante.
4. Escreva um programa que peça ao usuário para digitar um número e informe se ele é positivo, negativo ou zero.
5. Escreva um programa que peça ao usuário para digitar o seu salário e informe qual é o seu imposto de renda de acordo com a tabela abaixo:
   - Até R$ 1.903,98: isento
   - De R$ 1.903,99 até R$ 2.826,65: 7,5%
   - De R$ 2.826,66 até R$ 3.751,05: 15%
   - De R$ 3.751,06 até R$ 4.664,68: 22,5%
   - Acima de R$ 4.664,68: 27,5%
6. Escreva um programa que peça ao usuário para digitar a sua altura e o seu peso e informe se ele está abaixo do peso, no peso ideal ou acima do peso. Para isso, utilize o índice de massa corporal (IMC), que é calculado pela fórmula:
   - Para homens: peso ideal = (72.7 x altura) - 58
   - Para mulheres: peso ideal = (62.1 x altura) - 44.7


## Referências

- [W3schools Python reference](https://www.w3schools.com/python/default.asp)
- [Colab - Introdução a programação com a linguagem Python](https://colab.research.google.com/drive/17DTWLVeBgIuwp-FYGIsAxlaj_mRNNMkK?usp=sharing#scrollTo=-F7LD5SJy2eq)
- [Livro na Biblioteca Virtual - Introdução à programação em Python - Sérgio Furgeri](https://bibliotecadigitalsenac.com.br/#/?contentInfo=3011)
