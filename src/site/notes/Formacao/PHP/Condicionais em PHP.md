---
{"dg-publish":true,"permalink":"/formacao/php/condicionais-em-php/","metatags":{"description":"exemplos de códigos de desenvolvimento web"},"noteIcon":2,"updated":"2025-08-24T19:19:07.852-03:00"}
---

#PHP #condicional

Em PHP, as **estruturas condicionais** são ferramentas essenciais que permitem ao código tomar decisões e **executar diferentes blocos de instruções com base em se uma condição específica é verdadeira ou falsa**. Elas são fundamentais para controlar o **fluxo de execução** de um programa, desviando-o do caminho natural sequencial quando determinadas condições são satisfeitas.

Os blocos de comandos, que são conjuntos de instruções relacionadas, são agrupados e delimitados por **chaves `{}`**. Se uma estrutura de controle não usar esses delimitadores, apenas o comando imediatamente seguinte será associado a ela.

A seguir, exploraremos as principais estruturas condicionais em PHP: `if`, `if-else`, `if-elseif-else` e `switch case`.

---

### 1. Comando `if` (Se)

O comando `if` é a estrutura condicional mais básica e serve para **executar um bloco de código somente se uma determinada expressão booleana for avaliada como verdadeira (`TRUE`)**. Se a expressão for falsa, o bloco de comandos é simplesmente ignorado.

- **Sintaxe Básica:**
    
    ```php
    <?php
    if (condição) {
        // Bloco de código a ser executado se a condição for verdadeira
    }
    ?>
    ```
    
- **Observação:** Se houver apenas um comando a ser executado no bloco `if`, as chaves `{}` são opcionais, mas para múltiplos comandos, elas são **obrigatórias** para delimitar o bloco.
    
- **Exemplo Simples:**
    
    ```php
    <?php
    $idade = 17;
    
    if ($idade < 18) { // A condição ($idade < 18) é verdadeira (17 é menor que 18)
        echo "Você não pode entrar aqui!"; // Este comando será executado
    }
    
    echo "<p>Verificação de idade concluída.</p>";
    ?>
    ```
    
    **Saída:**
    
    ```
    Você não pode entrar aqui!
    Verificação de idade concluída.
    ```
    
    Neste caso, a condição `$idade < 18` é verdadeira, então a mensagem "Você não pode entrar aqui!" é exibida.
    

---

### 2. Comando `if-else` (Se-Senão)

A estrutura `if-else` estende o `if` permitindo a execução de **um bloco de código caso a condição seja verdadeira, e um bloco alternativo caso a condição seja falsa**. É como dizer "SE isso for verdade, FAÇA aquilo, SENÃO, FAÇA outra coisa".

- **Sintaxe Básica:**
    
    ```php
    <?php
    if (condição) {
        // Bloco de código a ser executado se a condição for verdadeira
    } else {
        // Bloco de código a ser executado se a condição for falsa
    }
    ?>
    ```
    
- **Exemplo Simples:**
    
    ```php
    <?php
    $idade = 20;
    
    if ($idade < 18) { // A condição ($idade < 18) é falsa (20 não é menor que 18)
        echo "Você não pode entrar aqui!";
    } else { // Este bloco será executado
        echo "Seja bem-vindo!";
    }
    
    echo "<p>Verificação de idade concluída.</p>";
    ?>
    ```
    
    **Saída:**
    
    ```
    Seja bem-vindo!
    Verificação de idade concluída.
    ```
    
    Aqui, a condição `$idade < 18` é falsa, então o bloco do `else` é executado, exibindo "Seja bem-vindo!".
    

---

### 3. Comando `if-elseif-else` (Se-Senão Se-Senão)

Quando há **múltiplas condições a serem testadas em sequência**, a estrutura `if-elseif-else` é a ideal. O PHP verifica cada condição `if` ou `elseif` na ordem em que aparecem. Assim que uma condição é verdadeira, o bloco de código correspondente é executado, e o restante da estrutura é ignorado. Se nenhuma das condições `if` ou `elseif` for verdadeira, o bloco `else` final (que é opcional) será executado.

- **Sintaxe Básica:**
    
    ```php
    <?php
    if (primeira_condição) {
        // Bloco de código para a primeira condição
    } elseif (segunda_condição) {
        // Bloco de código para a segunda condição
    } elseif (terceira_condição) {
        // Bloco de código para a terceira condição
    } else {
        // Bloco de código a ser executado se nenhuma das condições anteriores for verdadeira (opcional)
    }
    ?>
    ```
    
    É possível ter várias estruturas `else-if` após uma declaração `if`.
    
- **Exemplo Simples:**
    
    ```php
    <?php
    $hora = 14;
    
    if ($hora < 12) { // Condição falsa
        echo "Bom dia!";
    } elseif ($hora < 18) { // Condição verdadeira (14 é menor que 18)
        echo "Boa tarde!"; // Este bloco será executado
    } else {
        echo "Boa noite!";
    }
    ?>
    ```
    
    **Saída:**
    
    ```
    Boa tarde!
    ```
    
    Neste exemplo, a primeira condição é falsa. A segunda condição (`$hora < 18`) é verdadeira, então "Boa tarde!" é exibido, e o bloco `else` é ignorado.
    

---

### 4. Comando `switch case` (Escolha Caso)

O comando `switch case` é uma alternativa ao `if-elseif-else` quando se precisa **comparar uma única variável ou expressão com múltiplos valores fixos específicos**. Ele é ideal para situações onde a variável pode ter diversos valores e cada valor implica um fluxo diferente no programa.

- **Sintaxe Básica:**
    
    ```php
    <?php
    switch (variável_ou_expressão) {
        case valor1:
            // Bloco de código se a variável_ou_expressão for igual a valor1
            break; // IMPORTANTE: interrompe o switch
        case valor2:
            // Bloco de código se a variável_ou_expressão for igual a valor2
            break;
        case valorN:
            // Bloco de código se a variável_ou_expressão for igual a valorN
            break;
        default: // Opcional: bloco executado se nenhum dos cases corresponder
            // Bloco de código padrão
            break;
    }
    ?>
    ```
    
- **`case`**: Cada `case` define um valor a ser comparado com a variável do `switch`. Se houver correspondência, o PHP começa a executar as instruções a partir desse `case`.
    
- **`break`**: A instrução `break` é **crucial** dentro de um `switch`. Ela **interrompe a execução do `switch` imediatamente** após um `case` ser correspondido e seu bloco executado, evitando que o PHP continue a "cair" nos `case` seguintes (fenômeno conhecido como "fall-through"). Sem o `break`, todos os `case` seguintes seriam executados até o final do `switch` ou até encontrar um `break`.
    
- **`default`**: É um `case` especial e **opcional** que é executado se nenhum dos `case` anteriores corresponderem ao valor da variável. Quando presente, geralmente é a última instrução.
    
- **Exemplo Simples com `break` e `default`:**
    
    ```php
    <?php
    function traduz_prioridade($codigo) {
        $prioridade = '';
        switch ($codigo) { // Compara o valor de $codigo
            case 1:
                $prioridade = 'Baixa';
                break; // Se for 1, define 'Baixa' e sai do switch
            case 2:
                $prioridade = 'Média';
                break; // Se for 2, define 'Média' e sai do switch
            case 3:
                $prioridade = 'Alta';
                break; // Se for 3, define 'Alta' e sai do switch
            default:
                $prioridade = 'Não definida';
                break; // Se nenhum dos anteriores, define 'Não definida' e sai
        }
        return $prioridade;
    }
    
    echo "Prioridade: " . traduz_prioridade(2) . "<br>"; // Saída: Prioridade: Média
    echo "Prioridade: " . traduz_prioridade(5) . "<br>"; // Saída: Prioridade: Não definida
    ?>
    ```
    
    Neste exemplo, a função `traduz_prioridade` utiliza o `switch` para converter um código numérico em um nome de prioridade. O `break` garante que apenas a prioridade correta seja definida e que a execução do `switch` pare.
    
- **Limitação do `switch`**: Ao contrário do `if`, o `switch` **não pode ser usado para comparar se um valor é maior ou menor que outro** (ex: `$variavel < 10`); ele só aceita valores fixos para comparação nos `case`.
    

---

### 5. Operador Ternário (Atribuição Condicional)

O operador ternário é uma **forma compacta de escrever uma estrutura `if-else` simples em uma única linha**. Ele é particularmente útil para atribuir um valor a uma variável com base em uma condição.

- **Sintaxe Básica:**
    
    ```php
    <?php
    $variavel = (condição) ? valor_se_verdadeiro : valor_se_falso;
    ?>
    ```
    
- **Exemplo Simples:**
    
    ```php
    <?php
    $idade = 18;
    $mensagem = ($idade >= 18) ? "Bem-vindo!" : "Entrada proibida!";
    echo $mensagem;
    
    echo "<br>";
    
    $status = ($idade < 12) ? "Criança" : (($idade < 18) ? "Adolescente" : "Adulto");
    echo $status;
    ?>
    ```
    
    **Saída:**
    
    ```
    Bem-vindo!
    Adulto
    ```
    
    Neste exemplo, a variável `$mensagem` recebe "Bem-vindo!" porque `$idade` é maior ou igual a 18. O segundo exemplo mostra como aninhar operadores ternários para condições mais complexas.
    

As estruturas condicionais são, portanto, pilares da programação em PHP, permitindo que as aplicações reajam dinamicamente a diferentes entradas e estados, tornando-as mais flexíveis e interativas.

[[Formacao/Formacao em PHP\|Formacao em PHP]]
