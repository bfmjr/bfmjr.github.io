---
layout: post
title: "Templates com Handlebars.JS"
date: 2017-09-03 17:05:35
image: '/assets/img/'
description: 'Usando templates com HandlebarsJS.'
main-class: 'js'
color: '#D6BA32'
tags:
    - handlebars
    - js
categories:
    - 'O que aprendi'
twitter_text: 'Usando templates com HandlebarsJS.'
introduction: 'Usando templates com HandlebarsJS.'
---
Essa seja uma série de posts, onde mostro onde apliquei o que aprendi. Espero que goste.

## Handlebars

Reescrevendo uma aplicação, cheguei a um dilema, html no js. Bom, quem nunca fez isso, que atire a primeira pedra.

``` js

    var template   = '<div class="produto produto-'+ id +'">';
        template  += '<h1>'+ titulo +'</h1>';
        template  += '<img src="'+ img +'" alt="'+ titulo +'">';
        template  += '<p>'+ descricao +'</p>';
        template  += '<a href="'+ url +'">Ver Produto</a>';
        template  += '</div>';

 ```

Isso em uma condição boa, imagina casos mais complexo, onde incluem variação dependendo do retorno. Fica impossível ser entendido de forma rápida, certamente terá uma perda de tempo para entender. É nesse momento que entra o [Handlebars](http://handlebarsjs.com/) um script de template bem simples e semântico. Para começar a usar é bem simples.

## Criando o template

Vamos criar um template usando o exemplo acima.

```html
    {% raw %}
    <script id="produtoTemplate" type="text/x-handlebars-template">
        <div class="produto produto-{{id}}">
            <h1>{{titulo}}</h1>
            <img src="{{img}}" alt="{{titulo}}">
            <p>{{descricao}}</p>
            <a href="{{url}}"> Ver Produto </a>
        </div>
    </script>
    {% endraw %}
```

Dessa forma fica legível e de fácil entendimento, para manutenção é uma beleza. :)

## Usando template

Primeiro será necessário acessar o template e compilar para o Handlebars:


```js
    // Bem simples, acessa o template no html e compila através do método compile do Handlebars
    var source = $('produtoTemplate').html(),
        template  = Handlebars.compile( source );
```

Agora é so usar:

```js

    // Objeto do Produto
    var produtoInfo = {
        id : 1,
        titulo : 'Produto Handlebars',
        img : 'https://unsplash.it/150/?random',
        descricao : 'Meu primeiro template com Handlebars',
        url : '#'
    },
    // Adicionando as informações do produto ao template
    produto = template( produtoInfo );

    // Adicionando o template com as informações no HTML
    $('.produtos-listagem').append( produto )

```

## Mais

É possível adicionar condições no template, assim podendo modifica-lo quando necessário.

```html

    <script id="produtoTemplate" type="text/x-handlebars-template">
        {% raw %}
        <div class="produto produto-{{id}}">
        <!-- Caso promoção retorno true, a div com texto promocional é adicionada -->
            {{#if promocao}}
                <div class="promocao">20% Off</div>
            {{/if}}
            <h1>{{titulo}}</h1>
            <img src="{{img}}" alt="{{titulo}}">
            <p>{{descricao}}</p>
            <a href="{{url}}"> Ver Produto </a>
        </div>
        {% endraw %}
    </script>
```


## Finalizando

Abaixo tem um exemplo funcional. Espero que tenha gostado do post.

<p data-height="455" data-theme-id="dark" data-slug-hash="dzQNEz" data-default-tab="js,result" data-user="bfmjr" data-embed-version="2" data-pen-title="O que eu aprendi: Handlebars.js" data-preview="true" class="codepen">See the Pen <a href="https://codepen.io/bfmjr/pen/dzQNEz/">O que eu aprendi: Handlebars.js</a> by Bomfim Jr (<a href="https://codepen.io/bfmjr">@bfmjr</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

Qualquer dúvida ou sugestçao é só comentar xD