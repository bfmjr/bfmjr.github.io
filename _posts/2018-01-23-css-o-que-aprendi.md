---
layout: post
title: "CSS - o que aprendi"
date: 2018-01-23 12:52:53
image: '/assets/img/'
description: 'Algumas coisas que aprendi sobre css.'
main-class: 'css'
color:  
tags:
    - 'css'
categories:
    - 'css'
twitter_text: 'Algumas coisas que aprendi sobre css.'
introduction: 'Algumas coisas que aprendi sobre css.'
---

Antes de falar sobre o assunto principal, vou abrir um parênteses.

Quando você está iniciando na carreira, aprendendo css, você não se preocupa se está escrevendo da melhor forma, apenas foca em aprender. Mais em um determinado momento da sua carreira, não sei de onde, vem um chamado, onde você começa a prestar mais atenção em como escreve, em metodologias, em performance.

## Classes x IDs

Essa foi uma das primeiras mudanças que eu tive desde que eu comecei a escrever css. Foi bastante estranho parar de usar `ids` e começar a usar classes. No primeiro momento foi estranho, pois quando você usa `ids`, todo o seu css fica isolado, e com classe, se você não tomar cuidado pode sobrescrever o estilo em mais de um lugar.

## Especificidade

Quem nunca fez aquele seletor bonito, com várias casas de elementos:

```css
.meu-elemento article p a{}
```

Não é errado que seja errado isso, mais dessa forma você implica na performance do css, pois os browsers leem os css de trás para frente, usando como exemplo o trecho acima, a leitura começaria de encontrar todos os `a` da página, verificar se eles estão dentro de um `p`, depois se estão dentro de um `article` e por fim se estão dentro da classe `meu-elemento`. 

Melhorando o trecho de exemplo, poderia ser colocado uma classe no `article` e estilizar todos os links que estão dentro desse elemento. Dessa forma melhorando a performance do seu css.

```css
.meu-article a{}
```

Eu poderia falar, se você tem um site pequeno não se importe com isso, mas você pode diminuir a especificidade do seu css independente do tamanho do projeto, mesmo que seja o site da sua vizinha que vende bolo ou o site de uma grande marca que você esteja desenvolvendo, mantenha o mesmo mindset. Evite o máximo estilizar diretamente o elemento, prefira usar classes.

## Metodologia: BEM

Essa foi uma grande mudança de como eu escrevia as classes do meu css, nome de classe muitas vezes ou sempre, não tinha relação com o elemento pai, o que acaba prejudicando a manutenção futura. Eu particularmente gosto bastante do BEM, pois você separa de forma organizada, B = Block, E = Element, M = Modifier, ou seja, Blocos, Elementos e Modificador.

```css
/* meu-article principal */
.meu-article{
    display: flex;
    width: 400px;
}

/* Uma versão maior do meu-article */
.meu-article--big{
    display: flex;
    width: 600px;
}

/* Botão que faz parte do elemento meu-article */
.meu-article--btn{
    background-color: red;
    font-size: 20px;
}
```

Existem várias metodologias de css, cada uma resolve o problema de uma forma, você só precisa analisar se ela se encaixa no seu projeto. Você pode até mesmo criar a sua metodologia, usando um pouco de cada uma existente. O que vale é manter a consistência do seu projeto.

## Escrita

Além da metodologia, fiquei procurando alguns padrões de escrita dessa forma mantendo o css escrito de forma que fique padronizado e ajuda na manutenção. Acabei encontrando o idiomatic-css, onde possui alguns regras para escrever css de forma consistente e idiomática.


## Pré-processadores

Eles são uma mão na roda, tenho que salientar isso. Hoje eu conheço Stylus e SASS, durante o dia a dia usou mais o SASS, pois ele foi adotado pela equipe que trabalho. Fora que tanto o Stylus e SASS possuem syntax bem legais, economizando chaves no caso do SASS e no Stylus alem das chaves economizas os dois pontos (:) entre propriedade e valor. Alinhando as declarações com tabs, que na minha opinião fica bem mais claro, mais sempre mantando o limite máximo de 3 leveis para não ficar um hadouken no código.


### Finalizando

Consegui aprender bastante coisa sobre css, ainda falta muito, mais como eu disse, um momento na sua carreira, você vai sentir a necessidade de procurar maneiras, metodologias, padrões que melhorem a sua escrita css. Abaixo vou deixar alguns livros legais, que são sobre css ou tem um capitulo sobre. Valeu \o/

[CSS Eficiente](https://www.casadocodigo.com.br/products/livro-css-eficiente)

[Guia Front-End](https://www.casadocodigo.com.br/products/livro-guia-frontend)

[A Web Mobile](https://www.casadocodigo.com.br/products/livro-web-mobile)

[Web Design Responsivo](https://www.casadocodigo.com.br/products/livro-web-design-responsivo)

## Referências

[Idiomatic-CSS](https://github.com/necolas/idiomatic-css)

[SASS](http://sass-lang.com/)

[Stylus](http://stylus-lang.com/)

[BEM](http://getbem.com/introduction/)  