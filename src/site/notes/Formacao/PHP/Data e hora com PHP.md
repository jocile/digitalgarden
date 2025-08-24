---
{"dg-publish":true,"permalink":"/formacao/php/data-e-hora-com-php/","metatags":{"description":"exemplos de códigos de desenvolvimento web"},"noteIcon":2,"updated":"2025-08-24T17:30:07.302-03:00"}
---

#PHP #POO #data

>[!abstract] Resumo
>O tutorial introduz a **manipulação de datas e horas em PHP**, começando com o método básico `date()` para formatação simples. Embora útil para exibir dados, o método `date()` possui **limitações significativas para manipulações mais complexas**, como cálculos de diferença ou adição/subtração de períodos. Para resolver isso, o curso apresenta a **classe `DateTime`**, uma solução orientada a objetos que oferece métodos robustos para formatação e, crucialmente, manipulação avançada de datas. Complementarmente, a **classe `DateInterval`** é ensinada como ferramenta essencial para definir e aplicar períodos de tempo, permitindo adicionar ou subtrair anos, meses, dias, horas, minutos e segundos de forma fluida e eficiente de uma data `DateTime`.

# Data e Hora no PHP

## Definições

A manipulação de datas é uma funcionalidade **fundamental em praticamente qualquer sistema**. Em PHP, existem diversas formas de trabalhar com datas e horas, desde funções mais básicas até classes orientadas a objetos, e a integração com bancos de dados e formulários web exige atenção especial às conversões e formatações.

### Funções Básicas: `date()`

Para começar a trabalhar com datas em PHP, a forma mais básica é utilizando a **função `date()`**. Esta função é usada para **formatar datas e horas locais** (do servidor onde o PHP está rodando).

- Ela **retorna uma string com a data formatada** de acordo com os parâmetros fornecidos.
- Parâmetros como `d` (dia, de 01 a 31), `m` (mês), `Y` (ano com quatro dígitos) ou `y` (ano com dois dígitos), `H` (hora no formato 24h), `i` (minutos) e `s` (segundos) são utilizados para definir o formato de saída. Por exemplo, `date("d/m/Y")` exibiria a data como "12/12/2019".
- Apesar de simples, a função `date()` possui **limitações para a manipulação de datas**, como calcular diferenças, somar ou diminuir períodos, o que exigiria o uso de várias outras funções nativas.

### Abordagem Orientada a Objetos: `DateTime` e `DateInterval`

Para manipulações mais complexas e de forma orientada a objetos, o PHP oferece a **classe `DateTime`**.

- A classe `DateTime` é **completa e possui métodos** que facilitam o trabalho do desenvolvedor.
- Você **cria uma instância da classe `DateTime`** para ter um objeto que representa uma data e hora específicas.
- Ela permite **adicionar períodos** (`add()` método), **subtrair períodos** (`sub()` método) e **calcular a diferença entre duas datas** (`diff()` método).
- Para formatar a data de um objeto `DateTime`, você usa o **método `format()`**, que funciona de forma semelhante à função `date()`.

A manipulação de períodos é feita em conjunto com a **classe `DateInterval`**.

- A classe `DateInterval` permite **definir intervalos de tempo**.
- Ao criar uma instância de `DateInterval`, você passa uma string formatada (ex: `P5Y10M5D` para 5 anos, 10 meses e 5 dias, e `T10H50M10S` para 10 horas, 50 minutos e 10 segundos) que representa o período.
- Esse objeto `DateInterval` é então utilizado pelos métodos `add()` ou `sub()` da classe `DateTime` para manipular a data.

### Manipulação de Datas em Formulários e Bancos de Dados

A manipulação de datas também é crucial na interação entre formulários web e bancos de dados.

- **Fuso Horário (Time Zone)**: É importante definir o fuso horário correto da aplicação (ex: `America/Sao_Paulo` ou `America/Brasilia`) em arquivos de configuração como o `.env`. Isso garante que as datas e horas sejam registradas e exibidas corretamente.
- **Formatos de Data**: Há uma **diferença comum entre o formato de data utilizado pelo Brasil (DIA/MÊS/ANO)** e o formato padrão de bancos de dados como o MySQL (ANO-MÊS-DIA).
    - Isso exige a criação de "tradutores" ou **funções auxiliares (helpers)** que convertem a data do formato de entrada do usuário para o formato do banco e vice-versa.
    - Funções como `traduz_data_para_banco()` e `traduz_data_para_exibir()` são exemplos de como essas conversões podem ser implementadas, frequentemente utilizando `explode()` para separar as partes da string da data e depois reconstruí-la no formato desejado.
- **Validação de Datas**: Formulários devem validar se as datas inseridas são válidas, tanto em termos de **formato (DIA/MÊS/ANO)** quanto em termos de existência (evitar "31 de fevereiro").
    - **Expressões regulares** podem ser usadas para validar o formato de entrada da data, verificando padrões como `DD/MM/YYYY`.
    - As funções de tradução de data devem ser robustas o suficiente para lidar com datas vazias ou formatos inesperados, retornando uma string vazia ou a data original, se a validação falhar.
- **Tipos de Dados em MySQL**: No MySQL, colunas podem ser definidas com tipos como `DATE`, `TIME`, `DATETIME` ou `TIMESTAMP` para armazenar datas e horas.
- **Criptografia**: Em contextos de segurança, como senhas, o Laravel pode se encarregar de criptografar automaticamente, mas se a criptografia manual for implementada, é preciso atenção à quantidade de "saltos" (salts) configurada no arquivo `.env` (ex: 12).

Em resumo, a manipulação de datas em PHP, especialmente em aplicações web dinâmicas, envolve o uso inteligente de funções e classes nativas (`date()`, `DateTime`, `DateInterval`), a conversão entre diferentes formatos (usuário vs. banco de dados), a validação de entradas e a correta configuração de fuso horário.

## Exemplo

A manipulação de datas é uma **funcionalidade essencial** em sistemas e aplicações, e o PHP oferece ferramentas robustas para isso, desde funções básicas até classes orientadas a objetos. Para ilustrar as capacidades de manipulação de datas em PHP, especialmente com o Laravel, podemos usar a classe `DateTime` e `DateInterval`, que facilitam muito o trabalho com formatação, adição, subtração e cálculo de diferenças entre datas.

### Exemplo Prático de Manipulação de Datas em PHP

```php
<?php
// 1. Definir o fuso horário da aplicação
// É importante definir o fuso horário correto para a aplicação, garantindo que as datas e horas
// sejam registradas e exibidas corretamente. O fuso horário de São Paulo, por exemplo,
// é o mesmo de Brasília no momento. [i, 2, 7, 90]
date_default_timezone_set('America/Sao_Paulo');

echo "<h3>Exemplo Prático de Manipulação de Datas em PHP:</h3>";

// 2. Criar uma instância da data e hora atuais
// A classe DateTime é completa e possui métodos que facilitam o trabalho do desenvolvedor.
// Ela permite criar um objeto que representa uma data e hora específicas. [i, 333, 335]
$dataAtual = new DateTime();
echo "Data e Hora Atuais (Formato Padrão ISO 8601): " . $dataAtual->format('Y-m-d H:i:s') . " [i, 337, 338]<br>";

// 3. Formatar a data para o padrão brasileiro
// O Laravel oferece bibliotecas que auxiliam na formatação de datas. No Brasil, o formato
// DIA/MÊS/ANO é o mais comum, diferente do padrão de bancos de dados. [i, 8, 240]
echo "Data e Hora Atuais (Formato Brasileiro): " . $dataAtual->format('d/m/Y H:i:s') . " [i, 8, 337, 338]<br>";

echo "<br>";

// 4. Manipular datas: Adicionar períodos
// Para adicionar períodos, utiliza-se o método add() da classe DateTime em conjunto com
// a classe DateInterval. DateInterval permite definir intervalos de tempo. [i, 334, 340, 342]
// Exemplo: Adicionar 5 dias, 10 horas e 30 minutos.
$intervaloAdicionar = new DateInterval('P5DT10H30M'); // P para período, D para dias, T para tempo, H para horas, M para minutos. [i, 341]
$dataFutura = clone $dataAtual; // Clona o objeto para não modificar a data original.
$dataFutura->add($intervaloAdicionar); // Adiciona o intervalo à data. [i, 334, 342]
echo "Data e Hora em 5 dias, 10 horas e 30 minutos: " . $dataFutura->format('d/m/Y H:i:s') . " [i, 8, 337, 338]<br>";

// 5. Manipular datas: Subtrair períodos
// De forma similar, o método sub() permite subtrair períodos de uma data. [i, 334, 343]
// Exemplo: Subtrair 2 meses e 15 dias.
$intervaloSubtrair = new DateInterval('P2M15D'); // M para meses. [i, 343]
$dataPassada = clone $dataAtual;
$dataPassada->sub($intervaloSubtrair); // Subtrai o intervalo da data. [i, 334, 343]
echo "Data e Hora há 2 meses e 15 dias: " . $dataPassada->format('d/m/Y H:i:s') . " [i, 8, 337, 338]<br>";

echo "<br>";

// 6. Calcular a diferença entre duas datas
// A classe DateTime também possui o método diff() para calcular a diferença entre duas datas,
// retornando um objeto DateInterval com os componentes da diferença (anos, meses, dias, etc.). [i, 335]
$dataInicio = new DateTime('2023-01-01');
$dataFim = new DateTime('2024-03-15');
$diferenca = $dataInicio->diff($dataFim); // Calcula a diferença. [i, 335]

echo "Diferença entre " . $dataInicio->format('d/m/Y') . " e " . $dataFim->format('d/m/Y') . ": [i, 8, 337, 338]<br>";
echo "Anos: " . $diferenca->y . " [i]<br>";
echo "Meses: " . $diferenca->m . " [i]<br>";
echo "Dias: " . $diferenca->d . " [i]<br>";

echo "<br>";

// 7. Converter string de data (formato brasileiro) para objeto DateTime
// A DevMedia aborda a manipulação de strings e a necessidade de "tradutores" para converter
// entre formatos de data de entrada do usuário e do banco de dados. [i, 45, 240, 358, 457, 470, 483]
$dataStringBrasileira = "25/12/2024 10:00:00";
// Embora a função DateTime::createFromFormat não seja explicitamente nomeada nas fontes
// para essa conversão, o conceito de "tradutores" de datas implica a necessidade de funções
// que parseiem strings com formatos específicos para objetos de data.
$dataConvertida = DateTime::createFromFormat('d/m/Y H:i:s', $dataStringBrasileira);
if ($dataConvertida) {
    echo "Data convertida de '{$dataStringBrasileira}' para objeto DateTime: " . $dataConvertida->format('Y-m-d H:i:s') . " [i, 337, 338]<br>";
} else {
    echo "Erro ao converter a data '{$dataStringBrasileira}'. [i]<br>";
}
?>
```

**Explicação do Exemplo:**

1. **Configuração de Fuso Horário**: É fundamental iniciar com `date_default_timezone_set()` para definir o fuso horário da aplicação, como `America/Sao_Paulo`. Isso garante a correta interpretação e exibição das horas e datas .
2. **Instanciação de `DateTime`**: Criamos um objeto `DateTime` sem parâmetros para obter a data e hora atuais do servidor. Essa é a base para a manipulação orientada a objetos.
3. **Formatação de Datas**: Usamos o método `format()` do objeto `DateTime` para exibir a data em diferentes padrões. Por exemplo, `Y-m-d H:i:s` para um formato mais técnico (similar ao de banco de dados) e `d/m/Y H:i:s` para o padrão brasileiro.
4. **Adição e Subtração de Períodos**: Para manipular datas, ou seja, adicionar ou subtrair tempo, utilizamos a classe `DateInterval`. Um objeto `DateInterval` é criado com uma string que especifica o período (ex: `P5DT10H30M` para 5 dias, 10 horas e 30 minutos). Em seguida, os métodos `add()` ou `sub()` de `DateTime` aplicam esse intervalo à data .
5. **Cálculo de Diferença**: O método `diff()` de `DateTime` permite calcular a diferença entre duas datas, retornando um objeto `DateInterval` que pode ser usado para acessar as propriedades de anos (`y`), meses (`m`) e dias (`d`) da diferença.
6. **Conversão de String para `DateTime`**: A conversão de strings de data (como o formato brasileiro `DD/MM/YYYY HH:MM:SS`) para objetos `DateTime` é crucial, especialmente ao lidar com entradas de formulários e dados de banco de dados. Embora funções como `explode()` possam ser usadas para quebrar a string, `DateTime::createFromFormat` é uma abordagem mais robusta em PHP para parsear datas de formatos específicos para objetos `DateTime`. As fontes mencionam a necessidade de "tradutores" para converter entre formatos, e esta função serve a esse propósito.

Este exemplo demonstra como o PHP, especialmente com o auxílio de bibliotecas e classes, oferece uma abordagem flexível e poderosa para a manipulação de datas, essencial para o desenvolvimento web. No contexto do desenvolvimento PHP, é importante cuidar dos tipos de dados, embora PHP seja fracamente tipado, definir os tipos de retorno e parâmetros para métodos e funções é uma boa prática para garantir a consistência e facilitar a leitura do código.

[[Formacao/Formacao em PHP\|Formacao em PHP]]
