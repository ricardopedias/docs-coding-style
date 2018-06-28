# HTML - Meta Informations

* [Principal](readme.md)
* [Índice HTML](html.md)

As técnicas de SEO (Search Engine Optimization) são abrangentes e envolvem, além da programação, a forma como as informações são publicadas na internet. Artigos e textos bem elaborados somados às tags e atributos semanticamente corretos resultam numa maior exposição e pontuação nos mecanismos de busca, em especial no Google.

Uma parte importante do SEO é a adição de informações que expliquem de forma mais direta aos mecanimsos de busca sobre o que se trata a página HTML. Isso é feito através de meta informações.

Este documento não tem o objetivo de explicar sobre SEO, mas definir um parâmetro para aplicação das tags e atributos semanticamente corretos.


# 1. Declaração para indexação

**DEVE-SE** sempre adicionar a tag meta configurando como a página deve ser indexada.

```html
<meta name="robots" content="index, follow">
```

# 2. Títulos, descrições e palavras-chave

**DEVE-SE** tentar escrever títulos com no máximo 55 caracteres. Mais do que isso poderá será ignorado pelo Google;

**DEVE-SE** tentar escrever descrições de no máximo 155 caracteres. Mais do que isso poderá será ignorado pelo Google;

**SAIBA** que Google [ignora as tags `<meta name="keywords">` para a indexação de páginas](http://googlewebmastercentral.blogspot.in/2009/09/google-does-not-use-keywords-meta-tag.html). Mas você pode utilizá-las mesmo assim.


Mais informações sobre a limitação de caracteres em titulos e descrições em:

* [https://moz.com/blog/new-title-tag-guidelines-preview-tool](https://moz.com/blog/new-title-tag-guidelines-preview-tool)
* [http://www.sagerock.com/blog/title-tag-meta-description-length](http://www.sagerock.com/blog/title-tag-meta-description-length)
* [http://www.swellpath.com/2014/05/update-new-title-tag-meta-description-character-lengths](http://www.swellpath.com/2014/05/update-new-title-tag-meta-description-character-lengths)


# 3. Os tipos de meta informações

Existem vários tipos de meta informações que podem ser usadas em uma página HTML. Existem metadados exclusivos para o navegadores (Internet Explorer, Google Chrome), para leitores de tela não convencionais e até dispositivos móveis (Apple, Microsoft, etc).

Este documento irá abordar as mais importantes no contexto da SEO, ou seja, que forneçam maior resultado na exposição e divulgação das páginas HTML.
Abaixo, uma lista de tipos de metadados por ordem de importância:

* 1. Nativos: são meta informações padrões do HTML5, que podem ser adicionadas dentro da tag `<head>` do documento;
* 2. Microdatas: são meta informações e atributos que aproveitam o conteúdo já existente nas tags, transformando-os em valores de metadados;
* 3. Opengraph: são meta informações que podem ser adicionadas no documento HTML a fim de compartilhar estes dados nas redes sociais;


# 4. Usando meta informações

## 4.1. Metadados Nativos

As meta informações nativas do HTML não precisam de nenhuma configuração, basta adicioná-las na tag `<head>` do documneto html.
No exemplo abaixo, três meta informações são adicionadas: title, meta e link.

```html
<!DOCTYPE html>
<html>
    <head>

        <title>Cidade Jardim</title>
        <meta name="description" content="O site mais legal do bairro">
        <link rel="canonical" href="http://www.cidadejardim.com.br/">
        <!-- outros metadados -->
        <!-- outros metadados -->

    </head>

    <body>
        <!-- mais código html -->
    </body>
</html>
```

## 4.2. Microdatas

Depois dos metadados nativos, as microdatas são as mais importantes, justamente por terem sido assumidas e apoiadas pelo Google.

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


## 4.3. OpenGraph metadados

Por último na classificação dos três tipos mais importantes se encontra o OpenGraph, desenvolvido pela equipe do Facebook. 
Embora também possam ser analizados pelos motores de busca, o opengraph contém metadados usados principalmente para que as informações de uma página HTML seja interpretada por redes sociais que compartilhem conteúdo da internet, como o Facebook ou o Twitter, por exemplo.

Quando um usuário do facebook compartilha o URL de uma página que contém metadados opengraph, o facebook é notificado sobre qual título, descrição e imagem usar para formatar o Post do usuário na timeline da rede social.

Para essas informações sejam identificadas pelas redes sociais, é preciso declarar que o documento HTML contém metadados opengraph, adicionando ao container `<html>` o atributo ***"prefix"***, que deve conter um prefixos seguido do tipo do escopo ao qual a página HTML pertence.


Sem Open Graph:

```html
<!DOCTYPE html>
<html>
    <head>

        <title>Cidade Jardim</title>
        <meta name="description" content="O site mais legal do bairro">
        <link rel="canonical" href="http://www.cidadejardim.com.br/">
        <!-- outros metadados -->
        <!-- outros metadados -->

    </head>

    <body>
        <!-- mais código html -->
    </body>
</html>
```

Com Open Graph para Facebook:

```html
<!DOCTYPE html>
<html prefix="og: http://ogp.me/ns/website#">
    <head>

        <!-- metadados nativos -->
        <title>Cidade Jardim</title>
        <meta name="description" content="O site mais legal do bairro">
        <link rel="canonical" href="http://www.cidadejardim.com.br/">

        <!-- metadados opengraph -->
        <meta property="og:type" content="website">
        <meta property="og:title" content="Cidade Jardim">
        <meta property="og:description" content="O site mais legal do bairro">
        <meta property="og:url" content="http://www.cidadejardim.com.br/">
        <meta property="og:image" content="http://www.cidadejardim.com.br/logo.png">
        
        <!-- outros metadados -->
        <!-- outros metadados -->

    </head>

    <body>
        <!-- mais código html -->
    </body>
</html>
```

Com Open Graph para o Twitter

```html
<!DOCTYPE html>
<html prefix="og: http://ogp.me/ns/website#">
    <head>

        <!-- metadados nativos -->
        <title>Cidade Jardim</title>
        <meta name="description" content="O site mais legal do bairro">
        <link rel="canonical" href="http://www.cidadejardim.com.br/">

        <!-- metadados somente do twitter -->
        <meta name="twitter:card" content="summary">
        <meta name="twitter:site" content="@cidadejardim">
        <meta name="twitter:creator" content="@ricardopereira">
        <!-- metatados compartilhados: facebook + twitter -->
        <meta property="og:type" content="website">
        <meta property="og:title" content="Cidade Jardim">
        <meta property="og:description" content="O site mais legal do bairro">
        <meta property="og:url" content="http://www.cidadejardim.com.br/">
        <meta property="og:image" content="http://www.cidadejardim.com.br/logo.png">

        <!-- outros metadados -->
        <!-- outros metadados -->

    </head>

    <body>
        <!-- mais código html -->
    </body>
</html>
```

Para conhecer todos os tipos de escopo disponíveis, acesse [http://ogp.me](http://ogp.me/).
Para descobrir os metadados opengraph suportados pelo twitter acesse [https://developer.twitter.com](https://developer.twitter.com/en/docs/tweets/optimize-with-cards/guides/getting-started.html).

Para testar as tags do opengraph você pode usar o [Debugger do Facebook](https://developers.facebook.com/tools/debug/) ou a [Ferramenta de Testes do Google](https://search.google.com/structured-data/testing-tool).



# 5. A lista de metadados

Abaixo está organizada uma lista de tags para serem utilizadas no container `<head>` dos documentos html.
A lista é classificada por parâmetros, sempre exibindo os três tipos de metadados:

# 5.1. Título

| Tipo         | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       | `<title>Homem Aranha Home Page</title>`                                      |
| Microdata    | `<meta itemprop="name" content="Homem Aranha Home Page">`                    |
| Opengraph    | `<meta property="og:title" content="Homem Aranha Home Page"`                 |

# 5.2. Descrição

| Tipo         | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       | `<meta name="description" content="Site do Amigo da vizinhança">`            |
| Microdata    | `<meta itemprop="description" content="Site do Amigo da vizinhança">`        |
| Opengraph    | `<meta property="og:description" content="Site do Amigo da vizinhança">`     |









## 2.1. Dados para Homepage

| Informação       | HTML                                                                         |
|:----------------:|:-----------------------------------------------------------------------------|
| Namespace        | `<!DOCTYPE html>`                                                            |
| Título           | `<title>Home Aranha</title>`                                                 |
| Descrição        | `<meta name="description" content="Site do Amigo da vizinhança">`            |
| Url              | `<link rel="canonical" href="http://www.spidey.com">`                        |
| Imagem           |                                                                              |
| Autor            | `<meta name="author" content="https://rpdesignerfly.github.io">`             |
| Autor            | `<link rel="author" href="https://rpdesignerfly.github.io">`                 |


| Informação       | Microdata                                                                    |
|:----------------:|:-----------------------------------------------------------------------------| 
| Namespace        | `<head itemscope itemtype="http://schema.org/WebPage">`                      |
| Título           | `<meta itemprop="name" content="Fale com Home Aranha">`                      |
| Descrição        | `<meta itemprop="description" content="Amigo da vizinhança">`                |
| Url              | `<meta itemprop="url" content="http://www.spidey.com/contato">`              |
| Imagem           | `<meta itemprop="image" content="http://www.spidey.com/logo.png">`           |
| Autor            | `<meta name="author" content="https://rpdesignerfly.github.io">`             |

| Informação       | Opengraph                                                                    |
|:----------------:|:-----------------------------------------------------------------------------|
| Namespace        | `<html prefix="og: http://ogp.me/ns/website#">`                              |
| Título           | `<meta property="og:title" content="Fale com Home Aranha">`                  |
| Descrição        | `<meta property="og:description" content="Amigo da vizinhança">`             |
| Url              | `<meta property="og:url" content="http://www.spidey.com/contato">`           |
| Imagem           | `<meta property="og:image" content="http://www.spidey.com/logo.png">`        |
| Autor            | `<meta property="article:author" content="https://rpdesignerfly.github.io">` |


## 2.1. Dados para um Artigo

| Informação       | HTML                                                                       |
|:----------------:|:--------------------------------------------------------------------------:|
| Título           | `<title>Fale com Home Aranha</title>`                                      |
| Descrição        | `<meta name="description" content="Amigo da vizinhança">`                  |
| Url do site      | `<link rel="base" href="http://www.spidey.com">`                           |
| Url da Página    | `<link rel="canonical" href="http://www.spidey.com/contato">`              |
| Imagem da página |                                                                            |
| Url do Autor     | `<meta name="author" content="http://www.fb.com/stanlee">`                 |
| Url do Autor     | `<link rel="author" href="http://www.fb.com/stanlee">`                     |
| Url Editora/Pub  | `<link rel="publisher" href="http://www.fb.com/comiccon">`                 |


| Informação       | Microdata                                                                  |
|:----------------:|:--------------------------------------------------------------------------:|
| Título           | `<meta itemprop="name" content="Fale com Home Aranha">`                    |
| Descrição        | `<meta itemprop="description" content="Amigo da vizinhança">`              |
| Url do site      | ``                                                                         |
| Url da Página    | `<meta itemprop="url" content="http://www.spidey.com/contato">`            |
| Imagem da página | `<meta itemprop="image" content="http://www.spidey.com/logo.png">`         |
| Url do Autor     | `<meta name="author" content="http://www.fb.com/stanlee">`                 |
| Url Editora/Pub  | `<meta name="publisher" content="http://www.fb.com/stanlee">`              |


| Informação       | Opengraph                                                                  |
|:----------------:|:--------------------------------------------------------------------------:|
| Título           | `<meta property="og:title" content="Fale com Home Aranha">`                |
| Descrição        | `<meta property="og:description" content="Amigo da vizinhança">`           |
| Url do site      |                                                                            |
| Url da Página    | `<meta property="og:url" content="http://www.spidey.com/contato">`         |
| Imagem da página | `<meta property="og:image" content="http://www.spidey.com/logo.png">`      |
| Url do Autor     | `<meta property="article:author" content="http://www.fb.com/stanlee">`     |
| Url Editora/Pub  | `<meta property="article:publisher" content="http://www.fb.com/stanlee">`  |




## 2.1. Dados básicos em HTML

No container `<head>` do documneto HTML, adicione:

```html
<title>Cidade Jardim</title>
<meta name="description" content="O site mais legal do bairro">
<link rel="canonical" href="http://www.cidadejardim.com.br/">

```

## 2.2. Dados básicos Microdatas

Na tag `<head>`, ative os atributos para microdatas do tipo *"http://schema.org/WebPage"*:

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
<meta itemprop="name" content="Cidade Jardim">
<meta itemprop="description" content="O site mais legal do bairro">
<meta itemprop="url" content="http://www.cidadejardim.com.br/">
<meta itemprop="image" content="http://www.cidadejardim.com.br/logo.png">
```

## 2.3. Títulos e Descrições em Opengraph

Na tag `<html>`, ative os atributos opengraph do tipo *"http://ogp.me/ns/website"*:


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

<meta property="og:title" content="Cidade Jardim">
<meta property="og:description" content="O site mais legal do bairro">
<meta property="og:url" content="http://www.cidadejardim.com.br/">
<meta property="og:image" content="http://www.cidadejardim.com.br/logo.png">
```

## 2.4. Títulos e Descrições em Twitter Card

Na tag `<html>`, ative os atributos opengraph de qualquer tipo.
Neste exemplo, vamos usar o tipo básico o *"og: http://ogp.me/ns"*:

Sem opengraph:

```html
<html>
```

Com opengraph:

```html
<html prefix="og: http://ogp.me/ns#">
```

Dentro do container `<head>`, adicione:


```html
<meta name="twitter:card" content="summary">
<meta name="twitter:site" content="@nytimesbits">
<meta name="twitter:creator" content="@nickbilton">

<meta property="og:title" content="Cidade Jardim">
<meta property="og:description" content="O site mais legal do bairro">
<meta property="og:url" content="http://www.cidadejardim.com.br/">
<meta property="og:image" content="http://www.cidadejardim.com.br/logo.png">
```




# 3. Informações de Autoria


```html
<meta name="author" content="www.fb.com/santabrancaonline">
```





# 3. OpenGraph

| Tipo de Página    | Namespace Opengraph                             |
|:-----------------:|:-----------------------------------------------:|
| Homepage          | `<html prefix="og: http://ogp.me/ns/website#">` |
| Página de Música  | `<html prefix="og: http://ogp.me/ns/music#">`   |
| Página de Vídeo   | `<html prefix="og: http://ogp.me/ns/video#">`   |
| Artigo/Postagem   | `<html prefix="og: http://ogp.me/ns/article#">` |
| Livro             | `<html prefix="og: http://ogp.me/ns/book#">`    |
| Perfil            | `<html prefix="og: http://ogp.me/ns/profile#">` |
| Perfil            | `<html prefix="og: http://ogp.me/ns/profile#">` |








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
