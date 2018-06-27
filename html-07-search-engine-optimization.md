# HTML - Search Engine Optimization

* [Principal](readme.md)
* [Índice HTML](html.md)

As técnicas de SEO (Search Engine Optimization) são abrangentes e envolvem, além da programação, a forma como as informações são publicadas na internet. Artigos e textos bem elaborados somados às tags e atributos semanticamente corretos resultam numa maior exposição e pontuação nos mecanismos de busca, em especial no Google.

Este documento não tem o objetivo de explicar tudo sobre SEO, mas definir um parâmetro para aplicação das tags e atributos semanticamente corretos.


# 1. Declaração para indexação

```html
<meta name="robots" content="index, follow">
```

# 2. Títulos e Descrições


**DEVE-SE** tentar escrever títulos com no máximo 55 caracteres. Mais do que isso poderá será ignorado pelo Google;

**DEVE-SE** tentar escrever descrições de no máximo 155 caracteres. Mais do que isso poderá será ignorado pelo Google;

**SAIBA** que Google [ignora as tags `<meta name="keywords">` para a indexação de páginas](http://googlewebmastercentral.blogspot.in/2009/09/google-does-not-use-keywords-meta-tag.html). Mas você pode utilizá-las mesmo assim.


Mais informações sobre a limitação de caaracteres em titulos e descrições em:

* [https://moz.com/blog/new-title-tag-guidelines-preview-tool](https://moz.com/blog/new-title-tag-guidelines-preview-tool)
* [http://www.sagerock.com/blog/title-tag-meta-description-length](http://www.sagerock.com/blog/title-tag-meta-description-length)
* [http://www.swellpath.com/2014/05/update-new-title-tag-meta-description-character-lengths](http://www.swellpath.com/2014/05/update-new-title-tag-meta-description-character-lengths)


## 2.1. Títulos e Descrições em HTML

No container `<head>` do documneto HTML, adicione:

```html
<title>CGNow Treinamentos</title>
<meta name="description" content="Os melhores e mais completos cursos de Blender 3D e Ilustração do mercado. Cursos online 100% em vídeo aulas, com suporte especializado!">

```

## 2.2. Títulos e Descrições em Microdatas

Na tag `<head>`, ative os atributos para microdatas do tipo *"WebPage"*:

Sem microdata:

```html
<head>
```

Com microdata:

```html
<head itemscope itemtype="http://schema.org/WebPage">
```

Dentro do container `<head itemscope itemtype="http://schema.org/WebPage">`, adicione:

```html
<meta itemprop="name" content="CGNow Treinamentos - Cursos de Computação Gráfica, Blender e Ilustração">
<meta itemprop="description" content="Os melhores e mais completos cursos de Blender 3D e Ilustração do mercado. Cursos online 100% em vídeo aulas, com suporte especializado!">
```

## 2.3. Títulos e Descrições em Opengraph

Na tag `<html>`, ative os atributos opengraph do tipo apropriado. Abaixo uma lista de namespaces e sua aplicação:


| Tipo de Página    | Namespace Opengraph                             |
|:-----------------:|:-----------------------------------------------:|
| Homepage          | `<html prefix="og: http://ogp.me/ns/website#">` |
| Página de Música  | `<html prefix="og: http://ogp.me/ns/music#">`   |
| Página de Vídeo   | `<html prefix="og: http://ogp.me/ns/video#">`   |
| Artigo/Postagem   | `<html prefix="og: http://ogp.me/ns/article#">` |
| Livro             | `<html prefix="og: http://ogp.me/ns/book#">`    |
| Perfil            | `<html prefix="og: http://ogp.me/ns/profile#">` |
| Perfil            | `<html prefix="og: http://ogp.me/ns/profile#">` |



Sem opengraph:

```html
<html>
```

Com opengraph:

```html
<html prefix="og: http://ogp.me/ns/website#">
```

Dentro do container `<head>`, adicione:

```html
<meta property="og:type" content="website">
<meta property="og:title" content="CGNow Treinamentos - Cursos de Computação Gráfica, Blender e Ilustração">
<meta property="og:description" content="Os melhores e mais completos cursos de Blender 3D e Ilustração do mercado. Cursos online 100% em vídeo aulas, com suporte especializado!">
```

## 2.4. Títulos e Descrições em Twitter Card

```html
<meta name="twitter:card" content="summary" />
<meta name="twitter:site" content="@nytimesbits" />
<meta name="twitter:creator" content="@nickbilton" />
<meta property="og:url" content="http://bits.blogs.nytimes.com/2011/12/08/a-twitter-for-my-sister/" />
<meta property="og:title" content="A Twitter for My Sister" />
<meta property="og:description" content="In the early days, Twitter grew so quickly that it was almost impossible to add new features because engineers spent their time trying to keep the rocket ship from stalling." />
<meta property="og:image" content="http://graphics8.nytimes.com/images/2011/12/08/technology/bits-newtwitter/bits-newtwitter-tmagArticle.jpg" />
```

# 3. Informações de Autoria


```html
<meta name="author" content="www.fb.com/santabrancaonline">
```



# 4. Microdatas

Os atributos especiais chamados de ***"microdatas"*** são uma forma de classificar os valores já existentes em uma página html, atrelando-os a definições específicas para que os mecanismos de busca possam entender o conteúdo com mais exatidão.

Para as microdatas serem identificadas pelos mecanismos de busca, é preciso declarar que o elemento escolhido servirá como um container de escopo, adicionando a ele o atributo ***"itemscope"***. Uma vez declarado o elemento como escopo de microdatas, é preciso definir o tipo do escopo, adicionando o atributo ***"itemtype"***. 

Sem Microdata:

```html
<section>

  <h1>Walter Elias Disney</h1>
  
  <p><img src="http://www.example.com/disney.jpg" alt="Walter Disney"></p>
  
  <p><a href="https://pt.wikipedia.org/wiki/Walt_Disney">Info</a></p>
  
</section>
```

Com Microdata:

```html
<section itemscope itemtype="http://schema.org/Person">

  <h1 itemprop="name">Walter Elias Disney</h1>
  
  <p><img itemprop="image" src="http://www.example.com/disney.jpg" alt="Walter Disney"></p>
  
  <p><a itemprop="url" href="https://pt.wikipedia.org/wiki/Walt_Disney">Info</a></p>
  
</section>
```

Analizando o exemplo acima, perceba:


| Tag   | Microdata | Origem              | Valor                                     |
|:-----:|:---------:|:-------------------:|:------------------------------------------:
| h1    | name      | conteúdo da tag h1  | Walter Elias Disney                       |
| img   | image     | atributo src        | http://www.example.com/disney.jpg         |
| a     | url       | atributi href       | https://pt.wikipedia.org/wiki/Walt_Disney |



Dependendo da tag, o valor da microdata possui diferentes origens. abaixo, uma tabela de referência para saber onde estão os valores para os atributos *itemprop*:


| Tag           |  Localização do valor            |  Exemplo                                       |
|:-------------:|:--------------------------------:|:----------------------------------------------:|
| `<meta>`      |  Atributo content                | `<meta itemprop="latitude" content="37.4149">` |
| `<audio>`     |  Atributo src                    | `<audio itemprop="contentUrl" src="horse.ogg"></audio>`
| `<embed>`     |  Atributo src                    |	`<embed  itemprop="contentUrl" src="helloworld.swf">`
| `<iframe>`    |  Atributo src                    |	`<iframe itemprop="url" src="/default.php"></iframe>`
| `<img>`       |  Atributo src                    |	`<img itemprop="image" src="/foto.jpg">`
| `<source>`    |  Atributo src                    |	`<audio><source itemprop="contentUrl" src="horse.ogg" type="audio/ogg"></audio>`
| `<video>`     |  Atributo src                    |	`<video itemprop="contentUrl" src="movie.ogg"></video>`
| `<a>`         |  Atributo href                   |	`<a itemprop="url" href="http://google.com">`
| `<area>`      |  Atributo href                   |	`<area itemprop="url" shape="rect" coords="0,0,82,126" href="sun.htm" alt="Sun">`
| `<link>`      |  Atributo href                   |	`<link itemprop="url" rel="stylesheet" type="text/css" href="theme.css">`
| `<object>`    |  Atributo data                   |	`<object itemprop="contentUrl" width="400" height="400" data="helloworld.swf"></object>`
| `<time>`      |  Atributo datetime               |	`<time itemprop="birthday" datetime="2017-02-20">Aniversário</time>`
| Demais Tags   |  Conteúdo textual                |	`<h1 itemprop="name">Ricardo Pereira</h1>`


Para testar as microdatas e descobrir os tipos de escopo disponíveis, acesse [https://schema.org](https://schema.org/docs/full.html). Para exemplos e explicações mais detalhadas acesse [https://diveintohtml5.com.br](https://diveintohtml5.com.br/extensibility.html#what-is-microdata). A especificação se encontra na [W3C](https://www.w3.org/TR/microdata/).




# 1. Cabeçalhos SEO

Atualmente o google aceita como máximo de caracteres para títulos e descrições:
     * Title Tags = 55 characters
     * Meta Description = 115 characters
     * @see http://www.sagerock.com/blog/title-tag-meta-description-length/
     * @see https://moz.com/blog/new-title-tag-guidelines-preview-tool
     * @see http://www.swellpath.com/2014/05/update-new-title-tag-meta-description-character-lengths/
     * 
     * O Google ignora as Meta Keywords para a indexação de páginas
     * @see http://googlewebmastercentral.blogspot.in/2009/09/google-does-not-use-keywords-meta-tag.html
     * 

Abaixo segue uma referência de informações para utilizar nos cabeçalhos de documentos HTML:

```html
<meta name="description" content="Os melhores e mais completos cursos de Blender 3D e Ilustração do mercado. Cursos online 100% em vídeo aulas, com suporte especializado!">
<meta name="robots" content="index, follow">
<meta name="author" content="www.fb.com/santabrancaonline">


<meta itemprop="name" content="CGNow Treinamentos - Cursos de Computação Gráfica, Blender e Ilustração">
<meta itemprop="description" content="Os melhores e mais completos cursos de Blender 3D e Ilustração do mercado. Cursos online 100% em vídeo aulas, com suporte especializado!">
<meta itemprop="image" content="http://www.cgnow.com.br/assets/images/site.png"/>
<meta itemprop="url" content="http://www.cgnow.com.br/"/>


<meta property="og:type" content="article">
<meta property="og:title" content="CGNow Treinamentos - Cursos de Computação Gráfica, Blender e Ilustração">
<meta property="og:site_name" content="CGNow Treinamentos">
<meta property="og:url" content="http://www.cgnow.com.br/">
<meta property="og:description" content="Os melhores e mais completos cursos de Blender 3D e Ilustração do mercado. Cursos online 100% em vídeo aulas, com suporte especializado!">
<meta property="og:locale" content="pt_BR" />
<meta property="og:image" content="http://www.cgnow.com.br/assets/images/site.png"/>
<meta property="article:author" content=""/>
<meta property="article:publisher" content=""/>

<meta name="twitter:card" content="summary_large_image"/>
<meta name="twitter:site" content="@cgnowbr"/>
<meta name="twitter:title" content="CGNow Treinamentos - Cursos de Computação Gráfica, Blender e Ilustração"/>
<meta name="twitter:description" content="Os melhores e mais completos cursos de Blender 3D e Ilustração do mercado. Cursos online 100% em vídeo aulas, com suporte especializado!"/>
<meta name="twitter:image" content="http://www.cgnow.com.br/assets/images/site.png"/>


<link rel="base" href="http://www.cgnow.com.br"/>
<link rel="author" href="https://plus.google.com/+RicardoPereiraDias">
<link rel="publisher" href="https://plus.google.com/+CgnowBr">
<link rel="canonical" href="http://www.cgnow.com.br/">

<link rel="shortcut icon" href="http://www.cgnow.com.br/assets/images/favicon.png">
<link rel="icon" href="http://www.cgnow.com.br/assets/images/icon32.png" type="image/png" sizes="32x32">
<link rel="icon" href="http://www.cgnow.com.br/assets/images/icon76.png" type="image/png" sizes="76x76">
<link rel="icon" href="http://www.cgnow.com.br/assets/images/icon144.png" type="image/png" sizes="144x144">
<link rel="apple-touch-icon" href="http://www.cgnow.com.br/assets/images/icon144.png" type="image/png" sizes="144x144">
<link rel="apple-touch-icon" href="http://www.cgnow.com.br/assets/images/icon76.png" type="image/png" sizes="76x76">
<link rel="apple-touch-icon" href="http://www.cgnow.com.br/assets/images/icon144.png" type="image/png">
```

http://ogp.me/
https://schema.org/docs/full.html
https://developer.twitter.com/en/docs/tweets/optimize-with-cards/guides/getting-started.html
https://diveintohtml5.com.br/extensibility.html#what-is-microdata

[Anterior](html-05-semantica-estrutural.md) ... [Próxima](html-08-implementando-postagens.md)
