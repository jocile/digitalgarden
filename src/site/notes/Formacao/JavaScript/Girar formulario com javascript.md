---
{"dg-publish":true,"permalink":"/formacao/java-script/girar-formulario-com-javascript/","metatags":{"description":"Exemplos de animação de formunlário com JavaScript"},"noteIcon":2,"updated":"2026-02-03T22:36:12.723-03:00"}
---

#JavaScript #exercícios 

# Prática formulário girando

A prática de **Controle de Animações 3D** para girar formulários utiliza o JavaScript como um gatilho para alternar estados visuais, permitindo transitar entre duas interfaces (como login e cadastro) como se fossem as faces de um cartão.

Abaixo, detalho as etapas técnicas dessa prática:

## 1. Estrutura de "Cartão" (HTML)

Para que o efeito funcione, é necessário criar uma hierarquia de containers que permita a manipulação tridimensional:

- **Container Principal:** Uma `div` com a classe `.container` que define o espaço da animação.
- **O Cartão (`.card`):** Uma `div` interna que agrupa as duas seções de formulário.
- **Faces do Cartão:** Duas seções HTML (ex: `<section class='signin'>` e `<section class='signup'>`), representando a frente e o verso.

Esta etapa é o fundamento para criar a ilusão de um objeto tridimensional no navegador, permitindo que o usuário alterne entre dois formulários como se estivesse girando um cartão físico.

Abaixo, detalho o passo a passo para montar essa estrutura utilizando o exemplo de login e cadastro apresentado nas fontes:

### Passo a Passo: Estrutura de "Cartão" (HTML)

1. **Criação do Container de Perspectiva:** Inicie criando uma `div` externa (ex: `.container`). Este elemento é vital pois servirá como o "palco" onde a profundidade será definida posteriormente via CSS.
2. **Definição do Elemento Giratório (O Cartão):** Dentro do container, insira uma segunda `div` com a classe `.card`. Este elemento será o responsável por agrupar as duas faces e sofrer a rotação de 180 graus.
3. **Montagem da Face Frontal (Login):** Dentro da `div.card`, crie uma `<section>` com a classe `.signin`. Esta será a primeira face que o usuário verá ao carregar a página.
4. **Montagem da Face Traseira (Cadastro):** Abaixo da seção anterior, ainda dentro da `div.card`, crie outra `<section>` com a classe `.signup`. Esta face ficará posicionada "atrás" da primeira no espaço 3D.
5. **Inclusão de Controles de Alternância:** Em ambos os formulários, adicione links com uma classe específica (ex: `.toggle`). Estes links serão os gatilhos que o JavaScript usará para adicionar a classe de rotação ao cartão.

---

### Exemplo de Código HTML da Estrutura

Conforme as fontes, o código deve ser organizado da seguinte forma para garantir que as seções fiquem empilhadas corretamente para o efeito de giro:

```html
<!-- 1. O container que define o espaço 3D -->
<div class='container'>

    <!-- 2. O cartão que sofrerá a rotação -->
    <div class='card'>

        <!-- 3. Face Frontal: Formulário de Login -->
        <section class='signin'>
            <form>
                <h2>Entrar no site</h2>
                <p>
                    <label for="user_email">E-mail</label>
                    <input type='email' id="user_email">
                </p>
                <p>
                    <label for="user_password">Senha</label>
                    <input type='password' id="user_password">
                </p>
                <button>Enviar!</button>
                <!-- Link para girar para o cadastro -->
                <a href='javascript:;' class='toggle'>Quero me cadastrar</a>
            </form>
        </section>

        <!-- 4. Face Traseira: Formulário de Cadastro -->
        <section class='signup'>
            <form>
                <h2>Cadastre-se agora!</h2>
                <p>
                    <label for="account_email">E-mail</label>
                    <input type='email' id="account_email">
                </p>
                <p>
                    <label for="account_password">Senha</label>
                    <input type='password' id="account_password">
                </p>
                <button>Enviar!</button>
                <!-- Link para girar de volta para o login -->
                <a href='javascript:;' class='toggle'>Já estou cadastrado no site</a>
            </form>
        </section>

    </div> <!-- Fim do .card -->
</div> <!-- Fim do .container -->
```

### Por que esta estrutura é necessária?

- **Empilhamento:** No CSS, as seções serão posicionadas de forma absoluta (`position: absolute`), ficando uma exatamente sobre a outra.
- **Visibilidade:** O uso de elementos separados permite aplicar a propriedade `backface-visibility: hidden`, garantindo que, ao girar, o verso de um formulário não apareça de forma invertida sobre o outro.
- **Contexto 3D:** A `div.card` precisa da propriedade `transform-style: preserve-3d` para que seus filhos (os formulários) também se movam no espaço tridimensional.


## 2. Configuração do Espaço 3D (CSS)

O efeito visual depende de propriedades específicas do CSS3:

- **Perspectiva:** No container principal, aplica-se a propriedade `perspective: 500px;` para criar a ilusão de profundidade. Sem isso, o elemento pareceria apenas achatar e esticar, sem o aspecto de giro real.
- **Preservação do 3D:** O elemento `.card` deve ter `transform-style: preserve-3d;` para garantir que os elementos filhos (os formulários) também se comportem no espaço tridimensional.
- **Visibilidade do Verso:** Aplica-se `backface-visibility: hidden;` às seções dos formulários. Isso torna o verso de cada "face" invisível quando ela está de costas para o usuário, evitando que o texto apareça invertido.
- **Posicionamento Inicial:** A seção de cadastro (`.signup`) deve ser iniciada já rotacionada com `transform: rotateY(180deg);` para ficar "de costas".

Nesta segunda etapa, configuramos o **CSS** para transformar a estrutura HTML em um ambiente tridimensional funcional, permitindo o efeito de profundidade e o giro suave entre as faces.

### Passo a Passo: Configuração do Espaço 3D (CSS)

1. **Definição da Perspectiva:** No elemento pai (`.container`), aplique a propriedade **`perspective`**. Valores em torno de **500px** são ideais para criar a ilusão de profundidade necessária para que os elementos pareçam girar em um eixo no espaço. Sem isso, o giro parecerá um simples achatamento bidimensional.
2. **Preparação do Cartão para o 3D:** No elemento `.card`, utilize **`transform-style: preserve-3d;`**. Esta regra é crucial para que os elementos filhos (os formulários) compartilhem do mesmo contexto tridimensional e acompanhem o movimento do pai.
3. **Suavização do Movimento:** Ainda no `.card`, adicione a propriedade **`transition: transform 1s;`**. Isso garante que, quando a classe de rotação for aplicada, o navegador execute a animação de giro de forma fluida durante um segundo.
4. **Empilhamento e Ocultação das Faces:** Configure as seções internas (`.card section`) com **`position: absolute;`** para que fiquem exatamente uma em cima da outra. Aplique **`backface-visibility: hidden;`** para que o verso de cada formulário fique invisível quando estiver de costas para o usuário, evitando que o conteúdo apareça invertido.
5. **Posicionamento do Verso:** Para que as seções funcionem como as duas faces de um cartão, a seção de cadastro (`.signup`) deve começar "de costas", utilizando **`transform: rotateY(180deg);`**.
6. **Criação do Estado de Giro:** Defina a classe **`.card.flipped`**, que aplicará a rotação de **180 graus** ao cartão inteiro quando ativada pelo JavaScript.

---

### Exemplo de Código CSS da Parte 2

Abaixo está a implementação técnica baseada nas fontes para consolidar o espaço 3D:

```css
/* 1. O palco da animação */
.container {
    height: 300px;
    perspective: 500px; /* Define a profundidade do plano 3D */
    position: relative;
    width: 200px;
}

/* 2. O corpo do cartão que gira */
.card {
    height: 100%;
    position: absolute;
    transform-style: preserve-3d; /* Garante que os filhos fiquem no espaço 3D */
    transition: transform 1s; /* Duração da animação de giro */
    width: 100%;
}

/* 3. Configuração das faces (Login e Cadastro) */
.card section {
    backface-visibility: hidden; /* Esconde o verso invertido */
    background-color: #FFF;
    border-radius: 5px;
    position: absolute; /* Empilha as seções */
    width: 100%;
    height: 100%;
}

/* 4. Colocando o formulário de cadastro de costas */
.signup {
    transform: rotateY(180deg);
}

/* 5. Classe que dispara a rotação total */
.card.flipped {
    transform: rotateY(180deg);
}
```

Nesta configuração, ao adicionar a classe `.flipped` ao elemento `.card`, o formulário que estava na frente gira para trás e desaparece, enquanto o que estava de costas gira para a frente e torna-se visível, criando o efeito de "cartão giratório".

## 3. Alternância de Estados com JavaScript

O JavaScript (utilizando a biblioteca **jQuery**) atua apenas para gerenciar a classe que dispara a animação:

- **Evento de Clique:** Associa-se um evento de clique aos links de alternância (ex: "Quero me cadastrar" ou "Já estou cadastrado").
- **Gatilho Visual (`toggleClass`):** Ao clicar, o JavaScript executa a função `.toggleClass('flipped')` no elemento `.card`.
- **Transição Automática:** No CSS, define-se que quando o `.card` possuir a classe `.flipped`, ele deve rotacionar: `transform: rotateY(180deg);`. Como o cartão possui a propriedade `transition: transform 1s;`, o navegador executa o giro suavemente durante um segundo.

Para concluir a prática de **Controle de Animações 3D**, a terceira parte foca na **Alternância de Estados com JavaScript**. Nesta fase, o código JavaScript atua como o "gatilho" que dispara a animação definida no CSS, permitindo que o usuário interaja com o formulário e veja o "giro" do cartão.

Aqui está o passo a passo detalhado utilizando a biblioteca **jQuery**, conforme recomendado nas fontes:

### Passo a Passo: Alternância de Estados com JavaScript

1. **Carregar a Biblioteca jQuery:** Certifique-se de que o jQuery está referenciado ao final do seu documento HTML (antes do fechamento da tag `</body>`) para garantir que a manipulação do DOM ocorra após o carregamento dos elementos.
2. **Identificar os Gatilhos de Clique:** O JavaScript deve monitorar os cliques nos links de alternância (classe `.toggle` ou links dentro das `sections`) que criamos na estrutura HTML.
3. **Associar o Evento de Clique:** Utilize o método `.on('click', ...)` para capturar a interação do usuário. É importante passar o objeto de evento (`e`) para evitar o comportamento padrão do link, se necessário.
4. **Alternar a Classe `.flipped`:** A função principal do script é selecionar o elemento `.card` e utilizar o método **`.toggleClass('flipped')`**.
    - Se a classe não estiver presente, o jQuery a adiciona (o cartão gira para o verso).
    - Se a classe já estiver presente, o jQuery a remove (o cartão volta para a frente).
5. **Delegar o Trabalho ao Navegador:** Ao alternar a classe, o JavaScript não faz o cálculo da animação; ele apenas muda o estado do elemento. O navegador, ao detectar a nova classe `.flipped`, aplica automaticamente a transição de `rotateY(180deg)` definida no CSS.

---

### Exemplo de Código JavaScript (jQuery)

Baseado no exemplo prático das fontes para transitar entre os formulários de login e cadastro:

```js
// Garante que o código execute após o carregamento da página
jQuery(function($) {

    // 1. Monitora o clique em qualquer link ('a') dentro das seções do formulário
    $('section').on('click', 'a', function(e) {

        // Evita que o link tente navegar para outra página
        e.preventDefault();

        // 2. Seleciona o elemento .card e alterna a classe 'flipped'
        // Isso dispara a transição CSS3 de rotação em 3D
        $('.card').toggleClass('flipped');

    });

});
```

### Por que usar JavaScript para isso?

- **Controle de Interação:** Diferente de efeitos que usam apenas o `:hover` do CSS (que disparam a animação apenas ao passar o mouse), o JavaScript permite que a mudança de estado seja **persistente** após o clique.
- **Simplicidade e Performance:** Ao usar o `toggleClass`, você escreve apenas duas ou três linhas de código e deixa a renderização pesada para o motor gráfico do navegador através do CSS3, o que reduz bugs e melhora a fluidez em comparação com animações feitas puramente em scripts.
- **Encadeamento (Opcional):** Caso você queira executar algo após o fim do giro, pode utilizar o evento de JavaScript `transitionend` (ou `webkitTransitionEnd`), que é disparado exatamente quando a animação de rotação termina.

## Resultado Visual

Ao clicar no link, o JavaScript altera o estado do container. O navegador, interpretando a mudança de classe, aplica a transformação 3D. O formulário que estava na frente gira para trás e desaparece (devido ao `backface-visibility`), enquanto o que estava atrás gira para a frente e torna-se visível, criando uma transição elegante e performática que delega o "trabalho pesado" de renderização ao navegador.
