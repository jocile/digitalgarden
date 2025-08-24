---
{"dg-publish":true,"permalink":"/formacao/php/classes-em-php/","metatags":{"description":"exemplos de códigos de desenvolvimento web"},"noteIcon":2,"updated":"2025-08-24T17:46:00.698-03:00"}
---

#PHP #POO

>[!abstract] Resumo
>O trecho explora a criação de **classes e objetos** em PHP, utilizando o exemplo de uma `ContaBancaria` para ilustrar conceitos fundamentais. Uma **classe** é apresentada como a **representação de um objeto do mundo real** dentro da aplicação, enquanto um **objeto** é uma **instância** dessa classe, criada com a palavra-chave `new`. A discussão avança para as **propriedades (ou atributos)** de uma classe, que descrevem suas características, como `banco` ou `saldo`, e a importância dos **modificadores de acesso** (`public`, `private`, `protected`) para controlar a visibilidade e a segurança desses atributos. O autor enfatiza que propriedades como o `saldo` devem ser `private` para evitar modificações diretas e garantir a integridade dos dados, preparando o terreno para a introdução de **métodos**, que representam as ações que um objeto pode realizar.

# Classes em PHP

## Definições

Em PHP, as **classes** são a **espinha dorsal da Programação Orientada a Objetos (POO)** e servem como **modelos ou projetos para criar objetos**. Pense em uma classe como a planta de um prédio: ela define como o prédio será (tamanho dos cômodos, número de andares, etc.), mas não é o prédio em si. O prédio real é uma **instância** dessa planta, ou seja, um **objeto**.

### O que é uma Classe?

Uma classe é, portanto, a **representação de um objeto do mundo real** dentro da sua aplicação. Ela agrupa **dados (atributos/propriedades)** e **comportamentos (métodos/funções)** que descrevem e manipulam esses dados.

**Exemplo Didático:** No nosso exemplo da `ContaBancaria`, a **classe `ContaBancaria`** seria a planta que define o que toda conta bancária deve ter e o que ela pode fazer.

### Atributos (Propriedades) e Métodos (Funções)

Uma classe em PHP é composta por:

- **Atributos (ou Propriedades)**: São as **variáveis** que pertencem à classe e que definem as **características ou estados** do objeto. No exemplo da `ContaBancaria`, atributos poderiam ser `$banco`, `$nomeTitular`, `$numeroAgencia`, `$numeroConta` e `$saldo`.
- **Métodos (ou Funções)**: São as **ações ou comportamentos** que os objetos criados a partir da classe podem realizar. Eles contêm a lógica para manipular os atributos. Para a `ContaBancaria`, métodos seriam `depositar()`, `sacar()`, `obterSaldo()`.

### Criando um Objeto (Instância da Classe)

Para usar uma classe, você precisa **criar um objeto** a partir dela, o que é chamado de **instanciação**. Isso é feito usando a palavra-chave `new`.

```
// Instanciação: criando um objeto 'minhaConta' da classe 'ContaBancaria'
$minhaConta = new ContaBancaria("Banco X", "João", "1234", "5678-9", 1000.00);
```

Cada objeto (`$minhaConta`) terá seus próprios valores para os atributos (saldo, titular, etc.) e poderá executar os métodos definidos na classe.

### Sintaxe Básica para Definir uma Classe

A declaração de uma classe em PHP começa com a palavra-chave `class`, seguida do nome da classe e um bloco de código entre chaves `{}`:

```
<?php
class ContaBancaria {
    // Atributos (Propriedades) da classe
    private string $banco;
    private string $nomeTitular;
    private string $numeroAgencia;
    private string $numeroConta;
    private float $saldo;

    // Métodos (Funções) da classe
    // ... (construtor, depositar, sacar, obterSaldo)
}
?>
```

### Modificadores de Acesso (Visibilidade)

Todos os atributos e métodos de uma classe devem ter um modificador de acesso (ou visibilidade):

- `public`: O atributo ou método pode ser **acessado de qualquer lugar**, tanto de dentro quanto de fora da classe. É a visibilidade padrão se nenhuma for especificada.
- `private`: O acesso é **restrito apenas de dentro da própria classe**. Isso é crucial para o **encapsulamento**, protegendo os dados de modificações externas diretas.
- `protected`: O acesso é permitido de dentro da classe e também de **classes que herdam** dela (subclasses).

### A Palavra-Chave `$this`

Dentro de um método de uma classe, a palavra-chave **`$this` refere-se ao próprio objeto atual**. É usada para acessar os atributos e outros métodos desse objeto. Exemplo: `$this->saldo` acessaria o atributo `saldo` do objeto atual.

### O Método Construtor (`__construct()`)

O construtor é um **método especial** (`__construct`) que é **automaticamente executado toda vez que uma nova instância (objeto) da classe é criada**. Sua principal finalidade é **inicializar os atributos** do objeto com valores passados no momento da criação.

```
class ContaBancaria {
    private string $banco;
    // ... outros atributos

    public function __construct(string $banco, string $nomeTitular, string $numeroAgencia, string $numeroConta, float $saldoInicial) {
        $this->banco = $banco;
        $this->nomeTitular = $nomeTitular;
        $this->numeroAgencia = $numeroAgencia;
        $this->numeroConta = $numeroConta;
        $this->saldo = $saldoInicial;
    }
    // ... outros métodos
}
```

### Encapsulamento, Getters e Setters

O **encapsulamento** é um pilar da POO que visa **proteger os atributos de uma classe**, impedindo o acesso direto de fora dela. Em vez disso, a manipulação dos atributos é feita por meio de **métodos públicos** específicos:

- **Getters** (métodos `get...()`): Métodos públicos que **retornam o valor** de um atributo privado. Ex: `public function getSaldo(): float { return $this->saldo; }`
- **Setters** (métodos `set...()`): Métodos públicos que **definem ou modificam o valor** de um atributo privado. Ex: `public function setSaldo(float $novoSaldo) { $this->saldo = $novoSaldo; }`

### Herança (`extends`)

A **herança** permite que uma classe (chamada de **subclasse** ou classe filha) **herde atributos e métodos de outra classe** (chamada de **superclasse** ou classe pai). Isso promove a **reutilização de código** e a organização de uma hierarquia de classes. Usa-se a palavra-chave `extends`.

```
class ContaPoupanca extends ContaBancaria {
    // ContaPoupanca herda todos os atributos e métodos públicos/protegidos de ContaBancaria
    // e pode ter seus próprios atributos e métodos adicionais.
}
```

### Interfaces (`implements`)

Uma **interface** define um **contrato**, especificando quais métodos uma classe deve implementar, mas **sem fornecer a implementação** desses métodos. Uma classe usa a palavra-chave `implements` para indicar que adere a uma ou mais interfaces.

```
interface OperacoesFinanceiras {
    public function depositar(float $valor);
    public function sacar(float $valor);
}

class MinhaConta implements OperacoesFinanceiras {
    // Deve implementar os métodos depositar() e sacar()
}
```

### Métodos e Atributos Estáticos

**Membros estáticos** (atributos ou métodos) pertencem à **classe em si**, e não a uma instância específica (objeto) dela. Eles são declarados com a palavra-chave `static` e são acessados diretamente pela classe, sem a necessidade de criar um objeto, usando o operador `::`. Exemplo: `ContaBancaria::getNumeroTotalDeContasCriadas()` (se `getNumeroTotalDeContasCriadas` fosse um método estático).

As classes são um conceito fundamental para construir aplicações PHP mais robustas, organizadas e fáceis de manter, sendo a base para a implementação de padrões de projeto e frameworks.

## Exemplo

Continuando nosso exemplo de forma didática, vamos aprofundar nas classes em PHP usando a `ContaBancaria` como referência.

### A Classe `ContaBancaria`: O Projeto da sua Conta Real

Uma **classe é a representação de um objeto do mundo real na sua aplicação**. No nosso caso, a classe `ContaBancaria` é o "projeto" ou "planta" que define como todas as contas bancárias no seu sistema devem ser e o que elas podem fazer. Assim como uma planta de um prédio não é o prédio em si, mas as instruções para construí-lo, a classe `ContaBancaria` não é uma conta real, mas o modelo para criar várias contas.

### Componentes de uma Classe: Atributos e Métodos

Uma classe é composta por:

- **Atributos (ou Propriedades)**: São as **características ou dados que o objeto possui**. Para nossa `ContaBancaria`, atributos poderiam ser: `$banco`, `$nomeTitular`, `$numeroAgencia`, `$numeroConta` e `$saldo`. Estes atributos são declarados como variáveis dentro da classe.
- **Métodos (ou Funções)**: São as **ações ou comportamentos que o objeto pode realizar**. Para a `ContaBancaria`, exemplos de métodos seriam: `depositar()`, `sacar()`, `obterSaldo()`.

### Modificadores de Acesso (Visibilidade): Protegendo seus Dados

Todos os atributos e métodos de uma classe devem ter um modificador de acesso (ou visibilidade). Estes definem onde o atributo ou método pode ser acessado:

- **`public`**: O membro é **acessível de qualquer lugar**, tanto de dentro quanto de fora da classe. Por exemplo, um método para exibir o saldo pode ser público.
- **`private`**: O acesso é **restrito apenas de dentro da própria classe**. Isso é fundamental para o **encapsulamento**, que protege os dados de modificações externas diretas. Imagine o saldo de uma conta: ele não deve ser alterado diretamente por qualquer parte do código (`$conta->saldo = 0;`), mas apenas através de métodos específicos como `depositar()` ou `sacar()`. Se tentar acessar uma propriedade privada de fora da classe, você receberá um erro.
- **`protected`**: O acesso é permitido de dentro da classe e também de **classes que herdam dela** (subclasses). O comportamento é semelhante ao `private`, mas com essa exceção para herança.

### Criando um Objeto (Instanciação): Dando Vida à Sua Conta

Para usar a planta da `ContaBancaria`, você precisa construir um prédio real, ou seja, **criar um objeto (uma instância) da classe**. Isso é feito com a palavra-chave `new`.

```
<?php
// Exemplo de criação de uma instância da classe ContaBancaria
$minhaConta = new ContaBancaria("Banco do Brasil", "Gustavo", "1234", "5678-9", 300.00);
?>
```

Cada objeto criado terá seus próprios valores para os atributos e poderá executar os métodos definidos na classe. A variável `$minhaConta` agora contém um objeto do tipo `ContaBancaria`.

### O Construtor `__construct()`: Iniciando sua Conta

O método **`__construct()`** é um **método mágico especial que é executado automaticamente toda vez que um novo objeto da classe é criado**. Sua função principal é **inicializar os atributos do objeto** com os valores passados no momento da criação.

```
<?php
class ContaBancaria {
    private string $banco;
    private string $nomeTitular;
    private string $numeroAgencia;
    private string $numeroConta;
    private float $saldo;

    public function __construct(string $banco, string $nomeTitular, string $numeroAgencia, string $numeroConta, float $saldoInicial) {
        // A palavra-chave $this refere-se ao objeto atual.
        // Usamos $this->atributo para acessar as propriedades do objeto.
        $this->banco = $banco;
        $this->nomeTitular = $nomeTitular;
        $this->numeroAgencia = $numeroAgencia;
        $this->numeroConta = $numeroConta;
        $this->saldo = $saldoInicial; // Inicializa o saldo.
    }
    // ... outros métodos
}
?>
```

Ao criar o objeto `$minhaConta` com `new ContaBancaria(...)`, o construtor é chamado, e os valores `"Banco do Brasil"`, `"Gustavo"`, etc., são usados para definir o estado inicial dos atributos do objeto.

### O `$this` Keyword: Referenciando o Objeto Atual

Dentro de um método da classe, a palavra-chave **`$this` é usada para referenciar o próprio objeto atual**. Você a utiliza para acessar os atributos (`$this->saldo`) ou outros métodos (`$this->obterSaldo()`) desse objeto.

### Métodos: As Ações da Sua Conta (Getters e Setters)

Os métodos permitem que seu objeto `ContaBancaria` realize ações, como depositar ou sacar. Eles são a forma controlada de interagir com os atributos (especialmente os privados).

- **Getters (métodos de leitura)**: São métodos públicos que **retornam o valor de um atributo privado**. Para o nosso exemplo, se `$saldo` é privado, precisamos de um método público para lê-lo.
    
    ```
    <?php
    class ContaBancaria {
        // ... atributos e construtor
        public function obterSaldo(): float { // Retorna o saldo.
            return $this->saldo; // Acessa o atributo privado saldo usando $this.
        }
        // ...
    }
    ?>
    ```
    
    Isso permite que você veja o saldo (`$minhaConta->obterSaldo()`) sem acessá-lo diretamente, mantendo o encapsulamento.
    
- **Setters (métodos de escrita/modificação)**: São métodos públicos que **definem ou modificam o valor de um atributo privado**. Os métodos `depositar()` e `sacar()` são exemplos de setters, pois eles alteram o `$saldo` de forma controlada.
    
    ```
    <?php
    class ContaBancaria {
        // ... atributos, construtor e obterSaldo()
    
        public function depositar(float $valor): string { // Recebe um valor e o soma ao saldo.
            $this->saldo += $valor; // Modifica o saldo usando $this.
            return "Depósito de {$valor} realizado. Seu saldo atual é {$this->saldo}."; // Retorna uma mensagem.
        }
    
        public function sacar(float $valor): string { // Recebe um valor e o subtrai do saldo.
            if ($this->saldo >= $valor) {
                $this->saldo -= $valor; // Modifica o saldo usando $this.
                return "Saque de {$valor} realizado. Seu saldo atual é {$this->saldo}."; // Retorna uma mensagem.
            }
            return "Saldo insuficiente para o saque de {$valor}. Seu saldo atual é {$this->saldo}.";
        }
    }
    ?>
    ```
    
    Ao usar `$minhaConta->depositar(500);` ou `$minhaConta->sacar(150);`, você interage com o saldo de forma segura, garantindo que a lógica de negócio (como verificar se há saldo suficiente para saque) seja aplicada.
    

### Declaração de Tipos: Melhorando a Robustez

A partir do PHP 7.4, é possível declarar explicitamente os tipos de dados para atributos, parâmetros de métodos e retornos de métodos. Isso torna o código mais legível e robusto, pois o PHP fará a verificação de tipos automaticamente.

```
<?php
class ContaBancaria {
    private string $banco; // Declarando o tipo string para o atributo.
    private string $nomeTitular;
    private string $numeroAgencia;
    private string $numeroConta;
    private float $saldo; // Declarando o tipo float para o saldo.

    public function __construct(string $banco, string $nomeTitular, string $numeroAgencia, string $numeroConta, float $saldoInicial) { // Tipos para parâmetros.
        $this->banco = $banco;
        $this->nomeTitular = $nomeTitular;
        $this->numeroAgencia = $numeroAgencia;
        $this->numeroConta = $numeroConta;
        $this->saldo = $saldoInicial;
    }

    public function obterSaldo(): float { // Declarando o tipo de retorno float.
        return $this->saldo;
    }
    // ... outros métodos com tipos declarados
}
?>
```

### Herança (`extends`): Reutilizando e Estendendo Funcionalidades

A **herança** permite que uma nova classe (subclasse) **herde atributos e métodos de uma classe existente** (superclasse). Isso promove a reutilização de código e a criação de hierarquias de classes.

Por exemplo, poderíamos criar uma `ContaPoupanca` que **estende** `ContaBancaria`:

```
<?php
class ContaPoupanca extends ContaBancaria { // ContaPoupanca herda tudo de ContaBancaria.
    // ... pode ter atributos e métodos próprios, como data de aniversário para rendimento.
}
?>
```

A `ContaPoupanca` teria automaticamente os atributos e métodos de `ContaBancaria` (banco, saldo, depositar, sacar) e poderia adicionar ou modificar funcionalidades.

### Interfaces (`implements`): Definindo Contratos

Uma **interface** define um **contrato** para as classes, especificando quais métodos elas devem ter, mas **sem fornecer a implementação** desses métodos. Uma classe usa a palavra-chave `implements` para indicar que ela adere a uma ou mais interfaces.

Por exemplo, poderíamos ter uma interface `OperacoesFinanceiras`:

```
<?php
interface OperacoesFinanceiras {
    public function depositar(float $valor);
    public function sacar(float $valor);
    public function transferir(float $valor, ContaBancaria $destino);
}

class ContaCorrente implements OperacoesFinanceiras { // Deve implementar todos os métodos da interface.
    // ... Implementação dos métodos aqui
}
?>
```

Isso garante que qualquer classe que implemente `OperacoesFinanceiras` terá esses métodos, criando um padrão de comportamento.

### Membros Estáticos (`static`): Acesso Direto pela Classe

**Atributos e métodos estáticos** pertencem à **classe em si**, e não a uma instância específica (objeto). Eles são declarados com a palavra-chave `static` e são acessados diretamente pela classe usando o operador de resolução de escopo `::`.

```
<?php
class ContaBancaria {
    // ... atributos e métodos existentes
    private static int $totalContasCriadas = 0; // Atributo estático.

    public function __construct(...) {
        // ...
        self::$totalContasCriadas++; // Incrementa o contador de contas.
    }

    public static function obterTotalContas(): int { // Método estático.
        return self::$totalContasCriadas; // Acessa atributo estático usando self::.
    }
}

// Para acessar:
echo ContaBancaria::obterTotalContas(); // Não precisa de um objeto.
?>
```

Os membros estáticos são úteis para funcionalidades que não dependem do estado de um objeto específico, como um contador de todas as contas criadas ou um método utilitário.

Com este entendimento, você pode construir classes PHP mais complexas e bem estruturadas, aproveitando os princípios da Programação Orientada a Objetos para organizar seu código e torná-lo mais modular e fácil de manter.

[[Formacao/Formacao em PHP\|Formacao em PHP]] / [[Formacao/PHP/POO com PHP\|POO com PHP]] / [[Formacao/PHP/Metodos com PHP\|Metodos com PHP]]
