---
layout: post
title: "CSS e JS no WordPress - Como adicionar"
date: 2017-09-03 16:50:52
image: '/assets/img/'
description: 'Como incluir JS e CSS de forma correta e reaproveitável.'
main-class: 'wp'
color: '#464646'
tags: 
    - 'wordpress'
    - 'php'
categories:
    - 'O que aprendi'
twitter_text: 'Como incluir JS e CSS de forma correta e reaproveitável.'
introduction: 'Como incluir JS e CSS de forma correta e reaproveitável.'
---

Mais um post da série "O que aprendi", dessa vez vou mostrar como registar e adicionar CSS e JS no WordPress.

## JS

Para registar js no seu tema, usa-se a função `wp_register_script()`, que tem a responsabildiade de registar no seu tema. A função `wp_enqueue_script()` registar e adiciona o script na fila de carregamento, ou seja, tem função dupla. Ambas as funções possuem os mesmos paramentos.


### Parametros

* **$handle**: nome do script, obrigatório;
* **$src**: url do script, podendo ser a url completa, para casos externos, ou caminho relativo a pasta do WordPress, podendo concatenar com o caminho para o seu tema, obrigatório;
* **$deps**: scripts de dependencia em array, opicional;
* **$ver**: versão do script, podendo ser bool, string ou null;
* **$in_footer**: recebe valor bool, caso true, o script será carregado no rodapé, valor padrão false, assim carregando na tag head.

### Colocando em prática

Vamos usar um exemplo simples. Suponha que você tem um slide apenas na home do seu site, não tem a necessidade de carregar esse script nas páginas internas. Usando a função `wp_register_script()`, vou registar o Slick:


```php
wp_register_script('Slick', get_template_directory_uri() . '/assets/js/slick.min.js', array('jquery'), '1.0', true );
```

No código acima, registrei o script Slick, que está na pagina do meu tema, por esse motivo, eu concatenei a função `get_template_directory_uri()` para ter dinâmicamente a url do meu tema, como dependencia coloquei o jQuery, a versão 1.0, e true para o script ser carregado no rodapé.

Para adicionar o Slick a fila, uso a função `wp_enqueue_script()`, dentro de um condicional para carregar apenas na home:

```php
function loadFiles() {

    wp_register_script('Slick', get_template_directory_uri() . '/assets/js/slick.min.js', array('jquery'), '1.0', true );

    if(is_front_page()):
        wp_enqueue_script( 'Slick' );
    endif;
}
add_action( 'wp_enqueue_scripts', 'loadFiles' );
```

## CSS

No css é feita da mesma forma. Usa-se a função `wp_register_style()` para registar e a função `wp_enqueue_style()` para adicionar a fila de carregamento, os quatro primeiros paramentros são iguais a função dos scripts, o que muda é o ultimo parametro.

### Parametros

* **$handle**: nome do script, obrigatório;
* **$src**: caminho do script, podendo ser a url completa, para casos externos, ou, caminho relativo a pasta do WordPress, podendo concatenar com o caminho para o seu tema, obrigatório;
* **$deps**: scripts de dependencia em array, opicional;
* **$ver**: versão do script, podendo ser bool, string ou null, opcional;
* **$media**: recebe uma string especificando a media do css, 'all', 'scree', 'print', por exemplo, opcional.


### Colocando em prática

Continuando com o exemplo do slide, vou registrar o css, usando a função `wp_register_style()`e adicionar a fila com `wp_enqueue_style()`.

``` php
wp_register_style('SlickCSS', get_template_directory_uri() . '/assets/css/slick.min.css', array(), '1.0', 'all' );
```

Usando o mesmo condicional usado para o js, vou adicionar a fila o css do slide:

``` php
function loadFiles() {
    
    wp_register_script('Slick', get_template_directory_uri() . '/assets/js/slick.min.js', array('jquery'), '1.0', true );
    wp_register_style('SlickCSS', get_template_directory_uri() . '/assets/css/slick.min.css', array(), '1.0', 'all' );

    if(is_front_page()):
        // Adição a fila de JS
        wp_enqueue_script( 'Slick' );
        // Adição a fila de CSS
        wp_enqueue_style( 'SlickCSS' );
    endif;
}
add_action( 'wp_enqueue_scripts', 'loadFiles' );
```

## Finalizando

Usando a função de registro os seus arquivos de css e js ficam disponiveis para serem adicionados a qualquer momento no template, dessa forma vocÊ tem o controle de onde eles vão ser carregados e quais as suas dependências, assim evitando problemas de código. Juntando as funções de registo e condicionais do WordPress, é possivel adicionar os scritps por template de paginas, categorias, entre outras possibilidades. Para saber mais você pode acessar [Developer Wordpress](https://developer.wordpress.org/reference/).

Por hoje é isso, qualquer dúvida ou sugestão, só comentar. Valeu!
