---
{"dg-publish":true,"permalink":"/tecnico/programador/desafios/desafios-python/saldo-de-transacoes-bancarias/","title":"Saldo de Transações Bancárias","metatags":{"description":"calcular o saldo final da conta com base nas transações realizadas."},"noteIcon":2,"updated":"2026-02-03T07:28:46.685-03:00"}
---

#Lógica #exercícios #Python 

# Saldo de Transações Bancárias

## Descrição

Imagine que você trabalha no setor de TI de um banco e precisa criar um programa que registre as transações de uma conta bancária. Cada transação pode ser um depósito ou um saque, e todas elas serão armazenadas em uma lista. Seu programa deve calcular o saldo final da conta com base nas transações realizadas. Depósitos serão representados como valores positivos e saques como valores negativos.

## Entrada

Uma lista contendo valores inteiros ou decimais representando as transações realizadas (ex.: `[100, -50, 200]`).

- Valores positivos representam depósitos.
- Valores negativos representam saques.

## Saída

O saldo final da conta no formato: `"Saldo: R$ X.XX"`

## Exemplos

A tabela abaixo apresenta exemplos com alguns dados de entrada e suas respectivas saídas esperadas. Certifique-se de testar seu programa com esses exemplos e com outros casos possíveis.

| Entrada           | Saída            |
| ----------------- | ---------------- |
| [100, -50, 200]   | Saldo: R$ 250.00 |
| [500, -200, -100] | Saldo: R$ 200.00 |
| [250 -150, -50]   | Saldo: R$ 50.00  |

**Atenção:** É extremamente importante que as entradas e saídas sejam exatamente iguais às descritas na descrição do desafio de código.

Os desafios apresentados aqui têm como objetivo principal exercitar os conceitos aprendidos e proporcionar um primeiro contato com lógica de programação. Caso não tenha experiência em programação, utilize o template disponível e preencha com os conceitos aprendidos. Para resetar o template, basta clicar em “`Restart Code`”.

Exemplo:

```python
''' 
Para ler e escrever dados em Python, utilizamos as seguintes funções: 
- input: lê UMA linha com dado(s) de Entrada do usuário;
- print: imprime um texto de Saída (Output), pulando linha.  
'''

def calcular_saldo(transacoes):
    saldo = 0

    # TODO: Itere sobre cada transação na lista:
    
        # TODO: Adicione o valor da transação ao saldo
        

    # TODO: Retorne o saldo formatado em moeda brasileira com duas casas decimais:
    

entrada_usuario = input()

entrada_usuario = entrada_usuario.strip("[]").replace(" ", "")

transacoes = [float(valor) for valor in entrada_usuario.split(",")]

# TODO: Calcule o saldo com base nas transações informadas:
resultado = calcular_saldo(transacoes)

print(resultado)
```

## Solução

Para resolver este problema, vamos criar uma função que calcula o saldo final de uma conta bancária após um série de depósitos e saques. A função levará em consideração cada transação individualmente e somará seus valores para determinar o saldo final.

### Explicação do Problema
- **Entrada:** Uma lista de valores inteiros ou decimais, onde os valores positivos representam depósitos e os valores negativos representam saques.
- **Saída:** O saldo final formatado como uma string no formato "Saldo: R$ X.XX", com duas casas decimais.

### Solução
1. **Leitura da Entrada:** A entrada é lida como uma string, que pode conter caracteres especiais como colchetes e espaços. Precisamos remover esses caracterees e dividir a string em valores individuais.
2. **Conversão de Valores:** Cada valor encontrado na entrada será convertido para um número float.
3. **Calculo do Saldo:** Iterando sobre cada valor, somaremos os valores positivos (depósitos) e subtraindimos os valores negativos (saques).
4. **Formatação do Resultado:** O resultado final será formatado com duas casas decimais no formato especificado.

