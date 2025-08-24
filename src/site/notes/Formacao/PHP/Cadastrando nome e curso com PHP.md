---
{"dg-publish":true,"permalink":"/formacao/php/cadastrando-nome-e-curso-com-php/","metatags":{"description":"exemplos de códigos de desenvolvimento web"},"noteIcon":2,"updated":"2025-08-24T19:56:24.347-03:00"}
---

#PHP #POO

> [!abstract] Resumo da atividade
 Aplicação de **repetições** em PHP, recebendo o nome e o curso de um formulário, e armazenando esses dados em um array de objetos, reforçando os conceitos de **Programação Orientada a Objetos (POO)** e **sessões**.

A **Programação Orientada a Objetos (POO)** ajuda a organizar o código em classes, que servem como modelos para criar objetos, facilitando a manutenção e reutilização. Neste exercício, teremos uma classe `Aluno` para representar cada estudante. Os dados do formulário serão enviados via método POST e armazenados em uma variável de sessão (`$_SESSION`), que é um tipo de array. Para exibir os alunos cadastrados, utilizaremos uma estrutura de repetição `foreach`.

---

### Exercício: Cadastro de Alunos e Cursos com Repetições (POO em PHP)

**Objetivo:** Desenvolver uma aplicação PHP que permita cadastrar o nome e o curso de alunos através de um formulário HTML, armazenar esses dados em uma sessão como objetos de uma classe `Aluno`, e listar todos os alunos cadastrados usando um laço de repetição.

**Conceitos a serem aplicados:**

- **[[Formacao/PHP/Classes em PHP\|Classes em PHP]] e Objetos:** Criação da classe `Aluno` com atributos (`nome`, `curso`) e métodos (construtor `__construct`, getters).
- **Formulários HTML:** Coleta de dados do usuário.
- **Variáveis Superglobais (`$_POST`):** Para receber os dados do formulário.
- **Sessões (`$_SESSION`):** Para armazenar os objetos `Aluno` em um array persistente entre as requisições. A função `session_start()` é obrigatória no início de scripts que usam sessões.
- **Estruturas de [[Formacao/PHP/Repeticao com PHP\|Repeticao com PHP]] (`foreach`):** Para iterar sobre o array de alunos na sessão e exibi-los.
- **Validação básica:** Verificação se os campos obrigatórios foram preenchidos utilizando `isset()` e `!empty()`.

---

**Passos para Implementação:**

#### Passo 1: Criar a Classe `Aluno` (arquivo `Aluno.php`)

Esta classe definirá a estrutura dos objetos que representarão cada aluno.

```php
<?php
// Arquivo: Aluno.php

/**
 * Classe Aluno para representar um estudante com nome e curso.
 */
class Aluno {
    // Atributos (propriedades) da classe Aluno
    public $nome;       // Nome completo do aluno
    public $curso;      // Curso em que o aluno está matriculado

    /**
     * Construtor da classe Aluno.
     * É invocado automaticamente ao criar uma nova instância de Aluno.
     *
     * @param string $nome  O nome do aluno.
     * @param string $curso O nome do curso.
     */
    public function __construct(string $nome, string $curso) {
        $this->nome = $nome; // O $this-> refere-se à própria instância do objeto.
        $this->curso = $curso;
    }

    /**
     * Método para obter o nome do aluno (getter).
     * @return string O nome do aluno.
     */
    public function getNome(): string {
        return $this->nome;
    }

    /**
     * Método para obter o curso do aluno (getter).
     * @return string O curso do aluno.
     */
    public function getCurso(): string {
        return $this->curso;
    }
}
?>
```

#### Passo 2: Criar o Formulário HTML e Lógica de Processamento (arquivo `index.php`)

Este arquivo conterá o formulário, a lógica para processar os dados e adicionar novos alunos à sessão, e a parte de listagem com repetição.

```php
<?php
// Arquivo: index.php

// Inicia a sessão. É essencial chamar session_start() no início de scripts que usam sessões.
session_start();

// Inclui a definição da classe Aluno.
include 'Aluno.php';

// Inicializa a lista de alunos na sessão se ela ainda não existir.
// $_SESSION é um array superglobal que persiste dados entre requisições.
if (!isset($_SESSION['lista_alunos'])) {
    $_SESSION['lista_alunos'] = []; // Armazenará objetos Aluno.
}

$mensagem = ''; // Variável para exibir mensagens ao usuário.

// Verifica se o formulário foi submetido via método POST.
// $_SERVER['REQUEST_METHOD'] verifica o método da requisição.
if ($_SERVER['REQUEST_METHOD'] === 'POST') {
    // Recupera os dados do formulário, usando o operador de coalescência (??) para evitar "undefined index".
    $nome_aluno = $_POST['nome_aluno'] ?? '';
    $curso_aluno = $_POST['curso_aluno'] ?? '';

    // Validação básica dos campos.
    if (!empty($nome_aluno) && !empty($curso_aluno)) {
        // Cria uma nova instância da classe Aluno (um objeto Aluno).
        $novo_aluno = new Aluno($nome_aluno, $curso_aluno);

        // Adiciona o objeto Aluno ao array de alunos na sessão.
        $_SESSION['lista_alunos'][] = $novo_aluno;
        $mensagem = "<p style='color: green;'>Aluno cadastrado com sucesso!</p>";

        // Redireciona para a mesma página para evitar reenvio do formulário ao recarregar a página (Post/Redirect/Get pattern).
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
    <title>Cadastro de Alunos e Cursos</title>
    <style>
        body { font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif; margin: 20px; background-color: #f4f7f6; color: #333; }
        .container { max-width: 700px; margin: 30px auto; padding: 25px; background-color: #fff; border-radius: 10px; box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1); }
        h1, h2 { color: #007bff; text-align: center; margin-bottom: 20px; }
        form div { margin-bottom: 15px; }
        label { display: block; margin-bottom: 8px; font-weight: bold; color: #555; }
        input[type="text"] { width: 100%; padding: 10px; border: 1px solid #ced4da; border-radius: 5px; box-sizing: border-box; font-size: 1rem; }
        button { display: block; width: 100%; padding: 12px; background-color: #007bff; color: white; border: none; border-radius: 5px; cursor: pointer; font-size: 1.1rem; font-weight: bold; transition: background-color 0.3s ease; }
        button:hover { background-color: #0056b3; }
        .message { text-align: center; margin-bottom: 20px; font-weight: bold; }
        table { width: 100%; border-collapse: collapse; margin-top: 25px; }
        th, td { border: 1px solid #dee2e6; padding: 12px; text-align: left; }
        th { background-color: #e9ecef; color: #495057; }
        tr:nth-child(even) { background-color: #f8f9fa; }
        tr:hover { background-color: #e2e6ea; }
    </style>
</head>
<body>
    <div class="container">
        <h1>Cadastro de Alunos</h1>

        <?php if (!empty($mensagem)): ?>
            <div class="message"><?php echo $mensagem; // Exibe mensagens de sucesso ou erro ?></div>
        <?php endif; ?>

        <form action="index.php" method="POST">
            <div>
                <label for="nome_aluno">Nome do Aluno:</label>
                <input type="text" id="nome_aluno" name="nome_aluno" value="<?php echo htmlspecialchars($_POST['nome_aluno'] ?? ''); ?>" required>
            </div>
            <div>
                <label for="curso_aluno">Curso:</label>
                <input type="text" id="curso_aluno" name="curso_aluno" value="<?php echo htmlspecialchars($_POST['curso_aluno'] ?? ''); ?>" required>
            </div>
            <button type="submit">Cadastrar Aluno</button>
        </form>

        <h2>Alunos Cadastrados</h2>
        <?php if (!empty($_SESSION['lista_alunos'])): ?>
            <table>
                <thead>
                    <tr>
                        <th>Nome</th>
                        <th>Curso</th>
                    </tr>
                </thead>
                <tbody>
                    <?php
                    // ----- Seção de Repetição (Loop) -----
                    // O laço foreach é ideal para percorrer arrays.
                    // Para cada objeto Aluno no array 'lista_alunos' da sessão, criamos uma linha na tabela.
                    foreach ($_SESSION['lista_alunos'] as $aluno): // A cada iteração, $aluno recebe um objeto Aluno.
                    ?>
                        <tr>
                            <td><?php echo htmlspecialchars($aluno->getNome()); ?></td>
                            <td><?php echo htmlspecialchars($aluno->getCurso()); ?></td>
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

**Instruções para o Exercício:**

1. **Servidor Local:** Certifique-se de ter um servidor local (como XAMPP ou WAMP) com PHP configurado.
2. **Organização dos Arquivos:**
    - Crie um diretório para o projeto.
    - Salve o código da **Classe `Aluno`** como `Aluno.php` dentro desse diretório.
    - Salve o código do **Formulário HTML e Lógica de Processamento** como `index.php` no mesmo diretório.
3. **Acessar no Navegador:** Abra seu navegador e acesse `http://localhost/seu_diretorio_do_projeto/index.php`.
4. **Testar:** Preencha o formulário com nomes de alunos e seus respectivos cursos e observe os alunos serem listados na tabela abaixo.

---

**Explicação dos Conceitos Aplicados:**

- **Classe `Aluno`:** Define um **modelo** para criar objetos `Aluno`. Cada objeto `Aluno` terá suas próprias propriedades (`$nome`, `$curso`), que são inicializadas no método **construtor (`__construct`)** quando o objeto é criado. Os **métodos getters (`getNome()`, `getCurso()`)** permitem acessar de forma controlada os valores das propriedades do objeto.
- **Formulário HTML:** É a interface que o usuário utiliza para **inserir os dados** (`nome` e `curso`). O atributo `method="POST"` indica que os dados serão enviados de forma mais segura (não visíveis na URL).
- **Processamento PHP:**
    - `session_start();`: Inicia ou retoma uma sessão PHP, fundamental para armazenar dados temporariamente entre as requisições do usuário.
    - `include 'Aluno.php';`: Inclui a definição da classe `Aluno`, tornando-a disponível para uso no `index.php`.
    - `$_POST`: É uma variável superglobal que contém os dados enviados pelo formulário HTML através do método POST. Usamos `$_POST['nome_aluno']` e `$_POST['curso_aluno']` para recuperar os valores digitados nos campos do formulário.
    - `new Aluno(...)`: Cria uma **nova instância (objeto)** da classe `Aluno`, passando os dados do formulário para o construtor.
    - `$_SESSION['lista_alunos'][] = $novo_aluno;`: Adiciona o objeto `Aluno` recém-criado ao array `lista_alunos` armazenado na sessão. As sessões são ideais para **persistir dados de um usuário específico** durante sua navegação pelo site.
- **Repetições (`foreach`) para Listagem:**
    - `foreach ($_SESSION['lista_alunos'] as $aluno):`: Esta é a parte central do requisito de repetição. O laço `foreach` é uma estrutura de controle projetada para **iterar facilmente sobre elementos de arrays**. Ele percorre cada `Aluno` no array `lista_alunos` armazenado na sessão. A cada repetição, a variável `$aluno` recebe um objeto `Aluno` diferente do array.
    - `echo htmlspecialchars($aluno->getNome());`: Dentro do laço, usamos os métodos `getNome()` e `getCurso()` de cada objeto `$aluno` para exibir suas informações em uma linha da tabela HTML. `htmlspecialchars()` é usado para prevenir ataques de Cross-Site Scripting (XSS).

Este exercício demonstra a sinergia entre POO, formulários, sessões e estruturas de repetição, que são pilares no desenvolvimento web com PHP.

[[Programador Web\|Programador Web]] / [[Formacao/Formacao em PHP\|Formacao em PHP]]
