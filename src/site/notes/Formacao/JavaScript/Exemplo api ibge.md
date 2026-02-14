---
{"dg-publish":true,"permalink":"/formacao/java-script/exemplo-api-ibge/","metatags":{"description":"utilizando a API do IBGE com JavaScript"},"noteIcon":2,"updated":"2026-02-13T22:14:03.000-03:00"}
---

#JavaScript #exemplo 

# Exemplo api ibge

Para listar os municípios por Unidade da Federação (UF) utilizando a API do IBGE com JavaScript, o desenvolvedor deve realizar uma **requisição assíncrona** ao endpoint de localidades do instituto,. O endereço base para essa consulta é `https://servicodados.ibge.gov.br/api/v1/localidades/estados/{UF}/municipios`, onde o parâmetro `{UF}` deve ser substituído pela sigla ou ID do estado,,.

## 1. Utilizando Ajax jQuery (Método via Biblioteca)

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
    conteudo += '<li>'+val.nome+'</li>';
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

Exemplo JavaScript com Select com uma lista de municípios:

```js
let url = 'https://servicodados.ibge.gov.br/api/v1/IocaIidades/estados/CE/municipios';
/// requisição JSON
$.getJSON(ur1, function(data){
  let conteudo = '<optiongroup>';
  $.each(data, function(v,val){
    if(val.nome = 'Itapipoca') {
      conteudo += '<option selected>' +val.nome +'<option>';
    else{
      conteudo += '<option>' +val.nome+' </option>' ;    
    }
});
conteudo += '</optiongroup>';
$("#municipios").html(conteudo);
```

## 2. Utilizando a Fetch API (Método Nativo)

A **Fetch API** é a interface moderna do JavaScript para intercâmbio de dados via AJAX.

- **Chamada da API:** Utiliza-se a função `fetch(url)` passando a URL formatada com a sigla do estado escolhido (geralmente capturada por um evento `onchange`),.
- **Tratamento da Resposta:** Por ser um processo assíncrono, utiliza-se a estrutura de promessas com **`.then()`**. O primeiro `.then()` recebe a resposta bruta e utiliza `response.json()` para converter o texto recebido em um objeto JavaScript,.
- **Manipulação do DOM:** No segundo `.then()`, o programador recebe o array de municípios. Utiliza-se um laço **`for`** para percorrer cada item, criando dinamicamente elementos HTML, como o **`<option>`**, onde a propriedade `id` da API é atribuída ao valor do campo e a propriedade `nome` é usada como o texto visível,.
- **Inserção na Página:** O novo elemento é adicionado ao campo de seleção (`<select>`) utilizando o método `add()` ou `appendChild()`.

Refatorando o exemplo de acesso a API do IBGE:

- Para substituir o método `$.getJSON` (AJAX do jQuery) pela **Fetch API** (padrão moderno do JavaScript), precisamos alterar a forma como as requisições são feitas e como as respostas são tratadas.
- A Fetch API utiliza Promises, então usamos `.then()` para processar a resposta (convertendo para JSON) e `.catch()` para tratar erros, o que torna o código mais limpo e padronizado.

Exemplo do HTML:

```html
  <h1>Cidades por estado</h1>
  <select name="estados" id="uf"></select>
  <select name="municipios" id="municipios"></select>
  <div id="info-municipio"></div>
```

Exemplo de código JavaScript:

```js
// 1. URL para obter os estados ordenados por nome
const urlEstados = 'https://servicodados.ibge.gov.br/api/v1/localidades/estados?orderBy=nome';

const ufSelect = document.getElementById('uf');
const municipioSelect = document.getElementById('municipios');
const infoDiv = document.getElementById('info-municipio');

// 2. Preencher o select de estados assim que a página carregar
fetch(urlEstados)
  .then(response => response.json())
  .then(data => {
	let itens = '<option value="">Selecione o Estado</option>';
	data.forEach(val => {
	  itens += `<option value="${val.sigla}">${val.sigla} - ${val.nome}</option>`;
	});
	ufSelect.innerHTML = itens;
  })
  .catch(error => {
	console.error("Erro ao carregar estados:", error);
	ufSelect.innerHTML = '<option>Erro ao carregar</option>';
  });

// 3. Carregar os municípios quando um estado for selecionado
ufSelect.addEventListener('change', function () {
  let uf = this.value;
  if (!uf) return;
  let url = `https://servicodados.ibge.gov.br/api/v1/localidades/estados/${uf}/municipios`;

  infoDiv.innerHTML = ''; // Limpa informações anteriores ao trocar de estado

  fetch(url)
	.then(response => response.json())
	.then(data => {
	  let conteudo = '<option value="">Selecione o Município</option>';
	  data.forEach(val => {
		conteudo += `<option value="${val.id}">${val.nome}</option>`;
	  });
	  municipioSelect.innerHTML = conteudo;
	})
	.catch(error => {
	  console.error("Erro ao carregar municípios:", error);
	  municipioSelect.innerHTML = '<option>Erro ao carregar</option>';
	});
});

// 4. Mostrar informações do município selecionado
municipioSelect.addEventListener('change', function () {
  let municipioId = this.value;
  if (!municipioId) return;

  let url = `https://servicodados.ibge.gov.br/api/v1/localidades/municipios/${municipioId}`;

  fetch(url)
	.then(response => response.json())
	.then(data => {
	  let info = `<h3>${data.nome}</h3><p>Microrregião: ${data.microrregiao.nome}</p><p>Mesorregião: ${data.microrregiao.mesorregiao.nome}</p><p>Região: ${data.microrregiao.mesorregiao.UF.regiao.nome}</p>`;
	  infoDiv.innerHTML = info;
	})
	.catch(error => {
	  console.error("Erro ao carregar informações:", error);
	  infoDiv.innerHTML = '<p>Erro ao carregar informações do município.</p>';
	});
});
```

### O que mudou

1. **`fetch(url)`**: Substitui o `$.getJSON(url)`.
2. **`.then(response => response.json())`**: Necessário para converter a resposta bruta da API em um objeto JavaScript (JSON).
3. **`data.forEach(...)`**: Substitui o `$.each(...)` do jQuery para iterar sobre os arrays de forma nativa.
4. **Tratamento de Erro**: O `.catch()`  funciona para capturar erros de rede ou problemas na conversão do JSON.

### Vantagens do Fetch sobre o Ajax

A principal vantagem de usar a Fetch API em vez do AJAX do jQuery ($.ajax ou $.getJSON) é que o Fetch é nativo do JavaScript moderno, enquanto o AJAX depende de uma biblioteca externa.

Aqui estão os principais pontos de comparação:

1. Zero Dependências (Mais Leve)
  - Fetch: Já vem embutido no navegador. Você não precisa baixar nem importar o jQuery (que pesa cerca de 30kb a 80kb) apenas para fazer requisições. Isso deixa seu site mais rápido.
  - AJAX: Exige que você inclua a tag <script src="jquery..."></script>.
2. Baseado em Promises e Async/Await
  - O Fetch foi desenhado para trabalhar com Promises, o que permite escrever um código muito mais limpo e legível, evitando o "inferno de callbacks" (várias funções uma dentro da outra).

```js
Com jQuery (Callback):
javascript
$.getJSON('url', function(data) {
    console.log(data);
});
Com Fetch (Moderno com Async/Await):
javascript
const response = await fetch('url');
const data = await response.json();
console.log(data);
```

3. Padrão da Web (Standard)
  - O Fetch é o padrão atual da web (W3C). O XMLHttpRequest (base do AJAX do jQuery) é uma tecnologia antiga e complexa que o jQuery tentava simplificar. O Fetch já nasceu simples.

>[!info] ⚠️ Uma diferença importante (Pegadinha)
> O Fetch não considera erros HTTP (como 404 ou 500) como falhas na Promise.
>
> - No jQuery, se der erro 404, ele cai direto no .fail() ou .catch().
> - No Fetch, ele considera que a requisição "chegou e voltou", então entra no .then(). Você precisa verificar manualmente a propriedade response.ok.

Exemplo de verificação manual no Fetch:

```javascript
 Show full code block 
fetch(url)
  .then(response => {
    if (!response.ok) { // Verifica se é 200-299
      throw new Error('Erro na requisição: ' + response.status);
    }
    return response.json();
  })
  .then(data => ...)
  .catch(erro => console.error(erro)); // Agora sim pega o erro 404
```

### Boas Práticas Recomendadas

- **Limpeza de Dados:** É essencial limpar a lista de cidades (definindo `innerHTML = ""` ou usando `.empty()`) sempre que o usuário trocar de estado, para garantir que as cidades do estado anterior não permaneçam na tela.
- **Tratamento de Erros:** Deve-se prever falhas na rede ou no serviço utilizando o método **`.catch()`** (na Fetch API) ou **`.fail()`** (no jQuery) para informar o usuário caso os dados não possam ser carregados,.

## Referências

- [Código ibge.html no GitHub](https://github.com/jocile/programadorweb2026/blob/main/exercicios/ibge.html) - [Visualizar Cidades do Ceará](https://jocile.github.io/programadorweb2026/exercicios/ibge.html)
- [Código ibge-fetch.html no GitHub](https://github.com/jocile/programadorweb2026/blob/main/exercicios/ibge-fetch.html) - [Visualizar Cidades do Ceará com fetch API](https://jocile.github.io/programadorweb2026/exercicios/ibge-fetch.html)
- [jQuery CDN](https://releases.jquery.com/)
- [API IBGE - Listando municípios por UF - Javascript - YouTube](https://www.youtube.com/watch?v=_mD8JKi5YCE)
- [API IBGE - gerando um campo select com uma lista de municípios - Javascript - YouTube](https://www.youtube.com/watch?v=2FjU6DbY9v8)
- [Eventos JavaScript - Gerando select de cidades baseado em um select de estados. - YouTube](https://www.youtube.com/watch?v=L_dP5dgfgt8)
- [Tutorials - Leaflet - a JavaScript library for interactive maps](https://leafletjs.com/examples.html) - [Explorando o Poder do Leaflet: Crie Mapas Interativos com JavaScript! - YouTube](https://www.youtube.com/watch?v=SctXG86xPw0)
