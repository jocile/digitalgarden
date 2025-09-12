---
{"dg-publish":true,"permalink":"/formacao/php/login-com-php-e-mysql/","metatags":{"description":"exemplos de códigos de desenvolvimento web"},"noteIcon":2,"updated":"2025-09-12T07:24:52.129-03:00"}
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

A conexão entre o PHP e o MySQL é um passo crucial. Geralmente, um arquivo separado (ex: `comum.php`, `banco.php`, `config.php`) é criado para centralizar as credenciais e a lógica de conexão. As credenciais incluem:

- Endereço do servidor (ex: `localhost` ou `127.0.0.1`).
- Nome de usuário do banco de dados (ex: `root`).
- Senha do banco de dados (que pode ser vazia em ambientes de desenvolvimento local como o XAMPP, mas deve ser segura em produção).
- Nome da base de dados.

Existem diferentes formas de realizar essa conexão:

- **`mysql_connect()`**: Uma função mais antiga, que foi descontinuada no PHP 7.
- **`mysqli_connect()`**: Uma versão melhorada, recomendada para MySQL 4.1 ou superior.
- **PDO (PHP Data Objects)**: A forma mais recomendada, pois oferece uma interface consistente e mais segura para acessar diversos tipos de bancos de dados, além de suportar Prepared Statements, que ajudam a prevenir ataques de SQL Injection.

É fundamental implementar o tratamento de erros para a conexão, informando ao usuário caso haja algum problema.

## Formulário de Login (HTML)

A interface de login é criada em uma página HTML (ex: `login.html`, `index.php`) e consiste em:

- Um elemento `<form>` com o atributo `action` apontando para o script PHP que processará o login e `method="post"` para enviar os dados de forma mais segura (oculta na URL).
- Campos de entrada (`<input>`) para o nome de usuário/e-mail (tipo `text`) e senha (tipo `password`).
- Um botão de submissão (`<input type="submit">`).
- O layout pode ser estilizado com frameworks CSS como Bootstrap para uma melhor experiência visual.

## Processamento do Login (Script PHP)

O script PHP responsável por processar os dados do formulário (ex: `login_vai.php`, `ope.php`, `login.php`) executa as seguintes etapas:

1. **Início da Sessão**: A função `session_start()` deve ser a primeira instrução PHP em qualquer script que utilize sessões, antes de qualquer saída de conteúdo HTML.
2. **Recuperação dos Dados**: Os valores inseridos nos campos do formulário são recuperados utilizando a superglobal `$_POST`, por exemplo, `$_POST['login']` e `$_POST['senha']`.
3. **Criptografia da Senha**: Antes de comparar a senha fornecida pelo usuário com a senha armazenada no banco de dados, é essencial criptografar a senha recebida do formulário. Historicamente, `md5()` foi usado, mas métodos mais seguros de hashing (como bcrypt) são a prática atual e frameworks como Laravel lidam com isso automaticamente.
4. **Consulta ao Banco de Dados**: Uma consulta SQL (`SELECT`) é executada no banco de dados para verificar se existe um registro de usuário que corresponda ao login e à senha fornecidos. Exemplo: `SELECT id, nome, login, senha, postar FROM aut_usuarios WHERE login = '$login'`.
5. **Verificação e Autenticação**:
    - Se a consulta retornar um ou mais registros, significa que as credenciais são válidas.
    - Os dados importantes do usuário (ID, nome, permissão) são então armazenados em variáveis de sessão, como `$_SESSION["id_usuario"]`, `$_SESSION["nome_usuario"]` e `$_SESSION["permissao"]`.
    - O usuário é redirecionado para uma página restrita ou para o painel administrativo (ex: `index.php`, `site.php`, `dashboard`) usando a função `header("Location: ...")`.
6. **Tratamento de Login Inválido**: Caso as credenciais não correspondam a nenhum registro no banco, uma mensagem de erro (ex: "E-mail ou senha inválido") é exibida, e o usuário é redirecionado de volta para a página de login para tentar novamente. Nesse cenário, quaisquer sessões anteriores podem ser destruídas com `unset()`.

## Proteção de Páginas Restritas

Para garantir que apenas usuários logados possam acessar certas áreas do site:

- Um script de verificação de sessão (ex: `verifica.php`) é incluído no início de todas as páginas que devem ser restritas.
- Este script verifica se as variáveis de sessão de login (e.g., `$_SESSION["id_usuario"]`) existem e estão definidas.
- Se as variáveis de sessão não existirem, o usuário é imediatamente redirecionado para a página de login.
- Em frameworks como Laravel, essa proteção é simplificada pelo uso de middlewares aplicados a grupos de rotas.

## Funcionalidade de Logout

Um link ou botão de "Sair do Sistema" é providenciado para que o usuário possa encerrar sua sessão. Ao clicar, um script PHP (ex: `sair.php`, ou um método de logout em uma Controller) é executado. Este script:

1. Inicia a sessão com `session_start()`.
2. Remove as variáveis de sessão específicas (`unset($_SESSION['usuario'])`) ou destrói a sessão completa (`session_destroy()`).
3. Redireciona o usuário de volta para a página de login.

## Boas Práticas e Considerações Adicionais

- **Segurança**: Além da criptografia de senhas, é fundamental proteger contra ataques de SQL Injection, utilizando Prepared Statements (com PDO) ou filtrando e tratando todas as entradas de dados. A proteção CSRF também é importante em formulários.
- **Experiência do Usuário (UX)**: Em caso de erros de validação no formulário, manter os valores que o usuário já preencheu (usando `old()` no Laravel ou lógica similar em PHP puro) é uma boa prática.
- **Organização do Código**: Separar a lógica em arquivos distintos (conexão, validação, processamento, views, helpers) e seguir padrões de arquitetura como MVC (Model-View-Controller) melhora a manutenção e a legibilidade do código.
- **Ambiente de Desenvolvimento**: Para construir e testar um sistema de login, é necessário um servidor local (XAMPP, WAMP, Laragon) com PHP e MySQL, e um editor de código (Visual Studio Code, Notepad++).
- **Frameworks**: Frameworks como Laravel simplificam e padronizam muitas dessas operações, oferecendo recursos prontos para autenticação, validação, gerenciamento de banco de dados (Models, Migrations), e rotas controladas por Controllers e Middlewares.

Este sistema básico oferece a estrutura para autenticação de usuários, permitindo a construção de aplicações web mais complexas e seguras.

Um sistema de login com PHP e MySQL utilizando sessões envolve a criação de vários arquivos para gerenciar a conexão com o banco de dados, o formulário de login, o processamento da autenticação, a verificação de sessão e o logout. As senhas são criptografadas em MD5 para aumentar o nível de segurança.

## Exemplo

Aqui está um exemplo de implementação:

### 1. Conexão com o Banco de Dados (`comum.php`)

Este arquivo é responsável por estabelecer a conexão com o banco de dados MySQL e será incluído em todas as páginas que precisarem interagir com ele.

```php
<?php
// Conecta-se com o MySQL
mysql_connect("localhost", "root", "root"); // (Nota: Esta função é obsoleta em PHP moderno. Para PHP 7+ e versões posteriores, utilize mysqli_connect() ou PDO.)
// Seleciona banco de dados
mysql_select_db("noticias"); //
?>
```

**Observação**: A função `mysql_connect()` é uma função mais antiga e foi descontinuada no PHP 7. Em implementações modernas, `mysqli_connect()` ou PDO (PHP Data Objects) são as alternativas recomendadas para uma conexão segura e eficaz.

### 2. Formulário de Login (`login.html`)

Esta é a página HTML que apresenta o formulário onde o usuário digitará o login e a senha.

```php
<HTML>
<HEAD><TITLE>Sistema de Notícias : Login</TITLE></HEAD>
<BODY>
<form action="login_vai.php" method="post"> //
Sistema Autenticação de Notícias.<BR>
Login: <input type="text" name="login"><br> //
Senha: <input type="password" name="senha"><br> //
<input type="submit" value="OK!"> //
</form>
</BODY>
</HTML>
```

### 3. Script de Processamento do Login (`login_vai.php`)

Esta página recebe os dados do formulário (`login.html`), verifica as credenciais no banco de dados e gerencia as sessões.

```php
<?php
// Conexão com o banco de dados
require "comum.php"; //

// Inicia sessões
session_start(); //

// Recupera o login e a senha, criptografando a senha em MD5
$login = isset($_POST["login"]) ? addslashes(trim($_POST["login"])) : FALSE; //
$senha = isset($_POST["senha"]) ? md5(trim($_POST["senha"])) : FALSE; //

// Usuário não forneceu a senha ou o login
if(!$login || !$senha) { //
    echo "Você deve digitar sua senha e login!"; //
    exit;
}

/**
 * Executa a consulta no banco de dados para verificar as credenciais.
 * Caso o número de linhas retornadas seja 1, o login é válido, caso 0, inválido.
 */
$SQL = "SELECT id, nome, login, senha, postar FROM aut_usuarios WHERE login = '" . $login . "'"; //
$result_id = @mysql_query($SQL) or die("Erro no banco de dados!"); //
$total = @mysql_num_rows($result_id); //

// Caso o usuário tenha digitado um login válido, o número de linhas será 1
if($total) { //
    // Obtém os dados do usuário para verificar a senha e passar os demais dados para a sessão
    $dados = @mysql_fetch_array($result_id); //

    // Agora verifica a senha (comparando as senhas já criptografadas em MD5)
    if(!strcmp($senha, $dados["senha"])) { //
        // TUDO OK! Agora, passa os dados para a sessão e redireciona o usuário
        $_SESSION["id_usuario"] = $dados["id"]; //
        $_SESSION["nome_usuario"] = stripslashes($dados["nome"]); //
        $_SESSION["permissao"] = $dados["postar"]; //
        header("Location: index.php"); // // Redireciona para a página principal (restrita)
        exit;
    }
    // Senha inválida
    else { //
        echo "Senha inválida!"; //
        exit;
    }
}
// Login inválido
else { //
    echo "O login fornecido por você é inexistente!"; //
    exit;
}
?>
```

**Observações Importantes**:

- A função `session_start()` deve ser a primeira instrução PHP em qualquer script que utiliza sessões, antes de qualquer saída de conteúdo HTML.
- A senha fornecida pelo usuário (`$_POST["senha"]`) é criptografada com `md5()` antes de ser comparada com a senha armazenada no banco de dados. A função `strcmp()` é usada para comparar as duas senhas já criptografadas. `strcmp` retorna zero se as strings forem iguais, por isso o uso de `!` (operador NOT).
- Em caso de sucesso na autenticação, os dados do usuário (id, nome, permissão) são armazenados na superglobal `$_SESSION` e o usuário é redirecionado para a página `index.php`.
- Se o login ou a senha estiverem incorretos, mensagens de erro são exibidas e o processamento é interrompido.

### 4. Verificação de Sessão (`verifica.php`)

Este script é incluído no início de todas as páginas que você deseja restringir, garantindo que apenas usuários autenticados possam acessá-las.

```php
<?php
// Inicia sessões
session_start(); //

// Verifica se existe os dados da sessão de login
if(!isset($_SESSION["id_usuario"]) || !isset($_SESSION["nome_usuario"])) { //
    // Usuário não logado! Redireciona para a página de login
    header("Location: login.html"); //
    exit;
}
?>
```

### 5. Script de Logout (`sair.php`)

Esta página permite que o usuário encerre sua sessão, destruindo todas as variáveis de sessão e redirecionando-o para a página de login.

```php
<?php
// Inicia sessões, para assim poder destruí-las
session_start(); //
session_destroy(); // // Destrói todas as variáveis de sessão de uma única vez.
header("Location: login.html"); //
?>
```

### Exemplo de Uso (Página Restrita - `index.php`)

A página `index.php` é um exemplo de uma página que exigiria autenticação. Nela, você incluiria os arquivos `verifica.php` e `comum.php`.

```php
<?php
// Verificador de sessão
require "verifica.php"; //
// Conexão com o banco de dados
require "comum.php"; //

// Imprime mensagem de boas-vindas
echo "<font face=\"Verdana\" size=2>Bem-Vindo " . $_SESSION["nome_usuario"] . "!<BR>\n"; //

// ... (Restante do conteúdo da página, como listagem de notícias, etc.)

// Imprime link de logout
echo " | <a href=\"sair.php\">Sair do Sistema</a>"; //
echo "<br><br>\n";

// ... (Outros conteúdos dinâmicos que podem depender das permissões do usuário)
?>
```

Este é um sistema de login básico que demonstra a lógica de autenticação usando PHP, MySQL e sessões. É fundamental para gerenciar o acesso de usuários e proteger áreas restritas de uma aplicação web.

[Sistema de Login com PHP e MySQL - YouTube](https://www.youtube.com/watch?v=Ln7lqyWJPUE)
