---
{"dg-publish":true,"permalink":"/formacao/php/login-com-php-e-mysql/","metatags":{"description":"exemplos de códigos de desenvolvimento web"},"noteIcon":2,"updated":"2025-09-16T10:04:28.807-03:00"}
---

#PHP #exemplos

# Sistema de login com php

Um sistema de login em PHP e MySQL com sessions é uma implementação fundamental para gerenciar o acesso de usuários a aplicações web, garantindo que apenas usuários autenticados possam acessar áreas restritas e que suas informações sejam mantidas de forma temporária durante a navegação. Este sistema se baseia na interação de três componentes principais: PHP, MySQL e Sessions.

## Componentes Principais

1. **PHP (Hypertext Preprocessor)**: É a linguagem de script do lado do servidor utilizada para processar a lógica de autenticação, desde a validação dos dados do formulário até a interação com o banco de dados e o gerenciamento de sessões.
2. **MySQL**: É o sistema de gerenciamento de banco de dados (SGBD) onde as informações dos usuários, como nome de usuário (ou e-mail) e senhas criptografadas, são armazenadas de forma persistente.
3. **Sessions (Sessões PHP)**: São um mecanismo do PHP que permite armazenar dados temporários no servidor para um usuário específico. Esses dados ficam acessíveis em diferentes páginas enquanto o usuário navega no site, sem a necessidade de reautenticação a cada requisição ou de armazenar os dados no banco a cada interação.

## Estrutura do Banco de Dados (MySQL)

Para um sistema de login, é essencial ter uma tabela dedicada ao armazenamento dos dados dos usuários. Um exemplo comum é uma tabela chamada `aut_usuarios` ou `USUARIO`, que pode conter os seguintes campos:

- `id`: Um identificador único para cada usuário, geralmente um inteiro com `PRIMARY KEY` e `AUTO_INCREMENT`.
- `nome`: O nome completo do usuário (VARCHAR).
- `login` ou `email`: O nome de usuário ou endereço de e-mail que o usuário utilizará para fazer login. Este campo deve ser único.
- `senha` ou `password`: A senha do usuário, **sempre armazenada de forma criptografada** para segurança.
- `postar` ou `tipo`: Um campo opcional para definir níveis de permissão ou tipos de acesso (ex: administrador, usuário comum).

Ferramentas como o PHPMyAdmin, que geralmente acompanha servidores locais como o XAMPP, são utilizadas para gerenciar o banco de dados e suas tabelas de forma gráfica.

## Conexão com o Banco de Dados (PHP)

A conexão entre o PHP e o MySQL é um passo crucial. Geralmente, um arquivo separado (ex: `conexao.php`, `banco.php`, `config.php`) é criado para centralizar as credenciais e a lógica de conexão. As credenciais incluem:

- Endereço do servidor (ex: `localhost` ou `127.0.0.1`).
- Nome de usuário do banco de dados (ex: `root`).
- Senha do banco de dados (que pode ser vazia em ambientes de desenvolvimento local como o XAMPP, mas deve ser segura em produção).
- Nome da base de dados.

Existem diferentes formas de realizar essa conexão:

- **`mysql_connect()`**: Uma função mais antiga, que foi descontinuada no PHP 7.
- **`mysqli_connect()`**: Uma versão melhorada, recomendada para MySQL 4.1 ou superior.
- **PDO (PHP Data Objects)**: A forma mais recomendada, pois oferece uma interface consistente e mais segura para acessar diversos tipos de bancos de dados, além de suportar Prepared Statements, que ajudam a prevenir ataques de SQL Injection.

É fundamental implementar o tratamento de erros para a conexão, informando ao usuário caso haja algum problema.

Exemplo: arquivo `conexao.php`

```php
<?php
$servername = "localhost";
$username = "root";
$password = ""; // vazia para facilitar os testes

// Criar conexão
$conn = mysqli_connect($servername, $username, $password);

// Verifica conexão
if ($conn->connect_error) {
    die('Não foi possível conectar ao Banco de Dados. Erro detectado: ' . $conn->connect_error);
  }
?>
```


## Formulário de Login (HTML)

A interface de login é criada em uma página HTML (ex: `login.html`, `index.php`) e consiste em:

- Um elemento `<form>` com o atributo `action` apontando para o script PHP que processará o login e `method="post"` para enviar os dados de forma mais segura (oculta na URL).
- Campos de entrada (`<input>`) para o nome de usuário/e-mail (tipo `text`) e senha (tipo `password`).
- Um botão de submissão (`<input type="submit">`).
- O layout pode ser estilizado com frameworks CSS como Bootstrap para uma melhor experiência visual.

Exemplo:

```html
<html>
<body>
<form action="login.php" method="post">
	<div">
	  <label for="usuario">Usuário</label>
	  <input type="text" name="usuario" required />
	</div>
	<div>
	  <label for="senha">Senha</label>
	  <input type="password" name="senha" required />
	</div>
	<button type="submit">Login</button>
</form>
</body>
</html>
```

## Processamento do Login (Script PHP)

O script PHP responsável por processar os dados do formulário (ex: `controle.php`, `login.php`) executa as seguintes etapas:

1. **Início da Sessão**: A função `session_start()` deve ser a primeira instrução PHP em qualquer script que utilize sessões, antes de qualquer saída de conteúdo HTML, é usada para guardar variáveis entre as páginas, neste caso, o usuário logado e sua senha.
2. **Recuperação dos Dados**: Os valores inseridos nos campos do formulário são recuperados utilizando a superglobal `$_POST`, por exemplo, `$_POST['usuario']` e `$_POST['senha']`.
3. **Criptografia da Senha**: Antes de comparar a senha fornecida pelo usuário com a senha armazenada no banco de dados, é essencial criptografar a senha recebida do formulário. Historicamente, `md5()` foi usado, mas métodos mais seguros de hashing (como bcrypt) são a prática atual e frameworks como Laravel lidam com isso automaticamente.
4. **Consulta ao Banco de Dados**: Uma consulta SQL (`SELECT`) é executada no banco de dados para verificar se existe um registro de usuário que corresponda ao login e à senha fornecidos. Exemplo: `SELECT id, nome, login, senha, postar FROM aut_usuarios WHERE login = '$login'`.
5. **Verificação e Autenticação**:
    - Se a consulta retornar um ou mais registros, significa que as credenciais são válidas.
    - Os dados importantes do usuário (ID, nome, permissão) são então armazenados em variáveis de sessão, como `$_SESSION["id_usuario"]`, `$_SESSION["nome_usuario"]` e `$_SESSION["permissao"]`.
    - O usuário é redirecionado para uma página restrita ou para o painel administrativo (ex: `administracao.php`, `site.php`, `dashboard`) usando a função `header("Location: ...")` ou um script de redirecionamento.
6. **Tratamento de Login Inválido**: Caso as credenciais não correspondam a nenhum registro no banco, uma mensagem de erro (ex: "E-mail ou senha inválido") é exibida, e o usuário é redirecionado de volta para a página de login para tentar novamente. Nesse cenário, quaisquer sessões anteriores podem ser destruídas com `unset()`.

Exemplo:

```php
<?php
// Incluindo os dados do formulario
$usuario = trim($_POST["usuario"]);
$senha = md5(trim($_POST["senha"]));

// Aqui a conexão com o banco de dados e tabela usuários, exemplo a seguir

// Consulta os dados na tabela e confere se o usuário e senha estão corretos
$stmt = $conn->prepare("SELECT * FROM usuarios WHERE usuario = ? AND senha = ?");
$stmt->bind_param("ss", $usuario, $senha);
$stmt->execute();
$res = $stmt->get_result();

// Se o número de linhas for maior que zero, o usuário e senha estão corretos
if ($res->num_rows > 0) {
  $row = $res->fetch_object();
  // Registra o usuário na sessão para acessar páginas restritas
  $_SESSION["usuario"] = $usuario;
  $_SESSION["tipo"] = $row->tipo_usuario;
  // Redireciona para uma página restrita
  echo "<script>location.href='dashboard.php';</script>";
} else {
  echo "<script>alert('Usuário ou senha inválidos!');</script>";
  echo "<script>location.href='index.php';</script>";
}

$stmt->close();
```

## Proteção de Páginas Restritas

Para garantir que apenas usuários logados possam acessar certas áreas do site:

- Um script de verificação de sessão (ex: `verifica.php`) é incluído no início de todas as páginas que devem ser restritas.
- Este script verifica se as variáveis de sessão de login (e.g., `$_SESSION["id_usuario"]`) existem e estão definidas.
- Se as variáveis de sessão não existirem, o usuário é imediatamente redirecionado para a página de login.
- Em frameworks como Laravel, essa proteção é simplificada pelo uso de middlewares aplicados a grupos de rotas.

Exemplo:

```php
<?php
// Inicia sessões
session_start();

// Verifica se os campos estão vazios
if (empty($_SESSION)) {
  print "<script>location.href='index.php';</script>";
}
// Continua com o conteúdo restrito
```


## Funcionalidade de Logout

Um link ou botão de "Sair do Sistema" é providenciado para que o usuário possa encerrar sua sessão. Ao clicar, um script PHP (ex: `sair.php`, ou um método de logout em uma Controller) é executado. Este script:

1. Inicia a sessão com `session_start()`.
2. Remove as variáveis de sessão específicas (`unset($_SESSION['usuario'])`) ou destrói a sessão completa (`session_destroy()`).
3. Redireciona o usuário de volta para a página de login.

Exemplo:

```php
<?php
session_start();
// remove todas as variáveis de sessão
session_unset();
// desativa a sessão
session_destroy();
// redireciona para a página inicial
header("Location: index.php");
exit;
```

## Boas Práticas e Considerações Adicionais

- **Segurança**: Além da criptografia de senhas, é fundamental proteger contra ataques de SQL Injection, utilizando Prepared Statements (com PDO) ou filtrando e tratando todas as entradas de dados. A proteção CSRF também é importante em formulários.
- **Experiência do Usuário (UX)**: Em caso de erros de validação no formulário, manter os valores que o usuário já preencheu (usando `old()` no Laravel ou lógica similar em PHP puro) é uma boa prática.
- **Organização do Código**: Separar a lógica em arquivos distintos (conexão, validação, processamento, views, helpers) e seguir padrões de arquitetura como MVC (Model-View-Controller) melhora a manutenção e a legibilidade do código.
- **Ambiente de Desenvolvimento**: Para construir e testar um sistema de login, é necessário um servidor local (XAMPP, WAMP, Laragon) com PHP e MySQL, e um editor de código (Visual Studio Code, Notepad++).
- **Frameworks**: Frameworks como Laravel simplificam e padronizam muitas dessas operações, oferecendo recursos prontos para autenticação, validação, gerenciamento de banco de dados (Models, Migrations), e rotas controladas por Controllers e Middlewares.

Este sistema básico oferece a estrutura para autenticação de usuários, permitindo a construção de aplicações web mais complexas e seguras.

Um sistema de login com PHP e MySQL utilizando sessões envolve a criação de vários arquivos para gerenciar a conexão com o banco de dados, o formulário de login, o processamento da autenticação, a verificação de sessão e o logout. As senhas são criptografadas em MD5 para aumentar o nível de segurança.

## Exemplo completo

Aqui está um exemplo de implementação:

### 1. Conexão com o Banco de Dados (`conexao.php`)

Este arquivo é responsável por estabelecer a conexão com o banco de dados MySQL e será incluído em todas as páginas que precisarem interagir com ele.

```php
<?php
$servername = "localhost";
$username = "root";
$password = ""; // aqui vazio para teste

// Criar conexão
$conn = mysqli_connect($servername, $username, $password);

// Verificar conexão
if ($conn->connect_error) {
    die('Não foi possível conectar ao Banco de Dados. Erro detectado: ' . $conn->connect_error);
  }
```

>[!warning] **Observação**: A função `mysql_connect()` é uma função mais antiga e foi descontinuada no PHP 7. Em implementações modernas, `mysqli_connect()` ou PDO (PHP Data Objects) são as alternativas recomendadas para uma conexão segura e eficaz.

### 2. Criando o banco de dados (`criarBanco.php`)

```php
<?php
// Criando o banco de dados se não existir
function criarBanco($conexao, $nomeBanco) {
  $banco = "CREATE DATABASE IF NOT EXISTS `$nomeBanco`";
  if ($conexao->query($banco)) {
    echo "Banco de dados '$nomeBanco' já criado com sucesso.<br>";
  } else {
    echo "Erro ao criar banco de dados: " . $conexao->error;
  }
}
```

### 3. Criando a tabela (`criarTabela.php`)

```php
<?php
// Criando a tabela se não existir
function criarTabela($conexao, $nomeBanco, $nomeTabela) {
  $tabela_usuario = "CREATE TABLE IF NOT EXISTS $nomeTabela (
    id INT(10) AUTO_INCREMENT PRIMARY KEY,
    usuario VARCHAR (50) NOT NULL,
    senha VARCHAR(50) NOT NULL,
    tipo_usuario INT(1) NOT NULL
    )";
  $conexao->select_db($nomeBanco);
  if ($conexao->query($tabela_usuario)) {
    echo "Tabela '$nomeTabela' já criada com sucesso.<br>";
  } else {
    echo "Erro ao criar a tabela: " . $conexao->error;
  }
}
```

### 4. Inserindo o usuário administrador

Primeiro é necessário um usuário administrador que pode cadastrar outros usuários.

Arquivo `cadastroForm.php`:

```php
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <title>Cadastro de usuários</title>
</head>
<body>
  <form action="cadastro.php" method="post">
	<div>
	  <label for="usuario">Login</label>
	  <input type="text" name="usuario" required />
	</div>
	<div>
	  <label for="senha">Senha</label>
	  <input type="password" name="senha" required />
	</div>
	<div>
	  <label for="tipo_usuario">Tipo de usuário</label>
	  <select name="tipo_usuario" required>
		<option value="">Selecione</option>
		<option value="1">Administrador</option>
		<option value="2">Usuário Comum</option>
	  </select>
	</div>
	<div>
	  <button type="submit" name="cadastrar" value="cadastrar">Cadastrar</button>
	</div>
  </form>

</body>
</html>
```

O arquivo `cadastro.php` que inclui os dados no Banco de Dados:

```php
<?php
// conectando ao banco de dados
require("conexao.php");

// Criando o banco de dados se não existir
require("criarBanco.php");
criarBanco($conn, "testelogin");

// Criando a tabela se não existir
require("criarTabela.php");
criarTabela($conn, "testelogin", "usuarios");

// Incluindo os dados do formulario
$usuario = trim($_POST["usuario"]);
$senha = md5(trim($_POST["senha"]));
$tipo_usuario = $_POST["tipo_usuario"];

// Inserção dos dados na tabela
$inserir = "INSERT INTO usuarios (usuario, senha, tipo_usuario) VALUES ('$usuario', '$senha', '$tipo_usuario')";
if (mysqli_query($conn, $inserir)) {
  //Redireciona para a página de sucesso
  echo "<script>alert('Usuário cadastrado com sucesso!');</script>";
  print "<script>setTimeout(function(){ location.href='index.php'; }, 9000);</script>";
  } else {
  echo "<script>alert('Erro ao cadastrar usuário!');</script>";
  print "<script>setTimeout(function(){ location.href='cadastroForm.php'; }, 9000);</script>";
  }
mysqli_close($conn);
```

Acesse o formulário criado e cadastre o usuário `admin` e senha `1234` para o login.

### 5. Formulário de Login (`index.php`)

Esta é a página HTML que apresenta o formulário onde o usuário digitará o login e a senha.

```php
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <title>Login</title>
</head>
<body>
    <form action="login.php" method="post">
    <div>
      <label for="usuario">Usuário</label>
      <input type="text" name="usuario" required />
    </div>
    <div>
      <label for="senha">Senha</label>
      <input type="password" name="senha" required />
    </div>
    <button type="submit">Login</button>
  </form>
</body>
</html>
```

### 6. Script de Processamento do Login (`login.php`)

Esta página recebe os dados do formulário (`index.php`), verifica as credenciais no banco de dados e gerencia as sessões.

```php
<?php
// Inicia sessões para guardar o login entre as páginas
session_start();

// Verifica se os campos estão vazios
if (empty($_POST) or (empty($_POST["usuario"]) or empty($_POST["senha"]))) {
  print "<script>location.href='index.php';</script>";
}

// Incluindo os dados do formulario
$usuario = $_POST["usuario"];
$senha = md5($_POST["senha"]);

// conectando ao banco de dados
require("conexao.php"); // inclui aqui o arquivo

// Consulta os dados na tabela e confere se o usuário e senha estão corretos
$conn->select_db("teste-login");
$stmt = $conn->prepare("SELECT * FROM usuarios WHERE usuario = ? AND senha = ?");
$stmt->bind_param("ss", $usuario, $senha);
$stmt->execute();
$res = $stmt->get_result();

// Se o número de linhas for maior que zero, o usuário e senha estão corretos
if ($res->num_rows > 0) {
  $row = $res->fetch_object();
  // Registra o usuário na sessão para acessar páginas restritas
  $_SESSION["usuario"] = $usuario;
  $_SESSION["tipo"] = $row->tipo_usuario;
  // Redireciona para uma página restrita
  echo "<script>location.href='dashboard.php';</script>";
} else {
  echo "<script>alert('Usuário ou senha inválidos!');</script>";
  echo "<script>location.href='index.php';</script>";
}

$stmt->close();
```

**Observações Importantes**:

- A função `session_start()` deve ser a primeira instrução PHP em qualquer script que utiliza sessões, antes de qualquer saída de conteúdo HTML.
- A senha fornecida pelo usuário (`$_POST["senha"]`) é criptografada com `md5()` antes de ser comparada com a senha armazenada no banco de dados. A função `strcmp()` é usada para comparar as duas senhas já criptografadas. `strcmp` retorna zero se as strings forem iguais, por isso o uso de `!` (operador NOT).
- Em caso de sucesso na autenticação, os dados do usuário (id, nome, permissão) são armazenados na superglobal `$_SESSION` e o usuário é redirecionado para a página `index.php`.
- Se o login ou a senha estiverem incorretos, mensagens de erro são exibidas e o processamento é interrompido.

### 7. Verificação de Sessão (`verifica.php`)

Este script é incluído no início de todas as páginas que você deseja restringir, garantindo que apenas usuários autenticados possam acessá-las.

```php
<?php
// Inicia sessões
session_start(); //

// Verifica se existe os dados da sessão de login
if (!isset($_SESSION["usuario"]) || !isset($_SESSION["tipo"])) { //
  // Usuário não logado! Redireciona para a página de login
  echo "<script>alert('Usuário não logado!');</script>";
  print "<script>setTimeout(function(){ location.href='index.php'; }, 9000);</script>";
  exit;
}
```

### 8. Página restrita (`dashboard.php`)

O arquivo `dashboard.php` apresenta um menu administrativo restrito:

```php
<?php require("verifica.php"); ?>
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Dashboard</title>
  <!-- BootStrap CSS -->
  <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/css/bootstrap.min.css" rel="stylesheet">
  <!-- BootStrap JavaScript -->
  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.3.3/dist/js/bootstrap.bundle.min.js"></script>
</head>

<body>
  <nav>
    <navbar class="navbar navbar-expand-lg navbar-light bg-light">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">
          <?php
          print "Dashboard- " . $_SESSION["usuario"];
          ?>
        </a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav">
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="#">Home</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Profile</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="#">Settings</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="cadastroForm.php">Cadastrar</a>
            </li>
            <li class="nav-item">
              <a class="nav-link" href="logout.php">Logout</a>
          </ul>
        </div>
      </div>
    </navbar>
  </nav>
</body>

</html>
```

### 9. Script de Logout (`logout.php`)

Esta página permite que o usuário encerre sua sessão, destruindo todas as variáveis de sessão e redirecionando-o para a página de login.

```php
<?php
// Inicia sessões, para assim poder destruí-las
session_start();
session_destroy(); // Destrói todas as variáveis de sessão de uma única vez.
header("Location: index.php");
?>
```

### Restringindo o acesso (Página Restrita - `cadastroForm.php`)

A página `cadastroForm.php` é um exemplo de uma página que exigiria autenticação. Nela, você incluiria o arquivo `verifica.php` para que somente usuários administradores pudessem cadastrar novos usuários.

```php
<?php require("verifica.php"); ?> // incluir este trecho para restringir o acesso
<!DOCTYPE html> // Continua com o conteúdo restrito
<html lang="pt-BR">
<head>
  <title>Cadastro de usuários</title>

// ... Restante do conteúdo
```

Este é um sistema de login básico que demonstra a lógica de autenticação usando PHP, MySQL e sessões. É fundamental para gerenciar o acesso de usuários e proteger áreas restritas de uma aplicação web.

## Referências

- [PHP-login em exercícios · GitHub](https://github.com/jocile/php-exercicios/tree/main/login)
- [Sistema de Login com PHP e MySQL - YouTube](https://www.youtube.com/watch?v=Ln7lqyWJPUE)
- [Aprenda a criar controle de acesso com PHP e MySQL - DevMedia - DevMedia](https://www.devmedia.com.br/criando-controle-de-acesso-com-php-e-mysql/28123)
- [How To Create a Login Form](https://www.w3schools.com/howto/howto_css_login_form.asp)
- [How To Create a Password Validation Form](https://www.w3schools.com/howto/howto_js_password_validation.asp)
- [How To Make a Modal Box With CSS and JavaScript](https://www.w3schools.com/howto/howto_css_modals.asp)
- [Cards · Bootstrap v5.3](https://getbootstrap.com/docs/5.3/components/card/)
