---
{"dg-publish":true,"permalink":"/formacao/php/metodos-com-php/","metatags":{"description":"exemplos de códigos de desenvolvimento web"},"noteIcon":2,"updated":"2025-08-24T17:15:53.459-03:00"}
---

#PHP #POO

>[!abstract] Resumo
>O texto explora a **programação orientada a objetos (POO) em PHP**, focando na implementação de classes, métodos e o conceito de construtores. Primeiramente, explica que **métodos são as ações ou funções de uma classe**, como "obter saldo", e demonstra como definir sua visibilidade (pública ou privada) e padrão de nomenclatura. Em seguida, detalha o **método construtor, uma função especial que é executada automaticamente** quando uma instância da classe é criada, sendo crucial para inicializar os atributos do objeto de forma dinâmica e segura. O autor enfatiza a importância de **tornar os atributos privados para proteger os dados** e utilizar métodos públicos (como "depositar" e "sacar") para interagir com eles, garantindo a integridade da classe. Por fim, o texto introduz a **tipagem estrita em PHP**, mostrando como declarar os tipos de dados para atributos e parâmetros, o que melhora a robustez e a legibilidade do código.

## Métodos

Em PHP, no contexto da Programação Orientada a Objetos (POO), os **métodos** são as **ações ou funções que pertencem a uma classe**. Eles definem o comportamento que os objetos criados a partir dessa classe podem realizar.

### Finalidade dos Métodos em PHP

Os métodos servem a várias finalidades essenciais em POO:

- **Implementar a lógica específica** que os objetos de uma classe devem executar. Por exemplo, em uma classe `ContaBancaria`, haveria métodos como `depositar`, `sacar` ou `obterSaldo`.
- **Manipular os atributos (propriedades)** de um objeto. Isso inclui acessar (`Get` ou "geteres") e modificar (`Set` ou "seteres") os valores dos atributos, garantindo o **encapsulamento** dos dados da classe. O encapsulamento protege as variáveis de uma classe, impedindo o acesso direto e garantindo que suas alterações ocorram de forma controlada.
- **Promover a reutilização de código**, pois uma função definida como método em uma classe pode ser chamada diversas vezes por diferentes objetos dessa classe.
- **Organizar o código** de forma mais estruturada e legível, centralizando as regras e lógicas relacionadas a uma entidade em um único local.

### Sintaxe e Funcionamento dos Métodos

A definição de um método em PHP segue uma sintaxe clara e possui características importantes:

- **Visibilidade (Modificador de Acesso)**: Todos os elementos de classe, incluindo métodos, precisam ter um modificador de acesso declarado.
    - `public`: Permite que o método seja acessado de qualquer lugar, dentro ou fora da classe.
    - `private`: Restringe o acesso ao método apenas de dentro da própria classe.
    - `protected`: Permite acesso ao método de dentro da classe e de suas classes filhas (herdeiras).
- **Palavra-chave `function`**: Utilizada para declarar o método, seguida pelo seu nome, parênteses (para parâmetros, se houver) e chaves `{}` para o bloco de código.
    
    ```
    public function nomeDoMetodo($parametro1, $parametro2) {
        // Lógica do método
        return $valor;
    }
    ```
    
- **Parâmetros**: Métodos podem receber parâmetros, assim como funções normais em PHP.
- **`$this->`**: Dentro de um método, a palavra-chave `$this->` é usada para se referir aos atributos e a outros métodos do próprio objeto (a instância atual da classe). Por exemplo, `$this->saldo` acessaria o atributo `saldo` do objeto.
- **Valor de Retorno (`return`)**: Uma função pode opcionalmente retornar um valor, que pode ser de diversos tipos (inteiro, string, array, objeto, etc.).
- **Nomenclatura**: É uma prática comum nomear métodos que retornam o valor de um atributo com o prefixo "get" (ex: `getCodigo()`, `getNome()`) e métodos que alteram um atributo com o prefixo "set" (ex: `setCodigo()`, `setNome()`).
- **Chamada de Método**: Para invocar um método de um objeto, utiliza-se o operador `->` seguido do nome do método e parênteses.

### Tipos Especiais de Métodos

Além dos métodos comuns, existem alguns tipos especiais:

- **Método Construtor (`__construct`)**: É um método mágico (identificado por dois underscores `__` no início) que é **automaticamente executado toda vez que uma nova instância de uma classe é criada**. Sua função principal é inicializar os atributos do objeto com valores específicos no momento da sua criação.
- **Métodos Estáticos**: São métodos que podem ser chamados diretamente na classe, sem a necessidade de criar uma instância (objeto) da classe. Para isso, usa-se a palavra-chave `static` na sua declaração e a sintaxe `NomeDaClasse::nomeDoMetodo()` para chamá-los.

A utilização de métodos é um pilar da Programação Orientada a Objetos em PHP, permitindo a criação de sistemas mais organizados, modulares e de fácil manutenção.

## Construtor

O método Construtor, em Programação Orientada a Objetos (POO) com PHP, possui uma finalidade específica e uma sintaxe particular que o diferencia dos demais métodos de uma classe.

### Finalidade do Método Construtor em POO

O Construtor (`__construct`) é um método especial que é **automaticamente executado toda vez que uma nova instância (objeto) de uma classe é criada** utilizando a palavra-chave `new`. Sua principal finalidade é:

- **Inicializar os atributos de um objeto com valores específicos no momento de sua criação**. Isso garante que o objeto já nasça em um estado válido e funcional, conforme as regras de negócio definidas. Por exemplo, para que um objeto "Usuário" possa existir, ele pode precisar obrigatoriamente de um nome de usuário e uma senha que são passados ao construtor.
- **Centralizar a lógica de configuração inicial** de um objeto, evitando que os atributos precisem ser definidos um a um após a sua criação.
- Permitir a criação genérica de **múltiplos objetos da mesma classe**, cada um com seus próprios dados iniciais, passados durante a instanciação.

### Sintaxe do Método Construtor em POO

A sintaxe para definir um método construtor em PHP é a seguinte:

- O método construtor é definido como um método público e recebe o nome **`__construct`**. Os dois sublinhados (`__`) no início indicam que é um "método mágico" do PHP.
    
- **Sintaxe básica:**
    
    ```
    public function __construct() {
        // Lógica de inicialização dos atributos
    }
    ```
    
- Geralmente, o construtor **recebe parâmetros** que correspondem aos valores que serão usados para inicializar os atributos do objeto. Por exemplo, ao criar uma `ContaBancaria`, pode-se passar o banco, nome do titular, número da agência, número da conta e saldo atual diretamente para o construtor.
    
- Dentro do construtor, a palavra-chave **`$this->`** é utilizada para se referir aos atributos do próprio objeto (da instância atual) e atribuir a eles os valores recebidos como parâmetros. Por exemplo: `$this->banco = $banco;`.
    
- Em versões mais recentes do PHP (a partir do 7.4), é possível **declarar os tipos** tanto para os atributos da classe quanto para os parâmetros do construtor, o que melhora a clareza do código e permite a validação automática de tipos durante a execução. Se um tipo incorreto for passado, um erro de tipo será retornado.
    

Em resumo, o método construtor é essencial para garantir que os objetos de uma classe sejam inicializados de forma consistente e com os dados necessários, agilizando o desenvolvimento e a manutenção do código.

## Get

Os métodos "Get", ou "métodos geteres", são funções essenciais na Programação Orientada a Objetos (POO) em PHP, com uma finalidade e um funcionamento bem definidos.

### Finalidade dos Métodos Get

A principal finalidade dos métodos Get é **retornar o valor de um atributo (propriedade) de uma classe**. Eles são fundamentais para o conceito de **encapsulamento**, que é uma forma de proteção do código. Por boas práticas de programação, os atributos de uma classe são frequentemente declarados como `private` (privados) ou `protected` (protegidos), o que impede o acesso direto a eles de fora da classe.

Nesse cenário, os métodos Get atuam como uma interface pública ou controlada, permitindo que outras partes do código, ou mesmo a própria classe, **verifiquem ou recuperem o valor desses atributos privados** de forma segura. Isso garante que os dados internos de um objeto sejam acessados de maneira controlada, sem que sejam diretamente expostos ou passíveis de alteração indevida.

Por exemplo, se um atributo como o saldo de uma conta bancária for privado, ele não pode ser acessado diretamente. Um método `obterSaldo()` público é criado para retornar esse valor, assegurando que o saldo esteja seguro e sua manipulação ocorra apenas através de métodos específicos (como depositar ou sacar).

### Funcionamento e Sintaxe

- **Nomenclatura**: Por padrão de nomenclatura, os métodos Get geralmente começam com o prefixo "get" seguido pelo nome do atributo que se deseja retornar, por exemplo, `getCodigo()` ou `getId()`.
- **Visibilidade**: São comumente definidos com a visibilidade `public` para que possam ser utilizados fora da classe, permitindo o acesso aos atributos encapsulados.
- **Parâmetros**: Geralmente, um método Get **não precisa de parâmetros**, pois sua função é retornar um valor que já existe no atributo do objeto.
- **Retorno**: Um método Get **retorna um valor**, que pode ser de diferentes tipos primitivos de dados (como `int`, `string`, `double`, `float`, `char`, `boolean`), ou até mesmo um objeto, ou pode retornar `void` (vazio) se não houver um valor a ser retornado ou a ação for outra. A palavra-chave `return` é utilizada para especificar o valor que será devolvido.
- **Acesso ao Atributo Interno**: Dentro do método Get, a palavra-chave **`$this->`** é usada para se referir ao atributo do próprio objeto (`$this` representa a própria instância da classe) e, em seguida, retornar seu valor. Por exemplo, `return $this->saldo;`.
- **Contraste com Set**: Métodos Get são o complemento dos métodos "Set" (seteres), que são responsáveis por armazenar ou **alterar os valores nos atributos** de uma classe.

Em suma, os métodos Get são uma parte fundamental da POO, permitindo acesso controlado e seguro aos dados internos dos objetos, aderindo aos princípios de encapsulamento e melhorando a organização e manutenção do código.

## Exemplo

Continuando com o exemplo da **`ContaBancaria`** em Programação Orientada a Objetos (POO) com PHP, podemos implementar métodos que representam as ações que uma conta bancária pode realizar, como obter o saldo, depositar e sacar. Isso reforça o conceito de **encapsulamento**, onde os atributos internos da classe são protegidos e manipulados apenas através de métodos específicos.

### Atributos da Classe `ContaBancaria`

Primeiramente, é importante definir os atributos da classe `ContaBancaria` como **privados** (`private`), para que não possam ser alterados diretamente por elementos externos, garantindo a segurança e consistência dos dados. No construtor, esses atributos são inicializados com os valores passados no momento da criação do objeto. Os atributos podem incluir:

- `$banco` (string)
- `$nomeTitular` (string)
- `$numeroAgencia` (string)
- `$numeroConta` (string)
- `$saldo` (float)

### Implementação de Métodos de Ação

Com os atributos definidos e inicializados pelo construtor, podemos criar os métodos para interagir com esses dados:

1. **Método `obterSaldo()` (Get Method)**
    
    - **Finalidade**: Este método é responsável por **retornar o valor atual do saldo** da conta. Sendo um método público, permite que outras partes do código consultem o saldo sem ter acesso direto ao atributo privado `$saldo`.
    - **Sintaxe e Funcionamento**: É declarado como `public function obterSaldo()`. Dentro do método, utiliza-se `$this->saldo` para acessar o atributo `$saldo` da instância atual da classe e o comando `return` para devolver seu valor. Além disso, pode-se concatenar uma mensagem para apresentar o saldo de forma mais amigável.
    
    ```
    public function obterSaldo() : float {
        return $this->saldo;
    }
    ```
    
    Ou com uma mensagem:
    
    ```
    public function obterSaldoComMensagem() : string {
        return "Seu saldo atual é " . $this->saldo . " reais.";
    }
    ```
    
    _Exemplo de uso:_ Chamar `conta->obterSaldoComMensagem()` retornaria "Seu saldo atual é 300 reais." se o saldo for 300.
    
2. **Método `depositar($valor)`**
    
    - **Finalidade**: Este método permite **adicionar um valor ao saldo** da conta. Ele recebe um parâmetro `$valor` que representa a quantia a ser depositada e, internamente, atualiza o atributo `$saldo`.
    - **Sintaxe e Funcionamento**: É declarado como `public function depositar(float $valor)`. Dentro do método, o valor recebido é somado ao saldo atual (`$this->saldo += $valor` ou `$this->saldo = $this->saldo + $valor`). O método pode, opcionalmente, retornar uma mensagem de confirmação do depósito.
    
    ```
    public function depositar(float $valor) : string {
        $this->saldo += $valor;
        return "Depósito de " . $valor . " realizado.";
    }
    ```
    
    _Exemplo de uso:_ `conta->depositar(300);` aumentaria o saldo em 300.
    
3. **Método `sacar($valor)`**
    
    - **Finalidade**: Este método permite **subtrair um valor do saldo** da conta. Similar ao método de depósito, ele recebe um parâmetro `$valor` que representa a quantia a ser sacada.
    - **Sintaxe e Funcionamento**: É declarado como `public function sacar(float $valor)`. A lógica interna subtrai o valor do saldo atual (`$this->saldo -= $valor` ou `$this->saldo = $this->saldo - $valor`). Também pode retornar uma mensagem de confirmação do saque.
    
    ```
    public function sacar(float $valor) : string {
        $this->saldo -= $valor;
        return "Saque de " . $valor . " realizado.";
    }
    ```
    
    _Exemplo de uso:_ `conta->sacar(150);` diminuiria o saldo em 150.
    

### Exemplo Completo de Interação

Ao combinar o construtor com esses métodos, a interação com o objeto `ContaBancaria` se torna clara e controlada:

```
// Definição da classe ContaBancaria (com atributos privados e os métodos acima)
class ContaBancaria {
    private string $banco;
    private string $nomeTitular;
    private string $numeroAgencia;
    private string $numeroConta;
    private float $saldo;

    public function __construct(string $banco, string $nomeTitular, string $numeroAgencia, string $numeroConta, float $saldoInicial) {
        $this->banco = $banco;
        $this->nomeTitular = $nomeTitular;
        $this->numeroAgencia = $numeroAgencia;
        $this->numeroConta = $numeroConta;
        $this->saldo = $saldoInicial;
    }

    public function obterSaldo() : float {
        return $this->saldo;
    }

    public function depositar(float $valor) : string {
        $this->saldo += $valor;
        return "Depósito de " . $valor . " realizado.";
    }

    public function sacar(float $valor) : string {
        if ($this->saldo >= $valor) { // Adiciona uma verificação para não sacar mais do que tem
            $this->saldo -= $valor;
            return "Saque de " . $valor . " realizado.";
        } else {
            return "Saldo insuficiente para saque de " . $valor . ". Saldo atual: " . $this->saldo;
        }
    }
}

// Criação de uma instância de ContaBancaria
$minhaConta = new ContaBancaria("Banco do Brasil", "Gustavo Fraga", "1234", "56789-0", 0.0);

echo "Saldo inicial: " . $minhaConta->obterSaldo() . " reais.\n"; // Saída: Saldo inicial: 0 reais.

echo $minhaConta->depositar(300) . "\n"; // Saída: Depósito de 300 realizado.
echo "Saldo após depósito: " . $minhaConta->obterSaldo() . " reais.\n"; // Saída: Saldo após depósito: 300 reais.

echo $minhaConta->sacar(150) . "\n"; // Saída: Saque de 150 realizado.
echo "Saldo após saque: " . $minhaConta->obterSaldo() . " reais.\n"; // Saída: Saldo após saque: 150 reais.

echo $minhaConta->sacar(200) . "\n"; // Saída: Saldo insuficiente para saque de 200. Saldo atual: 150.
```

Essa abordagem demonstra como a **Programação Orientada a Objetos** permite criar sistemas mais organizados, seguros e fáceis de manter, onde a lógica de negócio (como a manutenção do saldo) é encapsulada dentro da própria classe, sendo acessível apenas por meio de seus métodos públicos.

[[Formacao/Formacao em PHP\|Formacao em PHP]] / [[Formacao/PHP/Classes em PHP\|Classes em PHP]]
