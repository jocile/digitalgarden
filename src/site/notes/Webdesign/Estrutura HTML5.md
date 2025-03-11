---
{"dg-publish":true,"permalink":"/webdesign/estrutura-html-5/","title":"Estrutura do HTML5","metatags":{"description":"tags semânticas que ajudam a estruturar o conteúdo de uma página web de forma mais significativa."},"tags":["Webdesign","HTML5"],"updated":"2025-03-11T08:26:17.832-03:00"}
---


## Estrutura de um Site em HTML5 e suas Tags Semânticas

O HTML5 introduziu várias tags semânticas que ajudam a estruturar o conteúdo de uma página web de forma mais significativa. Aqui está uma visão geral da estrutura básica de um site HTML5 e suas principais tags semânticas:

### Estrutura Básica

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Título da Página</title>
</head>
<body>
    <!-- Conteúdo da página -->
</body>
</html>
```

### Tags Semânticas Principais

1. `<header>`: Define o cabeçalho da página ou de uma seção.
2. `<nav>`: Contém os principais links de navegação do site.
3. `<main>`: Engloba o conteúdo principal da página.
4. `<article>`: Representa um conteúdo independente e autocontido.
5. `<section>`: Define uma seção genérica de conteúdo.
6. `<aside>`: Contém conteúdo relacionado, mas separado do conteúdo principal.
7. `<footer>`: Define o rodapé da página ou de uma seção.
8. `<figure>`: Define conteúdo relacionado a imagem ou vídeo.
9. `<picture>`: Define várias fontes para um conteúdo de mídia.

### Exemplo de Estrutura

```html
<body>
    <header>
        <h1>Meu Site</h1>
        <nav>
            <ul>
                <li><a href="#home">Home</a></li>
                <li><a href="#sobre">Sobre</a></li>
                <li><a href="#contato">Contato</a></li>
            </ul>
        </nav>
    </header>
    <main>
        <article>
            <h2>Título do Artigo</h2>
            <p>Conteúdo do artigo...</p>
        </article>
        <section>
            <h2>Seção de Conteúdo</h2>
            <p>Conteúdo da seção...</p>
        </section>
        <aside>
            <h3>Conteúdo Relacionado</h3>
            <p>Informações adicionais...</p>
        </aside>
    </main>
    <footer>
        <p>© 2023 Meu Site. Todos os direitos reservados.</p>
    </footer>
</body>
```

Usar essas tags semânticas ajuda a melhorar a acessibilidade, SEO e a manutenção do código, tornando a estrutura do site mais clara e significativa.

### Referências

- [Learn HTML Free – Basic HTML Codes for Beginners](https://www.websiteplanet.com/blog/html-guide-beginners/)
- [🎓Curso HTML5 DIO](https://academiapme-my.sharepoint.com/:p:/g/personal/renato_dio_me/EZyg_wTP-VpGvglNScTbgKwBO861jGo0EIsOR8pAxt97-A?rtime=Phk7Od_U3Eg)
- [📃Estrutura HTML5 - MDN](https://developer.mozilla.org/pt-BR/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure)
- [📁github.com/jocile/webdesigner](https://github.com/jocile/webdesigner)
- [📄HTML5 Differences from HTML4](https://www.w3.org/TR/html5-diff/)
