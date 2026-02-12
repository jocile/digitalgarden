---
{"dg-publish":true,"permalink":"/formacao/java-script/j-query/","metatags":{"description":"é uma biblioteca JavaScript poderosa e amplamente adotada"},"noteIcon":2,"updated":"2026-02-12T10:21:31.585-03:00"}
---

#JavaScript #Webdesign 

# JQuery

O **jQuery** é uma biblioteca JavaScript poderosa e amplamente adotada, criada por **John Resig** com o lema **"write less, do more"** (escreva menos, faça mais). Sua função primordial é simplificar a manipulação de documentos HTML, o tratamento de eventos, a criação de animações e as interações com **AJAX** para o desenvolvimento rápido de aplicações web.

Abaixo estão os pontos principais para discutir o jQuery conforme as fontes:

## 1. Propósito e Vantagens

- **Abstração de Navegadores:** O jQuery resolve o problema histórico de inconsistências entre navegadores (como diferentes versões do Internet Explorer, Chrome e Firefox), permitindo que um único código funcione em diversas plataformas sem a necessidade de "gambiarras" ou múltiplos `if`s.
- **Simplicidade:** Tarefas que exigiriam dezenas de linhas em JavaScript puro podem ser realizadas com poucas linhas usando jQuery.
- **Encadeamento (Chaining):** Uma característica fundamental que permite executar várias operações em sequência sobre os mesmos elementos selecionados, tornando o código mais limpo e performático.

## 2. Sintaxe e Seletores

- **O Símbolo `$`: Atua como um apelido curto para a função `jQuery`**. Uma expressão básica segue o formato `$("seletor").ação()`.
- **Seletores:** O jQuery utiliza seletores baseados em CSS para identificar elementos na página, como tags (`$("p")`), IDs (`$("#id")`) e classes (`$(".classe")`). Existem também seletores avançados e pseudo-seletores próprios da biblioteca, como `:even`, `:odd`, `:first` e `:last`.

Os seletores são fundamentais no jQuery para indicar quais elementos serão manipulados, utilizando uma sintaxe baseada em CSS. Abaixo estão exemplos práticos divididos pelas categorias citadas:

### **2.1. Seletores Básicos**

- **Tag HTML:** `$("p")` seleciona todos os elementos de parágrafo da página.
- **Classe:** `$(".par")` localiza todos os elementos que possuem a classe "par", utilizando um ponto antes do nome.
- **ID:** `$("#texto")` seleciona o elemento exclusivo que possui o ID "texto", utilizando o caractere `#`.
- **Universal:** `$("*")` seleciona todos os elementos contidos no documento.

### **2.2. Seletores de Atributo**

- **Presença de Atributo:** `$("div[id]")` seleciona todos os `divs` que possuem qualquer ID definido.
- **Igualdade:** `$("img[title='logo']")` seleciona imagens com o título exatamente igual a "logo".
- **Início de valor:** `$("img[title^='logo']")` seleciona imagens cujo título começa com a string "logo".
- **Fim de valor:** `$("img[title$='logo']")` seleciona imagens cujo título termina com "logo".

### **2.3. Seletores de Hierarquia**

- **Descendente:** `$("div span")` seleciona todos os `spans` que estão dentro de um `div`, independentemente do nível.
- **Filho direto:** `$("div > span")` seleciona apenas os `spans` que são filhos imediatos de um `div`.
- **Irmão adjacente:** `$("h1 + p")` seleciona o parágrafo que aparece imediatamente após um título `h1`.

### **2.4. Filtros Básicos e de Conteúdo**

- **Posição específica:** `$("div:eq(3)")` seleciona o quarto elemento `div` da lista (o índice começa em 0).
- **Paridade:** `$("li:even")` seleciona os itens de lista de índice par e `$("li:odd")` os de índice ímpar.
- **Visibilidade:** `$("div:hidden")` seleciona elementos que não ocupam espaço na página e `$("div:visible")` os que estão visíveis.
- **Conteúdo de texto:** `$("div:contains('k19')")` seleciona `divs` que possuem o texto "k19" em seu corpo.

### **2.5. Seletores de Formulário**

- **Elementos de entrada:** `$(":input")` seleciona todos os campos `input` e `textarea`.
- **Tipos específicos:** `$(":checkbox")` seleciona todos os campos do tipo checkbox e `$(":password")` seleciona campos de senha.
- **Estados:** `$(":checked")` localiza checkboxes ou botões de rádio que estão marcados.

## 3. Funcionalidades Principais

- **Manipulação do DOM:** Oferece métodos para alterar conteúdos (`.html()`, `.text()`), atributos (`.attr()`), propriedades (`.prop()`) e estilos CSS (`.css()`). Também facilita a inserção de novos elementos com métodos como `.append()`, `.prepend()`, `.after()` e `.before()`.
- **Eventos:** Simplifica o registro de ações do usuário, como `.click()`, `.change()`, `.mouseenter()` e `.keydown()`. O método `.on()` é a forma recomendada para associar eventos a elementos, permitindo inclusive o uso de _namespaces_ para evitar conflitos.
- **Efeitos e Animações:** Inclui efeitos prontos como deslizamentos (`.slideDown()`, `.slideUp()`), esmaecimentos (`.fadeIn()`, `.fadeOut()`) e a função genérica `.animate()` para animar propriedades CSS.
- **AJAX:** Permite atualizar partes de uma página sem recarregá-la totalmente através de métodos simplificados como `$.get()`, `$.post()`, `$.getJSON()` e o método mais robusto `$.ajax()`.

Com base nas categorias de funcionalidades descritas anteriormente, aqui estão exemplos práticos de código jQuery:

### **3.1. Manipulação do DOM**

Essa funcionalidade permite alterar elementos, atributos e estilos de uma página de forma dinâmica.

- **Adicionar uma classe CSS:** `$("div").addClass("destaque grid")`.
- **Inserir conteúdo ao final de um elemento:** `$("p").append("<em>(fonte K19)</em>")`.
- **Recuperar o valor de um atributo (como o ID):** `var id = $("div").attr("id");`.
- **Alterar o conteúdo HTML interno:** `$("#div1").html("<h1>K19</h1><p>Cursos da K19.</p>")`.
- **Modificar o valor de um campo de entrada:** `$("#texto").val("esse é o novo texto")`.

### **3.2. Eventos**

O jQuery simplifica a captura de ações do usuário, como cliques ou digitação.

- **Evento de Clique:** `$("#esconder").click(function() { $("div").slideUp(); });`.
- **Evento de Mudança (Change):** `$(".quantity").change(function() { writeTotal(calculateTotalProducts()); });`.
- **Associação múltipla com namespaces:** `$("#tarefa").on("keydown.primeiro", function() { console.log("Primeiro evento"); });`.
- **Evento disparado ao perder o foco:** `element.on("blur.validador", onElementBlur);`.

### **3.3. Efeitos e Animações**

Permitem criar transições visuais suaves para os elementos.

- **Esmaecimento:** `$("#div").fadeIn();` ou `$("#div").fadeOut();`.
- **Deslizamento:** `$("#div").slideUp();` ou `$("#div").slideDown();`.
- **Animação de propriedades personalizadas:**
    
```js
$("#div").animate({ "border-width": "50px", "margin-top": "100px" });
```

### **3.4. AJAX**

Facilita a comunicação assíncrona com o servidor sem recarregar a página.

- **Requisição simples (GET):** `$.get(servico, function(data) { alert(data); });`.
- **Envio de dados (POST):** `$.post(server + "/tarefa", {tarefa_id: id, texto: text});`.
- **Captura de dados em formato JSON:** `$.getJSON(servico + cep).done(onCepDone).fail(onCepError);`.
- **Carregamento de conteúdo diretamente em um elemento:** `$("#conteudo").load("k19.html");`.

## 4. Ecossistema e Bibliotecas Complementares

- **jQuery UI:** Uma biblioteca de componentes visuais, efeitos e temas construída sobre o jQuery, oferecendo widgets como **Accordion**, **Datepicker**, janelas de diálogo (Dialog) e menus.
- **jQuery Mobile:** Um framework focado no desenvolvimento de sites para dispositivos móveis, garantindo aparência consistente em diferentes plataformas.
- **Plugins:** O jQuery é facilmente extensível, permitindo que desenvolvedores criem e compartilhem seus próprios métodos integrados à biblioteca.

O ecossistema do jQuery é vasto e composto por bibliotecas oficiais e de terceiros que estendem suas funcionalidades para interfaces ricas, dispositivos móveis e ferramentas específicas. Abaixo estão os exemplos:

### **4.1. jQuery UI (Componentes Visuais e Efeitos)**

Esta biblioteca oferece widgets e interações para desktop. Exemplos incluem:

- **Accordion (Sanfona):** Organiza o conteúdo exibindo apenas uma seção por vez. Código: `$("#accordion").accordion();`.
- **Autocomplete:** Fornece sugestões de texto enquanto o usuário digita. Código: `$("#tags").autocomplete({source: availableTags});`.
- **Datepicker (Calendário):** Um widget para seleção de datas totalmente configurável e traduzível.
- **Dialog (Janelas de Diálogo):** Exibe informações ou solicita decisões do usuário em janelas sobrepostas à página.
- **Botões:** Melhora a aparência visual de botões de formulário e links.
- **Tooltips:** Cria legendas personalizadas para elementos da página.

### **4.2. jQuery Mobile (Aplicações para Dispositivos Móveis)**

Focada em garantir uma aparência consistente em diferentes plataformas móveis. Exemplos incluem:

- **Widgets Específicos:** **ListView** (listas otimizadas para toque), **Collapsible** (listas que abrem e fecham) e botões com ícones específicos como `data-icon="home"` ou `search`.
- **Transições de Página:** Efeitos visuais para troca de telas, como `fade`, `pop`, `flip`, `turn` e `slide`.
- **Temas:** Uso do atributo `data-theme` para aplicar estilos pré-definidos (A a E) ou criados via **ThemeRoller**.
- **Geolocalização:** Integração com a API do Google Maps para exibir a localização do usuário.

### **4.3. Plugins (Extensões de Terceiros e Personalizadas)**

O jQuery permite que desenvolvedores criem seus próprios métodos integrados à biblioteca através do objeto `jQuery.fn`.

- **MaskMoney:** Plugin para formatação dinâmica de campos monetários (ex: R$ 1.234,56).
- **jqPlot:** Ferramenta para geração de centenas de tipos de gráficos utilizando o componente Canvas do HTML5.
- **Validador Personalizado:** Exemplo de criação de um plugin para verificar CPFs ou campos obrigatórios de forma encadeada.
- **Twitter Integration:** Plugins que permitem carregar e exibir os últimos tweets de um perfil diretamente na página.

### **4.4. Alternativas Leves**

Para situações onde o desempenho em redes móveis é crítico, as fontes mencionam o **Zepto.js**, uma biblioteca com sintaxe quase idêntica ao jQuery, porém quatro vezes menor em tamanho. Além disso, microframeworks como o **Hammer.js** são recomendados para gestos de toque.

## 5. Considerações Atuais

Embora o jQuery ainda seja onipresente, os navegadores modernos e as novas especificações do JavaScript (**ES6+**) implementaram nativamente muitas funcionalidades que antes dependiam da biblioteca, como o `document.querySelector` e métodos de array como `.map()`, `.filter()` e `.reduce()`. Em casos simples onde a compatibilidade com navegadores muito antigos não é exigida, o uso de JavaScript puro pode ser até **11 vezes mais rápido** que o jQuery em operações de leitura e modificação de elementos.

Com base nos tópicos discutidos anteriormente sobre o cenário atual do desenvolvimento com JavaScript e jQuery, os exemplos extraídos das fontes que ilustram as **considerações atuais** de performance e evolução tecnológica são:

### **5.1. Substituição por Métodos Nativos (JavaScript Puro)**

Embora o jQuery simplifique o código, operações simples em navegadores modernos podem ser realizadas de forma muito mais rápida usando JavaScript puro (Vanilla JS).

- **Leitura/Escrita de Conteúdo:** Em vez de usar `$("#teste").html()`, o uso direto de `elemento.innerHTML` ou `elemento.textContent` é significativamente mais performático.
- **Acesso ao ID:** Para recuperar o ID de um elemento, a instrução nativa `elemento.id` é mais rápida do que criar um objeto jQuery com `$(this).attr('id')`.

### **5.2. Métodos Declarativos do ES6+**

A evolução da linguagem introduziu métodos que tornam desnecessário o uso de loops imperativos manuais ou funções de bibliotecas para manipulação de coleções.

- **`map()`:** Utilizado para transformar dados e criar um novo array sem modificar o original.
- **`filter()`:** Empregado para selecionar apenas itens que atendam a um critério lógico específico.
- **`reduce()`:** Usado para agregar valores, como calcular o custo total de uma folha de pagamento a partir de uma lista filtrada.

### **5.3. Alternativas Leves para Dispositivos Móveis**

Para combater o problema do "peso" das bibliotecas em conexões móveis lentas, as fontes sugerem alternativas otimizadas:

- **Zepto.js:** Uma biblioteca com sintaxe quase idêntica ao jQuery, porém quatro vezes menor em tamanho (ex: 23.5 KB contra 90.5 KB do jQuery), ideal para carregar rapidamente em redes problemáticas.
- **Hammer.js:** Um microframework especializado em reconhecer gestos de toque, recomendado quando não é possível se livrar completamente de bibliotecas, mas busca-se leveza.

### **5.4. Tipagem e Segurança Lógica**

Uma tendência futura apontada é a integração com paradigmas funcionais e tipagem rigorosa através de ferramentas como o **TypeScript**, que adiciona uma camada de segurança sobre a flexibilidade do JavaScript tradicional.

## Referências

- [JQuery](https://api.jquery.com/)
- [jQuery Introduction](https://www.w3schools.com/jquery/jquery_intro.asp)
- [Getting Started with jQuery UI - jQuery Learning Center](https://learn.jquery.com/jquery-ui/getting-started/)
- [Livro de jQuery e Javascript - Casa do Código](https://www.casadocodigo.com.br/products/livro-javascript-jquery)
- [[Programador Web 2026\|Programador Web 2026]]
- [[Formacao/Formacao em JavaScript\|Formacao em JavaScript]]
