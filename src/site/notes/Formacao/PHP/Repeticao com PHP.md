---
{"dg-publish":true,"permalink":"/formacao/php/repeticao-com-php/","metatags":{"description":"exemplos de códigos de desenvolvimento web"},"noteIcon":2,"updated":"2025-08-24T19:22:05.711-03:00"}
---

#PHP #loop

> [!abstract] Resumo
> Este artigo aborda as **estruturas de repetição** em PHP, focando inicialmente no _for_, que é ideal quando a **quantidade de repetições é conhecida**. Ele é explicado através de suas três expressões: inicialização, condição de continuidade e atualização, com exemplos práticos como a exibição de números e a iteração sobre arrays. Em seguida,  demonstrando como aninhar laços _for_ para exibir elementos em um array. Posteriormente, é apresentada a estrutura **foreach**, uma forma mais simplificada de percorrer coleções de dados sem a necessidade de índices explícitos. Por fim, detalha as estruturas **while e do-while**, diferenciando-as pela ordem de verificação da condição: o _while_ verifica antes de executar, enquanto o _do-while_ executa pelo menos uma vez antes de verificar, sendo a escolha ideal para cenários específicos. Com isso, o texto busca equipar o leitor com um entendimento abrangente das ferramentas de repetição em PHP, incluindo comandos como _break_ e _continue_ para controle de fluxo dentro dos laços.

# Repetições com PHP

## Automatizando o Fluxo de Execução

No universo da programação, as **Estruturas de Repetição**, popularmente conhecidas como _loops_ ou laços de repetição, são ferramentas indispensáveis. Elas nos permitem executar um bloco de código **múltiplas vezes**, o que é fundamental para automatizar tarefas repetitivas e processar grandes coleções de dados de forma eficiente. Em PHP, a lógica e a sintaxe dessas estruturas são bastante similares às encontradas em outras linguagens de programação imperativas, facilitando o aprendizado e a aplicação.

### 1. O Laço `for`: Para Quando a Contagem Importa

O laço `for` é a escolha ideal quando a **quantidade de repetições é conhecida** antes mesmo do loop começar. Ele é definido por três expressões-chave, separadas por ponto e vírgula, que controlam seu funcionamento:

- **Inicialização**: Esta expressão é executada **apenas uma vez** no início do laço. Seu objetivo principal é declarar e atribuir um valor inicial à variável que controlará as iterações.
- **Condição**: Uma expressão booleana (que retorna `TRUE` ou `FALSE`) é avaliada antes de cada iteração. Se a condição for `TRUE`, o bloco de código dentro do `for` é executado. Se for `FALSE`, o laço é encerrado, e a execução do programa continua após ele.
- **Incremento/Decremento**: Executada ao **final de cada iteração**, esta expressão é responsável por modificar a(s) variável(is) de controle, geralmente incrementando ou decrementando um contador.

**Exemplo Prático:** Contar de 1 a 10 é um uso clássico do `for`. Além disso, é possível aninhar laços `for` (colocar um `for` dentro de outro) para percorrer estruturas mais complexas, como arrays multidimensionais.

**Gerando uma Lista Numérica**

Para gerar uma sequência de números ou elementos com base em um contador, o `for` é a escolha mais natural.

```php
<h3>Exemplo de Contagem com `for`</h3>
<?php
for ($i = 1; $i <= 10; $i++) {
    echo "<p>Item número: " . $i . "</p>";
}
?>
```

Este simples exemplo demonstra como o `for` inicializa `$i`, verifica a condição `$i <= 10` antes de cada iteração e incrementa `$i` após cada execução do bloco, imprimindo números de 1 a 10.

### 2. O Laço `foreach`: O Amigo dos Arrays

O `foreach` é uma das estruturas de repetição mais versáteis e amplamente utilizadas em PHP, especialmente quando o objetivo é **percorrer coleções de dados, como arrays ou matrizes**. Diferentemente do laço `for`, o `foreach` foi projetado para simplificar a iteração sobre todos os elementos de uma coleção **sem a necessidade de gerenciar explicitamente um contador ou índice**. Ele se torna indispensável em diversas aplicações web, como na exibição de listas de usuários, produtos ou mensagens de validação de formulários.

Sua sintaxe básica é muito intuitiva:

- `foreach (expressão_array as $valor) { comandos; }`
    - A cada iteração, um valor do array é atribuído à variável `$valor`.
- `foreach (expressão_array as $chave => $valor) { comandos; }`
    - Se você precisar tanto do índice (chave) quanto do valor, esta sintaxe permite acessar ambos.

**Uso Comum:** Em frameworks como Laravel, o `foreach` é amplamente empregado para listar e exibir registros recuperados de um banco de dados. Para maior legibilidade em templates HTML, como os usados no Laravel, a sintaxe `<?php foreach (...): ?> ... <?php endforeach; ?>` é frequentemente recomendada.

Vamos a um exemplo simples para ilustrar seu funcionamento:

Suponha que temos um array com nomes de frutas e queremos exibir cada fruta em uma lista no navegador:

```php
<?php
// Define um array simples de frutas
$frutas = array("maçã", "laranja", "pêra", "banana");

// Utiliza o laço foreach para iterar sobre cada fruta no array
foreach ($frutas as $fruta) {
    echo $fruta . "<br>"; // Exibe o nome da fruta seguido de uma quebra de linha HTML
}
?>
```

**Explicação detalhada:**

- **`$frutas = array("maçã", "laranja", "pêra", "banana");`**:
    - Aqui, inicializamos uma variável chamada `$frutas` como um **array**, que é uma estrutura de dados capaz de armazenar múltiplos valores (neste caso, strings).
- **`foreach ($frutas as $fruta)`**:
    - Esta é a sintaxe fundamental do `foreach`.
    - Ela instrui o PHP a **iterar sobre cada elemento** do array `$frutas`.
    - Em cada iteração, o valor do elemento atual do array `$frutas` é **atribuído temporariamente** à variável `$fruta`.
    - O laço continua executando o bloco de código interno para cada elemento, até que todos os itens do array `$frutas` tenham sido processados.
- **`echo $fruta . "<br>";`**:
    - Dentro do bloco do `foreach`, a instrução `echo` é utilizada para **imprimir o valor** contido na variável `$fruta` (que é o item atual do array).
    - O `. "<br>"` concatena o nome da fruta com uma tag HTML de quebra de linha, garantindo que cada fruta seja exibida em uma nova linha no navegador.

**Saída esperada no navegador:**

```
maçã
laranja
pêra
banana
```

Este exemplo demonstra como o `foreach` permite **acessar e manipular facilmente cada item de uma coleção**, tornando o código mais intuitivo e menos propenso a erros relacionados a índices. Além da forma `as $valor`, o `foreach` também pode ser usado para acessar tanto a chave quanto o valor de um array, utilizando a sintaxe `foreach ($array as $chave => $valor)`.

### 3. O Laço `while`: Repita Enquanto a Condição For Verdadeira

O laço `while` estabelece um bloco de repetição que **continua executando enquanto uma condição específica for verdadeira**. Sua principal característica é que a condição é **verificada no início de cada iteração**.

- Se a condição for `TRUE`, o bloco de código é executado.
- Se a condição for `FALSE`, o loop é encerrado.

**Sintaxe:** `while (expressão) { comandos; }`.

**Atenção:** É **fundamental** que a condição do `while` eventualmente se torne `FALSE`, caso contrário, você terá um _loop_ infinito, o que pode travar sua aplicação, o navegador ou até mesmo o servidor. Assim como o `foreach`, o `while` também pode ser usado para iterar sobre resultados de banco de dados.

**Exemplo: Processando um Número Fixo de Operações (com condição)**

```php
<h3>Exemplo de Repetição com `while`</h3>
<?php
$tentativas = 0;
$max_tentativas = 3;

while ($tentativas < $max_tentativas) {
    echo "<p>Tentativa de processamento: " . ($tentativas + 1) . "</p>";
    $tentativas++; // Incrementa o contador para evitar um loop infinito
}
echo "<p>Processamento concluído após " . $tentativas . " tentativas.</p>";
?>
```

Aqui, o loop continua enquanto `$tentativas` for menor que `$max_tentativas`. A cada iteração, `$tentativas` é incrementada, o que eventualmente fará a condição ser falsa e o loop será encerrado

### 4. O Laço `do-while`: Execute Pelo Menos Uma Vez

O `do-while` é muito semelhante ao `while`, mas com uma diferença crucial: o bloco de código é **executado pelo menos uma vez**, **antes que a condição seja avaliada**. A condição é testada apenas ao final de cada execução do bloco.

**Sintaxe:** `do { comandos; } while (expressão);`.

**Cenário de Uso:** Esta estrutura é útil em situações onde a ação dentro do loop precisa ocorrer ao menos uma vez, independentemente da condição inicial, como na primeira exibição de um formulário ou na tentativa inicial de uma operação.

Exemplo: **Execução Inicial Obrigatória**

```php
<h3>Exemplo de Repetição com `do-while`</h3>
<?php
$opcao = 0; // Suponha que 0 não é uma opção válida para continuar
do {
    echo "<p>Executando o bloco. Opção atual: " . $opcao . "</p>";
    $opcao = rand(1, 5); // Simula uma ação que define a próxima opção
    // O loop continua se a opção não for 3 (condição para sair)
} while ($opcao != 3);
echo "<p>Saindo do loop. Opção final: " . $opcao . "</p>";
?>
```

Neste exemplo, mesmo que `$opcao` fosse `3` inicialmente, o bloco de código dentro do `do` seria executado uma vez, gerando uma nova opção antes de a condição `($opcao != 3)` ser testada. Isso garante a execução inicial do processo, útil para interações com o usuário ou validações pós-ação.

### Controle de Fluxo Dentro dos Laços: `break` e `continue`

Para um controle ainda mais fino sobre a execução dos laços, o PHP oferece duas instruções especiais:

- **`break`**: Esta instrução é usada para **encerrar imediatamente a execução do laço atual**. Após o `break`, o programa continua a execução a partir do primeiro comando que segue o laço. Em laços aninhados, é possível especificar qual nível de laço deve ser interrompido (ex: `break 2;` para sair de dois níveis de laço).
    
- **`continue`**: A instrução `continue` faz com que o laço **pule as instruções restantes da iteração atual** e passe diretamente para a próxima iteração. O fluxo de controle retorna ao início do laço para reavaliar a condição (para `while` e `for`) ou para processar o próximo elemento (para `foreach`).
    

`break` e `continue` são comandos muito úteis para controlar o fluxo de execução dentro das estruturas de repetição, oferecendo flexibilidade para lidar com cenários específicos sem ter que esperar o laço terminar naturalmente. Eles são aplicáveis em `for`, `foreach`, `while` e `do-while`.

Vamos a exemplos simples para entender como cada um funciona em um laço `for`.

---

#### 1. O Comando `break`: Interrompendo o Laço Completamente

O comando `break` é usado para **abortar (parar) a execução do loop atual instantaneamente**, fazendo com que o programa continue a execução na primeira linha de código **após o bloco do loop**. É como um "ponto final" para o laço quando uma condição específica é atendida. O fluxo de execução "salta" para fora do bloco onde o `break` está contido.

**Exemplo Prático com `break`:**

Vamos simular um processo de busca por um item em uma lista, onde queremos parar a busca assim que o item for encontrado.

```php
<?php
$itens = ["maçã", "banana", "laranja", "pêra", "uva"];
$item_procurado = "laranja";
$encontrado = false;

echo "<h3>Buscando por '" . $item_procurado . "' na lista:</h3>";

for ($i = 0; $i < count($itens); $i++) {
    echo "Verificando item na posição " . $i . ": " . $itens[$i] . "<br>";

    if ($itens[$i] === $item_procurado) {
        echo "**Item '" . $item_procurado . "' encontrado na posição " . $i . "!**<br>";
        $encontrado = true;
        break; // Interrompe o loop completamente
    }
}

if (!$encontrado) {
    echo "Item '" . $item_procurado . "' não foi encontrado após a busca.<br>";
}

echo "<p>Execução continuada após o loop.</p>";
?>
```

**Saída Esperada e Explicação:**

```
Buscando por 'laranja' na lista:
Verificando item na posição 0: maçã
Verificando item na posição 1: banana
Verificando item na posição 2: laranja
**Item 'laranja' encontrado na posição 2!**
Execução continuada após o loop.
```

Neste exemplo:

- O loop `for` é iniciado para percorrer o array `$itens`.
- A cada iteração, ele imprime o item que está sendo verificado.
- Quando o `$itens[$i]` (o item atual) é igual a `$item_procurado` ("laranja"), a condição `if` é verdadeira.
- A mensagem de item encontrado é exibida.
- Em seguida, o `break` é executado, e o **loop é imediatamente encerrado**. Todas as iterações restantes (para "pêra" e "uva") são ignoradas.
- O programa então prossegue para as linhas de código que vêm depois do loop, imprimindo "Execução continuada após o loop.".

#### 2. O Comando `continue`: Saltando a Iteração Atual

O comando `continue` é utilizado para **saltar a execução do resto da iteração atual do loop e mover o fluxo para a próxima iteração**. Em outras palavras, ele ignora as instruções que viriam após o `continue` dentro do bloco atual do loop, mas permite que o loop continue suas próximas iterações.

**Exemplo Prático com `continue`:**

Vamos exibir uma sequência de números, mas queremos pular um número específico ou uma condição para processamento.

```php
<?php
echo "<h3>Contando de 1 a 5, mas pulando o número 3:</h3>";

for ($i = 1; $i <= 5; $i++) {
    if ($i == 3) {
        echo "Pulando o número " . $i . " (continue)<br>";
        continue; // Pula o restante do código desta iteração
    }
    echo "Processando o número: " . $i . "<br>";
}

echo "<p>Execução continuada após o loop.</p>";
?>
```

**Saída Esperada e Explicação:**

```
Contando de 1 a 5, mas pulando o número 3:
Processando o número: 1
Processando o número: 2
Pulando o número 3 (continue)
Processando o número: 4
Processando o número: 5
Execução continuada após o loop.
```

Neste exemplo:

- O loop `for` itera de 1 a 5.
- Quando `$i` é igual a `1` ou `2`, a condição `if ($i == 3)` é falsa, e a linha "Processando o número: " é executada.
- Quando `$i` se torna `3`, a condição `if ($i == 3)` é verdadeira.
- A mensagem "Pulando o número 3 (continue)" é exibida.
- O `continue` é executado, e o PHP **salta imediatamente para a próxima iteração** do loop (onde `$i` se tornará `4`), ignorando a linha `echo "Processando o número: " . $i . "<br>";` que viria logo em seguida para `$i = 3`.
- O loop continua normalmente para `$i = 4` e `$i = 5`.
- Após o término do loop, o programa prossegue para a linha `echo "<p>Execução continuada após o loop.</p>";`.

Em resumo, enquanto `break` para todo o laço, `continue` apenas pula a iteração atual e avança para a próxima, sem interromper o laço por completo.

### Aplicações no Desenvolvimento Web com PHP

As estruturas de repetição são a espinha dorsal de muitas funcionalidades em aplicações web PHP:

- **Manipulação e Exibição de Dados**: São amplamente utilizadas para exibir listas de usuários, produtos, notícias ou qualquer outro tipo de registro recuperado de um banco de dados, tornando as páginas dinâmicas.
- **Processamento de Formulários**: Podem iterar sobre arrays de dados enviados por formulários, como múltiplos _checkboxes_ selecionados, facilitando a coleta e tratamento das informações.
- **Integração com Frameworks (Laravel)**: Frameworks como Laravel fazem uso extensivo dessas estruturas para renderizar _views_ dinamicamente, muitas vezes em conjunto com ORMs (Mapeamento Objeto-Relacional) para simplificar a recuperação e exibição de dados do banco de dados. Modelos (Models) do Laravel são usados para interagir com o banco de dados, permitindo operações como criação, listagem, edição e exclusão de registros.
- **Reusabilidade de Código**: Funções "ajudantes" (_helpers_) frequentemente encapsulam laços de repetição para formatar coleções de dados, como datas ou status, padronizando a apresentação.
- **Validação de Formulários**: Loops podem ser usados para percorrer e exibir múltiplas mensagens de erro de validação para o usuário, como no exemplo de usar um `foreach` para exibir erros `@errors` em Laravel.
- **Paginação**: Essenciais para criar links de navegação entre diferentes páginas de resultados, dividindo grandes volumes de dados em blocos gerenciáveis para o usuário.

Dominar essas estruturas é, portanto, um conhecimento fundamental. Elas capacitam o desenvolvedor a escrever códigos mais eficientes, dinâmicos e fáceis de manter, sendo a base para a criação de sistemas web robustos e interativos em PHP.

---

[[Formacao/Formacao em PHP\|Formacao em PHP]]
