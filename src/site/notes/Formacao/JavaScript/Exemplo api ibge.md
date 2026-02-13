---
{"dg-publish":true,"permalink":"/formacao/java-script/exemplo-api-ibge/","metatags":{"description":"Exemplos de scripts com tomada de decisão"},"noteIcon":2,"updated":"2026-02-13T13:33:36.636-03:00"}
---

#JavaScript #exemplo 

# Exemplo api ibge

Para listar os municípios por Unidade da Federação (UF) utilizando a API do IBGE com JavaScript, o desenvolvedor deve realizar uma **requisição assíncrona** ao endpoint de localidades do instituto,. O endereço base para essa consulta é `https://servicodados.ibge.gov.br/api/v1/localidades/estados/{UF}/municipios`, onde o parâmetro `{UF}` deve ser substituído pela sigla ou ID do estado,,.

## Descrição

Existem duas abordagens principais para implementar essa lógica:

### 1. Utilizando a Fetch API (Método Nativo)

A **Fetch API** é a interface moderna do JavaScript para intercâmbio de dados via AJAX.

- **Chamada da API:** Utiliza-se a função `fetch(url)` passando a URL formatada com a sigla do estado escolhido (geralmente capturada por um evento `onchange`),.
- **Tratamento da Resposta:** Por ser um processo assíncrono, utiliza-se a estrutura de promessas com **`.then()`**. O primeiro `.then()` recebe a resposta bruta e utiliza `response.json()` para converter o texto recebido em um objeto JavaScript,.
- **Manipulação do DOM:** No segundo `.then()`, o programador recebe o array de municípios. Utiliza-se um laço **`for`** para percorrer cada item, criando dinamicamente elementos HTML, como o **`<option>`**, onde a propriedade `id` da API é atribuída ao valor do campo e a propriedade `nome` é usada como o texto visível,.
- **Inserção na Página:** O novo elemento é adicionado ao campo de seleção (`<select>`) utilizando o método `add()` ou `appendChild()`.

Exemplo de código JavaScript:

```js
// URL da API do IBGE para municípios de um estado (ex: SP)
const uf = 'SP';
const url = `https://servicodados.ibge.gov.br/api/v1/localidades/estados/CE/municipios`;

// Função assíncrona para buscar os dados
async function listarMunicipios() {
  try {
    // 1. Faz a requisição Fetch
    const response = await fetch(url);
    
    // 2. Converte a resposta em JSON
    const municipios = await response.json();
    
    // 3. Manipula os dados (ordena e lista)
    console.log(`Municípios de ${uf}:`);
    municipios.sort((a, b) => a.nome.localeCompare(b.nome)).forEach(m => {
      console.log(`- ${m.nome} (ID: ${m.id})`);
    });
    
  } catch (error) {
    console.error('Erro ao buscar dados:', error);
  }
}

// Chama a função
listarMunicipios();

```


- Fetch API: Método nativo fetch() é usado para realizar a requisição HTTP GET.
- Async/Await: Torna o código assíncrono mais legível e fácil de gerenciar.
- API IBGE: A URL base é https://servicodados.ibge.gov.br/api/v1/localidades/.
- Manipulação: O resultado é um array de objetos, acessível via .json(). 
- Dica: Você pode substituir 'CE' por qualquer sigla de estado (ex: 'RJ', 'MG', SP') na variável uf.

### 2. Utilizando jQuery (Método via Biblioteca)

O **jQuery** oferece o método **`$.getJSON()`**, que simplifica a sintaxe ao já entregar os dados convertidos,.

- **Sintaxe:** Chama-se `$.getJSON(url, function(data) { ... })`, onde `data` é a variável que conterá a lista de municípios vinda do IBGE.
- **Lógica de Exibição:** Dentro da função de _callback_, percorre-se o array e incrementa-se uma variável de texto com a estrutura HTML desejada (ex: itens de uma lista `<li>`).
- **Injeção de Conteúdo:** Ao final do loop, utiliza-se o método **`.html()`** para jogar todo o conteúdo gerado dentro de um elemento específico da página, como uma `<div>`.

Exemplo HTM para listar as cidades:

```html
<html>
<head>
  <title>Exemplo lista de cidades do IBGE</title>
</head>
<body>
  <div id="lista"></div>
  <script src="https://code.jquery.com/jquery-3.6.e.min.js" integrity="sha256-/xUj+30JU5yEx1q6GSYGSHk7tPXikynS70gEvDej/m4=" crossorigin="anonymous"></script>
  <script type="text/javascript" src="app.js"></script>
</body>
</html>
```

Exemplo JavaScript para listar as cidades:

```js
let url = 'https://servicodados.ibge.gov.br/api/vl/localidades/estados/CE/municipios';
/// requisição JSON
$.getJSON(ur1, function(data){
  Let conteudo = '<ul>';
  $.each(data, function(v,val){
    conteudo '<li>'+val.nome+'</li>';
  })
  conteudo += '</ul>';
  $ ( "#1istaM" ).html(conteudo) ;
});
```

Exemplo HTML com Select em um formulário:

```html
<html>
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<tit1e>Se1ect</tit1e>
</head>
<body>
<header><h1>Eventos Javascript</h1></header>
<main>
  <section>
    <form>
     <label for="uf">UF</label>
     <select id="uf">
       <option></option>
     </select>
     <label for="cidade">Cidade</label>
     <select id="cidade">
       <option></option>
     </select>
    </form>
  </section>
</main>
<script type="text/javascript" src="app.js"></script>
</body>
```

Exemplo JavaScript:

```js
let url = 'https://servicodados.ibge.gov.br/api/v1/IocaIidades/estados/CE/municipios';
///requisicào JSON
$.getJSON(ur1, function(data){
  let conteudo = '<optiongroup>';
  $.each(data, function(v,val){
    conteudo '<option>'+val.nome+'</option>';
  })
  conteudo += '</optiongroup>';
  $ ( "#1istaM" ).html(conteudo) ;
});

```

### Boas Práticas Recomendadas

- **Limpeza de Dados:** É essencial limpar a lista de cidades (definindo `innerHTML = ""` ou usando `.empty()`) sempre que o usuário trocar de estado, para garantir que as cidades do estado anterior não permaneçam na tela.
- **Tratamento de Erros:** Deve-se prever falhas na rede ou no serviço utilizando o método **`.catch()`** (na Fetch API) ou **`.fail()`** (no jQuery) para informar o usuário caso os dados não possam ser carregados,.

## Referências

- [jQuery CDN](https://releases.jquery.com/)
- [API IBGE - Listando municípios por UF - Javascript - YouTube](https://www.youtube.com/watch?v=_mD8JKi5YCE)
- [API IBGE - gerando um campo select com uma lista de municípios - Javascript - YouTube](https://www.youtube.com/watch?v=2FjU6DbY9v8)
- [Eventos JavaScript - Gerando select de cidades baseado em um select de estados. - YouTube](https://www.youtube.com/watch?v=L_dP5dgfgt8)
