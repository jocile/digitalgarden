---
{"dg-publish":true,"permalink":"/formacao/php/cadastrando-alunos-com-php/","metatags":{"description":"exemplos de códigos de desenvolvimento web"},"noteIcon":2,"updated":"2025-08-24T20:18:21.069-03:00"}
---

#PHP #POO

> [!abstract] Resumo da atividade
> Criar um sistema de cadastro de alunos utilizando **Programação Orientada a Objetos (POO)** em PHP, com entrada de dados via formulário e armazenamento temporário em sessão, é um excelente exercício para solidificar conceitos.

A **POO** é uma metodologia que ajuda a organizar e reutilizar o código, facilitando a manutenção e a identificação de erros. Em vez de ter lógicas espalhadas em funções e condicionais, a POO as reúne em "pacotes" chamados **classes**. Uma **classe** serve como um modelo para criar **objetos**, que são instâncias dessa classe.

## Exercício: Sistema de Cadastro de Alunos com POO em PHP

**Objetivo:** Desenvolver uma aplicação PHP que permita cadastrar alunos através de um formulário HTML e listar os alunos registrados, aplicando os princípios de Programação Orientada a Objetos para representar um aluno e gerenciar seus dados em uma sessão.

**Conceitos a serem aplicados:**

- **[[Formacao/PHP/Classes em PHP\|Classes em PHP]]:** Definição e propósito.
- **Atributos (Propriedades):** Características de um objeto.
- **[[Formacao/PHP/Metodos com PHP\|Metodos com PHP]]:** Ações que um objeto pode realizar.
- **Construtor (`__construct`):** Método especial para inicializar um objeto no momento de sua criação.
- **Objetos:** Instâncias de uma classe.
- **Formulários HTML:** Coleta de dados do usuário.
- **Variáveis Superglobais (`$_POST`, `$_SESSION`):** Para receber dados do formulário e armazenar dados entre requisições.
- **Estruturas de [[Formacao/PHP/Repeticao com PHP\|Repeticao com PHP]] (`foreach`):** Para listar coleções de dados.

---

**Passos para Implementação:**

### Passo 1: Criar a Classe `Aluno` (arquivo `Aluno.php`)

Defina uma classe que represente um aluno, com seus atributos e um construtor para inicializá-los.

```php
<?php
// Arquivo: Aluno.php

class Aluno {
    // Atributos (propriedades) da classe Aluno
    public $nome;       // Nome do aluno
    public $email;      // Email do aluno
    public $matricula;  // Número de matrícula do aluno

    /**
     * Construtor da classe Aluno.
     * É executado automaticamente ao criar uma nova instância de Aluno.
     *
     * @param string $nome O nome completo do aluno.
     * @param string $email O endereço de e-mail do aluno.
     * @param string $matricula O número de matrícula do aluno.
     */
    public function __construct(string $nome, string $email, string $matricula) {
        $this->nome = $nome;
        $this->email = $email;
        $this->matricula = $matricula;
        // O $this-> refere-se à própria instância do objeto.
    }

    // Métodos para obter os valores dos atributos (getters - exemplo de como adicionar métodos)
    public function getNome(): string {
        return $this->nome;
    }

    public function getEmail(): string {
        return $this->email;
    }

    public function getMatricula(): string {
        return $this->matricula;
    }
}
?>
```

### Passo 2: Criar o Formulário HTML e Lógica de Processamento (arquivo `index.php`)

Neste arquivo, você terá:

1. Inclusão da classe `Aluno`.
2. Inicialização da sessão para armazenamento de dados.
3. Lógica para processar o formulário (`$_POST`).
4. Criação de um novo objeto `Aluno` e adição à sessão.
5. Exibição do formulário.
6. Listagem dos alunos já cadastrados.

```php
<?php
// Arquivo: index.php

// Inicia a sessão. Essencial para usar $_SESSION.
session_start();

// Inclui a definição da classe Aluno
include 'Aluno.php';

// Inicializa a lista de alunos na sessão, se ainda não existir
if (!isset($_SESSION['alunos'])) {
    $_SESSION['alunos'] = []; // Um array para armazenar objetos Aluno
}

$mensagem = '';

// Verifica se o formulário foi submetido via método POST.
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    // Recupera os dados do formulário
    $nome = $_POST['nome'] ?? '';
    $email = $_POST['email'] ?? '';
    $matricula = $_POST['matricula'] ?? '';

    // Validação básica. Em um sistema real, seria mais robusta.
    if (!empty($nome) && !empty($email) && !empty($matricula)) {
        // Cria um novo objeto Aluno
        $novoAluno = new Aluno($nome, $email, $matricula);

        // Adiciona o objeto Aluno à lista na sessão.
        $_SESSION['alunos'][] = $novoAluno;
        $mensagem = "<p style='color: green;'>Aluno cadastrado com sucesso!</p>";

        // Redireciona para evitar reenvio do formulário ao recarregar a página.
        header('Location: index.php');
        exit;
    } else {
        $mensagem = "<p style='color: red;'>Por favor, preencha todos os campos.</p>";
    }
}
?>

<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Cadastro de Alunos - POO PHP</title>
    <style>
        body { font-family: sans-serif; margin: 20px; }
        .container { max-width: 800px; margin: auto; padding: 20px; border: 1px solid #ccc; border-radius: 8px; }
        form div { margin-bottom: 10px; }
        label { display: block; margin-bottom: 5px; }
        input[type="text"], input[type="email"] { width: 100%; padding: 8px; box-sizing: border-box; }
        button { padding: 10px 15px; background-color: #007bff; color: white; border: none; border-radius: 5px; cursor: pointer; }
        button:hover { background-color: #0056b3; }
        table { width: 100%; border-collapse: collapse; margin-top: 20px; }
        th, td { border: 1px solid #ddd; padding: 8px; text-align: left; }
        th { background-color: #f2f2f2; }
    </style>
</head>
<body>
    <div class="container">
        <h1>Cadastro de Alunos</h1>
        <?php echo $mensagem; // Exibe mensagens de sucesso ou erro ?>

        <form action="index.php" method="POST">
            <div>
                <label for="nome">Nome:</label>
                <input type="text" id="nome" name="nome" value="<?php echo htmlspecialchars($_POST['nome'] ?? ''); ?>" required>
            </div>
            <div>
                <label for="email">Email:</label>
                <input type="email" id="email" name="email" value="<?php echo htmlspecialchars($_POST['email'] ?? ''); ?>" required>
            </div>
            <div>
                <label for="matricula">Matrícula:</label>
                <input type="text" id="matricula" name="matricula" value="<?php echo htmlspecialchars($_POST['matricula'] ?? ''); ?>" required>
            </div>
            <button type="submit">Cadastrar Aluno</button>
        </form>

        <h2>Alunos Cadastrados</h2>
        <?php if (!empty($_SESSION['alunos'])): ?>
            <table>
                <thead>
                    <tr>
                        <th>Nome</th>
                        <th>Email</th>
                        <th>Matrícula</th>
                    </tr>
                </thead>
                <tbody>
                    <?php
                    // Percorre a lista de alunos armazenada na sessão.
                    foreach ($_SESSION['alunos'] as $aluno):
                    ?>
                        <tr>
                            <td><?php echo htmlspecialchars($aluno->getNome()); ?></td>
                            <td><?php echo htmlspecialchars($aluno->getEmail()); ?></td>
                            <td><?php echo htmlspecialchars($aluno->getMatricula()); ?></td>
                        </tr>
                    <?php endforeach; ?>
                </tbody>
            </table>
        <?php else: ?>
            <p>Nenhum aluno cadastrado ainda.</p>
        <?php endif; ?>
    </div>
</body>
</html>
```

---

**Requisitos e Dicas Adicionais:**

- **Servidor Local:** Certifique-se de ter um servidor local (como XAMPP) para executar os arquivos PHP.
- **Nome dos Arquivos:** Salve o código da classe como `Aluno.php` e o formulário principal como `index.php` no mesmo diretório.
- **Limpeza da Sessão (Opcional):** Para resetar a lista de alunos, você pode adicionar um pequeno trecho de código temporário em `index.php` ou em um arquivo separado:

    ```php
    <?php
    session_start();
    session_destroy(); // Destrói todos os dados registrados em uma sessão
    header('Location: index.php');
    exit;
    ?>
    ```

    Salve este código como `reset.php` e acesse-o para limpar a lista.
- **Validação de Entrada:** A validação neste exercício é básica. Em um sistema de produção, você usaria validações mais completas, como verificação de formato de e-mail, unicidade de matrícula e tratamento de injeção de SQL. O Laravel, por exemplo, oferece funcionalidades de validação robustas através de "Requests".
- **Persistência de Dados:** Este exercício usa sessões para armazenamento temporário. Para persistência de dados (manter os dados mesmo após o navegador ser fechado ou o servidor reiniciado), seria necessário integrar um **banco de dados** (como MySQL) e utilizar técnicas de conexão e CRUD (Create, Retrieve, Update, Delete). A utilização de **PDO** em PHP é uma forma orientada a objetos de conectar-se a bancos de dados.

Este exercício proporciona uma base sólida para entender como os conceitos de POO se encaixam na construção de aplicações web funcionais.

[[Programador Web\|Programador Web]] / [[Formacao/Formacao em PHP\|Formacao em PHP]]
