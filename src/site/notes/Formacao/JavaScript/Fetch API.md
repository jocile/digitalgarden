---
{"dg-publish":true,"permalink":"/formacao/java-script/fetch-api/","metatags":{"description":"permite que uma página web se comunique com servidores para buscar ou enviar dados sem a necessidade de recarregar"},"noteIcon":2,"updated":"2026-02-13T09:48:06.930-03:00"}
---

#JavaScript #Webdesign

# Fetch API

## Introdução a Fetch API

A **Fetch API** é uma interface moderna do JavaScript projetada para realizar **requisições de rede assíncronas** (comumente chamadas de AJAX), permitindo que uma página web se comunique com servidores para buscar ou enviar dados sem a necessidade de recarregar o documento inteiro.

Abaixo estão os pontos principais sobre o funcionamento e a utilização desta API, conforme as fontes:

### 1. Propósito e Evolução

- **Substituição de métodos antigos:** O `fetch` surge como uma alternativa mais simples e intuitiva ao antigo objeto `XMLHttpRequest` e às funções de AJAX de bibliotecas como o jQuery.
- **Comunicação entre sistemas:** Ela possibilita que o navegador solicite dados de serviços externos (APIs), como listas de cidades do IBGE, ou envie informações para um banco de dados gerenciado por um sistema de backend separado.

### 2. Sintaxe e Funcionamento

- **Requisição Simples (GET):** A forma mais básica de uso é `fetch(url)`, onde o parâmetro é o endereço do serviço que se deseja acessar.
- **Natureza Assíncrona:** O `fetch` não bloqueia a execução do site enquanto aguarda a resposta; ele utiliza uma estrutura baseada em promessas, comumente manipulada através do método **`.then()`**.
- **Tratamento da Resposta:** Quando a resposta do servidor chega, ela não traz apenas os dados, mas também metadados como o status da conexão e cabeçalhos. Para extrair o conteúdo útil, o desenvolvedor deve usar métodos específicos como **`response.json()`** (para converter dados no formato JSON em objetos JavaScript) ou **`response.text()`** (para tratar a resposta como texto puro).

### 3. Configurações Avançadas (POST e Outros Métodos)

- **Configuração de Parâmetros:** Para requisições que não sejam apenas de leitura, o `fetch` aceita um segundo argumento opcional (um objeto de configuração).
- **Envio de Dados:** Nesse objeto, é possível definir o método HTTP (como **POST** ou **PUT**) e o corpo da mensagem (**`body`**) contendo as informações que serão gravadas no servidor.

### 4. Vantagens Práticas

- **Interface Padronizada:** Diferente de abordagens anteriores que exigiam códigos diferentes para navegadores distintos, a Fetch API oferece uma estrutura padronizada para lidar com o intercâmbio de dados.
- **Integração com o DOM:** Os dados recebidos via `fetch` podem ser iterados (usando loops como `for`) para criar dinamicamente novos elementos HTML, como preencher uma lista de seleção (`<select>`) com opções vindas de um serviço externo.


## Diferença entre o Ajax e Fetch

A principal diferença entre os dois reside na sua natureza: o **fetch** é uma interface moderna e **nativa** do JavaScript para realizar requisições de rede assíncronas, enquanto o **$.ajax** é um método pertencente à **biblioteca de terceiros jQuery**.

Abaixo estão detalhadas as principais distinções técnicas e contextuais:

### 1. Origem e Propósito

- **$.ajax (jQuery):** Foi criado para abstrair a complexidade do antigo objeto `XMLHttpRequest` e resolver o problema histórico de **inconsistências entre navegadores** (como as diferenças entre o Internet Explorer e o Firefox), permitindo que um único código funcionasse em diversas plataformas.
- **Fetch API:** Surgiu como uma alternativa nativa, mais simples e intuitiva para substituir tanto o `XMLHttpRequest` quanto os métodos de bibliotecas externas, oferecendo uma interface padronizada nos navegadores modernos.

### 2. Estrutura Lógica e Gerenciamento

- **Promessas vs. Callbacks:** O `fetch` utiliza nativamente a estrutura de **Promessas (Promises)**, sendo manipulado por encadeamentos de `.then()` e `.catch()`. O `$.ajax` retorna um objeto próprio chamado **jqXHR**, que permite o uso de métodos como `.done()` para sucesso e `.fail()` para erros.
- **Tratamento da Resposta:** No `fetch`, a resposta inicial é um objeto bruto; o desenvolvedor deve extrair explicitamente o conteúdo textual ou convertê-lo para JSON usando métodos como `response.json()`. O jQuery frequentemente automatiza esse processo, entregando o dado já convertido.

### 3. Performance e Peso

- **Peso da Biblioteca:** Para usar o `$.ajax`, é necessário carregar a biblioteca jQuery, que adiciona entre **30KB e 90KB** ao peso da página, o que pode ser prejudicial em conexões móveis ou redes lentas. O `fetch`, por ser nativo, tem "peso zero" de carregamento.
- **Velocidade:** Em navegadores modernos, a utilização de métodos nativos (JavaScript puro) pode ser significativamente mais rápida — em alguns casos de leitura e modificação de elementos, até **11 vezes mais rápida** que o jQuery.

### 4. Compatibilidade

- O **jQuery ($.ajax)** ainda é útil para manter compatibilidade com **navegadores muito antigos** (como o IE8), que não suportam as especificações mais recentes do JavaScript.
- O **fetch** é o padrão para o desenvolvimento moderno e profissional, embora exija o uso de _polyfills_ caso o desenvolvedor precise suportar ambientes extremamente antigos.

## Exemplo Prático: Busca de Cidades por Estado

Neste cenário, quando um usuário escolhe um estado em um formulário (evento `onchange`), a Fetch API é disparada para buscar a lista de municípios correspondentes.

**1. A Estrutura da Requisição (GET):** A função `fetch()` inicia a conexão com a URL do serviço. Como o processo é assíncrono e pode demorar, utiliza-se a estrutura de promessas com o método **`.then()`** para definir o que será feito quando o resultado chegar.

- **Primeiro `.then()`:** Recebe a resposta bruta do servidor e utiliza o método **`response.json()`** para extrair o conteúdo textual e convertê-lo em um objeto JavaScript utilizável,.
- **Segundo `.then()`:** Recebe os dados já convertidos (um array de objetos contendo `id` e `nome` das cidades) para manipulação,.

**2. Manipulação do DOM com os Dados:** Após receber o JSON, o código percorre a lista de cidades usando um laço `for`. Para cada item, o JavaScript cria dinamicamente um novo elemento HTML do tipo **`<option>`**, preenche seu valor com o ID da cidade e seu texto visível com o nome, adicionando-o em seguida a um campo de seleção (`<select>`) na página,.

A **Estrutura da Requisição (GET)** utilizando a **Fetch API** é o método moderno e padronizado para solicitar informações de um servidor de forma assíncrona, garantindo que o site continue funcional enquanto os dados são carregados.

Diferente de métodos antigos ou bibliotecas como jQuery, a Fetch API utiliza uma estrutura baseada em **Promessas (Promises)** para gerenciar o tempo de espera da resposta do servidor. Abaixo, detalhamos os componentes dessa estrutura:

### 1. A Chamada Inicial: `fetch(url)`

A requisição começa com a função `fetch()`, que recebe como parâmetro obrigatório a **URL** do serviço (API) que se deseja acessar.

- **Exemplo Prático (IBGE):** Para buscar cidades, a URL é composta por um endereço base somado à sigla do estado escolhido pelo usuário (ex: `.../estados/SP/municipios`).
- **Natureza Assíncrona:** Ao disparar o `fetch()`, o navegador inicia a conexão em "segundo plano", permitindo que o usuário continue interagindo com a página (rolando a tela ou clicando em outros botões) sem travamentos.

Exemplo html:

![Fetch API-1770986080061.png](/img/user/Formacao/JavaScript/Fetch%20API-1770986080061.png)

Exemplo css:

![Fetch API-1770986365213.png](/img/user/Formacao/JavaScript/Fetch%20API-1770986365213.png)

Exemplo JavaScript:



### 2. O Primeiro Contato: O Objeto `response`

Como a rede pode demorar, o `fetch()` retorna uma "promessa" de resposta. Quando o servidor finalmente responde, o primeiro método **`.then()`** é acionado.

- **Metadados:** Este primeiro estágio recebe um objeto de resposta bruto, que contém não apenas os dados solicitados, mas também informações de controle, como o **status da conexão** (se deu certo ou se houve erro 404) e os cabeçalhos de configuração.
- **Extração do Conteúdo:** Para chegar aos dados reais (como a lista de cidades), é necessário extrair a parte textual da resposta. O comando mais comum é o **`response.json()`**, que transforma o texto recebido em um objeto JavaScript manipulável.

### 3. O Recebimento dos Dados: O Segundo `.then()`

Uma vez que o processamento do JSON é concluído (o que também leva um tempo mínimo), um **segundo `.then()`** é executado.

- **Manipulação Real:** É dentro deste bloco que a lógica de programação ganha vida. Aqui, os dados já estão convertidos e prontos para serem usados, por exemplo, para preencher um campo de seleção (`<select>`) ou exibir uma mensagem na tela.
- **Registro de Ações:** Este estágio funciona como um registro: o programador define o que _será feito_ assim que os dados estiverem disponíveis, sem interromper o fluxo do código principal.

### 4. Tratamento de Falhas: O Método `.catch()`

Embora a estrutura básica foque no sucesso, uma requisição profissional deve prever falhas (como queda de internet ou servidor fora do ar). Para isso, utiliza-se o método **`.catch()`** ao final da corrente, que captura qualquer erro ocorrido em qualquer uma das etapas anteriores.

Essa estrutura em "cascata" (encadeamento) torna o código mais limpo e fácil de ler do que as abordagens antigas baseadas em múltiplos _callbacks_ aninhados.

## Envio de Dados (POST)

Além de buscar informações, a Fetch API também pode ser configurada para **enviar dados** a um banco de dados,.

- Nesse caso, a função `fetch()` recebe um segundo parâmetro de configuração.
- Deve-se especificar o **`method: 'POST'`** e o **`body`**, que contém as informações do formulário (como comentários ou cadastros) que serão gravadas no servidor.

Essa abordagem garante uma experiência de usuário fluida, pois o navegador continua operacional enquanto o JavaScript realiza o intercâmbio de dados em "segundo plano",.

## Referências

- [Realizando requisições Ajax em diferentes sistemas com a Fetch API do JavaScript - YouTube](https://www.youtube.com/watch?v=XHLb3yCIhdc)
- [API IBGE - Listando municípios por UF - Javascript - YouTube](https://www.youtube.com/watch?v=_mD8JKi5YCE)
- [JavaScript Fetch API](https://www.w3schools.com/js/js_api_fetch.asp)
- [[Formacao/Formacao em JavaScript\|Formacao em JavaScript]]
- [[Programador Web 2026\|Programador Web 2026]]
- [JSFiddle - Code Playground](https://jsfiddle.net/)
