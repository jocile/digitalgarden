---
{"dg-publish":true,"permalink":"/formacao/webdesign/exercicio-java-sript-cap6/","metatags":{"description":"Exemplos de manipulação de posicionamento do CSS"},"noteIcon":2,"updated":"2026-02-03T13:25:44.174-03:00"}
---

#JavaScript #exercícios 

Atividade prática cujo objetivo é construir um projeto coeso (uma página de blog) que aplica os mesmos conceitos de HTML, CSS e JavaScript de uma forma muito comum no mercado de trabalho.

A atividade guiará os alunos na criação de um layout de duas colunas com `float`, no posicionamento de elementos com `position` e na implementação de uma janela modal interativa com JavaScript (usando jQuery, como no exemplo).

---

### Atividade Prática: Layout de Blog com Janela Modal

**Objetivo:** Utilizar os conceitos de posicionamento do CSS (`display`, `float`, `position`) e a manipulação de eventos com JavaScript para construir a página de um blog simples, que inclui uma janela modal para inscrição em newsletter. Esta atividade aplicará de forma prática os conceitos demonstrados no arquivo [programadorweb2026/livro/cap6.html](https://github.com/jocile/programadorweb2026/blob/main/livro/cap6.html).

#### Parte 1: Estrutura (HTML)

Crie um novo arquivo chamado `exercicio_blog.html`. A estrutura da página deverá conter:

1. Um cabeçalho (`<header>`) para o título do blog e um rodapé (`<footer>`).
2. Um `div` container principal que usará a classe `clearfix` para conter o layout.
3. Dentro do container, crie uma área de conteúdo principal (`<main class="content">`) e uma barra lateral (`<aside class="sidebar">`).
4. O `<main>` deve conter um `<article>` com um título (`<h2>`), uma `div` para a imagem (que conterá a `<img>` e um `<span>` para a tag "Destaque") e alguns parágrafos de texto.
5. O `<aside>` deve conter um título e uma lista de links para outros posts.
6. No `<footer>`, adicione um `div` extra para praticar o posicionamento absoluto.
7. Após o `<footer>`, adicione o `<button>` que irá acionar o modal e, em seguida, as `divs` da estrutura do modal: uma para o `.overlay` e outra para o `.modal`.

#### Parte 2: Estilização (CSS)

Crie um arquivo em `css/exercicio_blog.css` e o vincule ao seu HTML.

1. **Layout com `float`:**
    
    - Faça o `<main class="content">` flutuar para a esquerda (`float: left`) com uma largura de `65%`.
    - Faça o `<aside class="sidebar">` flutuar para a direita (`float: right`) com uma largura de `30%`.
    - Implemente a classe `clearfix` no `div` container para que sua altura se ajuste corretamente aos elementos flutuantes internos.
2. **Posicionamento com `position`:**
    
    - Na `div` que envolve a imagem do artigo, aplique `position: relative`.
    - No `<span>` com o texto "Destaque", aplique `position: absolute` para posicioná-lo sobre a imagem (por exemplo, no canto superior direito).
    - No `<footer>`, aplique `position: relative`. No `div` de informação extra, use `position: absolute` para posicioná-lo no canto inferior direito do rodapé.
3. **Modal com `position: fixed`:**
    
    - Estilize o `.overlay`: defina `position: fixed`, faça-o ocupar toda a tela (`width: 100%`, `height: 100%`, `top: 0`, `left: 0`), aplique um `background-color` com transparência (ex: `rgba(0, 0, 0, 0.6)`) e um `z-index` (ex: 100).
    - Estilize o `.modal`: defina `position: fixed`, um `z-index` maior que o do overlay (ex: 101) e centralize-o na tela. A forma moderna de fazer isso é com `top: 50%`, `left: 50%` e `transform: translate(-50%, -50%)`.
    - Lembre-se de que ambos devem começar escondidos, utilizando `display: none`.

#### Parte 3: Interatividade (JavaScript/jQuery)

Crie um arquivo em `js/exercicio_blog.js` e o vincule ao seu HTML (após a inclusão do jQuery).

1. Capture o evento de clique no botão "Inscreva-se". Na função de callback, use o método `.show()` para exibir o `.overlay` e o `.modal`.
2. Capture o evento de clique tanto no botão de fechar do modal quanto no próprio `.overlay`. Na função de callback, use o método `.hide()` para escondê-los, permitindo que o usuário feche o modal de duas maneiras.

#### ✨ Desafio Extra

- Substitua os métodos `.show()` e `.hide()` por `.fadeIn()` e `.fadeOut()` para adicionar uma animação suave de transição.
- Implemente a funcionalidade de fechar o modal quando o usuário pressionar a tecla "Escape" (`Esc`) no teclado.

---


