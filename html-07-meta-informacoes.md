# HTML - Meta Informações

* [Principal](readme.md)
* [Índice HTML](html.md)

As técnicas de SEO (Search Engine Optimization) são abrangentes e envolvem, além da programação, a forma como as informações são publicadas na internet. Artigos e textos bem elaborados somados às tags e atributos semanticamente corretos resultam numa maior exposição e pontuação nos mecanismos de busca, em especial no Google.

Uma parte importante do SEO é a adição de informações que expliquem de forma mais direta aos mecanimsos de busca sobre o que se trata a página HTML. Isso é feito através de meta informações.

Este documento não tem o objetivo de explicar sobre SEO, mas definir um parâmetro para aplicação das tags e atributos semanticamente corretos.


# 1. Regras gerais

**DEVE-SE** sempre adicionar a tag `<meta charset="UTF-8">` para configurar a codificação de caracteres, pois a codificação padrão pode variar entre navegadores;

**DEVE-SE** sempre adicionar a tag `<meta name="robots" content="...">` configurando como os robôs de busca devem se comportar ao visitar o documento HTML;

**DEVE-SE** tentar escrever títulos com no máximo 55 caracteres. Mais do que isso poderá será ignorado pelo Google;

**DEVE-SE** tentar escrever descrições de no máximo 155 caracteres. Mais do que isso poderá será ignorado pelo Google;

**DEVE-SE** tentar escrever todas as palavras chave com no máximo 155 caracteres. Mais do que isso poderá será ignorado pelo Google;

**SAIBA** que o Google [ignora as tags `<meta name="keywords">` para a indexação de páginas](http://googlewebmastercentral.blogspot.in/2009/09/google-does-not-use-keywords-meta-tag.html). Mas você pode utilizá-las mesmo assim, pois as meta keywords ainda podem ajudar a categorizar o conteúdo da sua página.

Mais informações sobre a limitação de caracteres em titulos e descrições em:

* [https://moz.com/blog/new-title-tag-guidelines-preview-tool](https://moz.com/blog/new-title-tag-guidelines-preview-tool)
* [http://www.sagerock.com/blog/title-tag-meta-description-length](http://www.sagerock.com/blog/title-tag-meta-description-length)
* [http://www.swellpath.com/2014/05/update-new-title-tag-meta-description-character-lengths](http://www.swellpath.com/2014/05/update-new-title-tag-meta-description-character-lengths)


# 2. Robôs de Busca

## 2.1. Controlando os robôs de busca

Para determinar como o documento HTML deve ser indexado pelos robôs de busca, deve-se adicionar a tag `<meta name="robots" content="...">` no container `<head>`.

```html
<meta name="robots" content="index,follow">
```

A função desta tag é informar aos robôs de busca se devem indexar o documento HTML ou não.

> Se o objetivo for impedir que os robôs de busca acessem determinadas áreas (áreas inteiras como uma categoria de artigos, por exemplo, `http://www.spidey.com/artigos-ocultos/*`) do seu site, prefira utilizar um arquivo "robots.txt" na raiz do site, pois será mais fácil gerenciar o que deve ou não ser acessado.

A pergunta é: se é possivel gerenciar isso pelo arquivo *"robots.txt"*, porque usar meta informações para isso?

Quando você utiliza pop-ups ou iframes para mostrar o conteúdo do seu site, por exemplo, não é interessante que os robôs de busca indexem essas páginas, afinal, se elas forem acessadas individualmente, não vão significar nada e não trarão visitação relevante ao seu site. Excluir estas páginas da indexação através do arquivo *"robots.txt"* pode ser chato, trabalhoso e fadado a erros, tornando o arquivo extenso. Sendo assim, é mais inteligente e conveniente adicionar meta informações para forçar as diretivas diretamente nas páginas de pop-ups ou iframes.

Se os documentos HTML forem gerados dinamicamente por uma linguagem de servidor (como PHP ou Java), prefira adicionar as meta informações em todos os documentos, mesmo que seu site esteja usando um arquivo *"robots.txt"*.

## 2.2. Configurando o documento HTML

Os valores de configuração podem ser especificados em conjunto, separando as diretivas por vírgulas, ou separadamente, com cada diretiva em uma nova tag meta.

Em conjunto:

```html
<meta name="robots" content="index,follow,noarchive">
```

Separadamente:

```html
<meta name="robots" content="index">
<meta name="robots" content="follow">
<meta name="robots" content="noarchive">
```

A possíveis diretivas para esta meta informação são:

* **noindex**: o robô de busca não deve indexar a página;
* **index**: informa o robô de busca para indexar a página;
* **follow**: mesmo que a página não seja indexada, o robô de busca deve seguir todos os links do documento e efetuar a verificação neles também;
* **nofollow**: informa o robô de busca para não seguir nenhum link do documento;
* **noimageindex**: informa o robô de busca para não indexar nenhuma imagem em uma página;
* **none**: equivalente a usar as diretivas *noindex* e *nofollow* simultaneamente;
* **noarchive**: os robôs de busca não devem mostrar um link em cache para esta página em uma SERP;
* **nocache**: o mesmo que *noarchive*, mas usado apenas pelo *Internet Explorer* e *Firefox*.
* **nosnippet**: informa o robô de busca para não mostrar um trecho desta página (ou seja, meta descrição) desta página em uma SERP;
* **unavailable_after**: informa o robô de busca para não exibir esta página nos resultados da pesquisa após a data/hora especificada. A data/hora precisa ser especificada no formato RFC 850.

Um exemplo de uso da diretiva *unavailable_after*:

```html
<meta name="robots" content="unavailable_after: 10-Jan-1980 10:10:00 UTC">
```

> Nota: se você deseja que o documento seja divulgado, evite usar a opção noarchive, pois isso poderá diminuir a exposição.

## 2.3. Controlando um robô específico

É possivel também especificar estas mesmas informações, restrigindo-as para um robô de busca específico.
Por exemplo, para declarar que apenas o robô *Googlebot* não deve indexar o documento, troque a meta informação *"robots"* pelo user-agent do *Googlebot*:

```html
<meta name="googlebot" content="noindex,nofollow">
```

Abaixo, uma lista com os proncipais robôs de busca e seus respectivos user-agents:

| Nome                  | User Agent                |
|:---:                  |:---:                      |
| Google                | googlebot                 |
| Google News           | googlebot-news            |
| Google Images         | googlebot-image/1.0       |
| Google Video          | googlebot-video/1.0       |
| Google Adsense        | mediapartners-google      |
| Google App Crawler    | adsbot-google-mobile-apps |
| Bing                  | bingbot                   |
| Slurp Bot             | slurp                     |
| Duck Duck Bot         | duckduckbot               |
| Baidu Spider          | baiduspider               |
| Baidu Image Search    | baiduspider-image         |
| Baidu Video Search    | baiduspider-video         |
| Baidu News Search     | baiduspider-news          |
| Baidu Baidu wishlists | baiduspider-favo          |
| Baidu Baidu Union     | baiduspider-cpro          |
| Baidu Business Search | baiduspider-ads           |
| Yandex Bot            | yandexbot                 |
| Facebook External Hit | facebot                   |
| Alexa Crawler         | ia_archiver               |


Para mais informações, visite:

* [Documento de Robôs do Google](https://developers.google.com/search/reference/robots_meta_tag?hl=pt-br)
* [Documento da Mozilla SEO](https://moz.com/learn/seo/robots-meta-directives)


# 3. Usando meta informações

## 3.1 Os tipos de meta informações

Existem vários tipos de meta informações que podem ser usadas em uma página HTML. Existem metadados exclusivos para o navegadores (Internet Explorer, Google Chrome), para leitores de tela não convencionais e até para dispositivos móveis (Samsung, Apple, Microsoft, etc).

Este documento irá abordar as mais importantes no contexto da SEO, ou seja, que forneçam maior resultado na exposição e divulgação das páginas HTML.
Abaixo, uma lista de tipos de metadados por ordem de importância:

1. **Nativos**: são meta informações padrões do HTML5, que podem ser adicionadas dentro da tag `<head>` do documento;
2. **Microdatas**: são meta informações e atributos que aproveitam o conteúdo já existente nas tags, transformando-os em valores de metadados;
3. **Opengraph**: são meta informações que podem ser adicionadas no documento HTML a fim de compartilhar estes dados nas redes sociais;


## 3.2. Metadados Nativos

As meta informações nativas do HTML não precisam de nenhuma configuração, basta adicioná-las na tag `<head>` do documento html.
No exemplo abaixo, cinco meta informações são adicionadas: meta charset, title, meta description, meta keywords e link canonical.


```html
<!DOCTYPE html>
<html>
    <head>

        <meta charset="UTF-8">
        <title>Contato | Homem Aranha Home Page</title>
        <meta name="description" content="Entre em contato com o Amigo da vizinhança">
        <meta name="keywords" content="heroismo, quadrinhos, salvador de velhinhas">
        <link rel="canonical" href="http://www.spidey.com/contato">
        <!-- outros metadados -->
        <!-- outros metadados -->

    </head>

    <body>
        <!-- mais código html -->
    </body>
</html>
```

## 3.3. Microdatas

Depois dos metadados nativos, as microdatas são as mais importantes, justamente por terem sido assumidas e apoiadas pelo Google.

Os atributos especiais chamados de ***microdatas*** são uma forma de classificar os valores já existentes em uma página html, atrelando-os a definições específicas para que os mecanismos de busca possam entender o conteúdo com mais exatidão.

Para as microdatas serem identificadas pelos mecanismos de busca, é preciso declarar que o elemento escolhido servirá como um container de escopo, adicionando a ele o atributo ***itemscope***. Uma vez declarado o elemento como escopo de microdatas, é preciso definir o tipo do escopo, adicionando o atributo ***itemtype***. 

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
|:-------------:|:--------------------------------:|:-----------------------------------------------|
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


## 3.4. OpenGraph metadados

Por último na classificação dos três tipos mais importantes se encontra o OpenGraph, desenvolvido pela equipe do Facebook. 
Embora também possam ser analisados pelos robôs de busca, o opengraph contém metadados usados principalmente para que as informações de uma página HTML seja interpretada por redes sociais que compartilhem conteúdo da internet, como o Facebook ou o Twitter, por exemplo.

Quando um usuário do facebook compartilha o URL de uma página que contém metadados opengraph, o facebook é notificado sobre qual título, descrição e imagem usar para formatar o Post do usuário na timeline da rede social.

Para essas informações sejam identificadas pelas redes sociais, é preciso declarar que o documento HTML contém metadados opengraph, adicionando ao container `<html>` o atributo ***prefix***, que deve conter um prefixo seguido de dois pontos ***:*** e do tipo do escopo ao qual a página HTML pertence.


Sem Open Graph:

```html
<!DOCTYPE html>
<html>
    <head>

        <title>Homem Aranha Home Page</title>
        <meta name="description" content="Site do Amigo da vizinhança">
        <link rel="canonical" href="http://www.spidey.com/">
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
        <title>Homem Aranha Home Page</title>
        <meta name="description" content="Site do Amigo da vizinhança">
        <link rel="canonical" href="http://www.spidey.com/">

        <!-- metadados opengraph -->
        <meta property="og:type" content="website">
        <meta property="og:title" content="Homem Aranha Home Page">
        <meta property="og:description" content="Site do Amigo da vizinhança">
        <meta property="og:url" content="http://www.spidey.com/">
        <meta property="og:image" content="http://www.spidey.com/logo.png">
        
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
        <title>Homem Aranha Home Page</title>
        <meta name="description" content="Site do Amigo da vizinhança">
        <link rel="canonical" href="http://www.spidey.com/">

        <!-- metadados somente do twitter -->
        <meta name="twitter:card" content="summary">
        <meta name="twitter:site" content="@spideymarvel">
        <meta name="twitter:creator" content="@spydeymarvel">
        <!-- metatados compartilhados: facebook + twitter -->
        <meta property="og:type" content="website">
        <meta property="og:title" content="Homem Aranha Home Page">
        <meta property="og:description" content="Site do Amigo da vizinhança">
        <meta property="og:url" content="http://www.spidey.com/">
        <meta property="og:image" content="http://www.spidey.com/logo.png">

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


# 4. Tag head : Referência de meta informações

Abaixo está organizada uma lista de tags para serem utilizadas no container `<head>` dos documentos html.
A lista é classificada por parâmetros, sempre exibindo os três tipos de metadados, quando possuírem uma notação disponível:

## 4.1. Para página inicial


| Namespaces         | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       | `<!DOCTYPE html>` - no topo do documento                                     |
| Microdata    | `<head itemscope itemtype="http://schema.org/WebSite">`                      |
| Opengraph    | `<html prefix="og:http://ogp.me/ns# website: http://ogp.me/ns/website#">`    |

<br>

| Declarações         | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       |                                                                              |
| Microdata    |                                                                              |
| Opengraph    | `<meta property="og:type" content="website">`                                |

<br>

| Idioma         | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       | `<html lang="pt_BR">`                                                        |
| Microdata    | `<meta itemprop="inLanguage" content="pt_BR">`                               |
| Opengraph    | `<meta property="og:locale" content="pt_BR">`                                |

<br>

| Título do Site         | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       | `<title>Site do Homem Aranha</title>`                                        |
| Microdata    | `<meta itemprop="name" content="Site do Homem Aranha">`                      |
| Opengraph    | `<meta property="og:site_name" content="Site do Homem Aranha">`              |

<br>

| Descrição    | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       | `<meta name="description" content="Site do Amigo da vizinhança">`            |
| Microdata    | `<meta itemprop="description" content="Site do Amigo da vizinhança">`        |
| Opengraph    | `<meta property="og:description" content="Site do Amigo da vizinhança">`     |

<br>

| URL do site         | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       | `<link rel="canonical" href="http://www.spidey.com">`                        |
| Microdata    | `<meta itemprop="url" content="http://www.spidey.com/contato">`              |
| Opengraph    | `<meta property="og:url" content="http://www.spidey.com/contato">`           |

<br>

| Imagem do site         | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       |                                                                              |
| Microdata    | `<meta itemprop="image" content="http://www.spidey.com/logo.png">`           |
| Opengraph    | `<meta property="og:image" content="http://www.spidey.com/logo.png">`        |
| Opengraph    | `<meta property="og:image:secure_url" content="https://www.spidey.com/logo.png">` |
| Opengraph    | `<meta property="og:image:width" content="200">`                             |
| Opengraph    | `<meta property="og:image:height" content="200">`                            |
| Opengraph    | `<meta property="og:image:type" content="image/png">`                        |

<br>

| Autor do site         | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       | `<meta name="author" content="https://rpdesignerfly.github.io">`             |
| Nativa       | `<link rel="author" href="https://rpdesignerfly.github.io">`                 |
| Microdata    | `<meta itemprop="author" content="https://rpdesignerfly.github.io">`         |
| Opengraph    |                                                                              |

<br>

| Data de publicação do site         | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       |                                                                              |
| Microdata    | `<meta itemprop="datePublished" content="1972-06-18T01:23:45Z">`             |
| Opengraph    |                                                                              |


## 4.2. Para página de artigo/postagem

| Namespaces        | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       | `<!DOCTYPE html>` - no topo do documento                                     |
| Microdata    | `<head itemscope itemtype="http://schema.org/Article">`                      |
| Opengraph    | `<html prefix="og:http://ogp.me/ns# article:http://ogp.me/ns/article#">`     |

<br>

| Declarações         | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       |                                                                              |
| Microdata    |                                                                              |
| Opengraph    | `<meta property="og:type" content="article">`                                |
| Opengraph    | `<meta name="twitter:card" content="summary">`                               |

<br>

| Idioma        | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       | `<html lang="pt_BR">`                                                        |
| Microdata    | `<meta itemprop="inLanguage" content="pt_BR">`                               |
| Opengraph    | `<meta property="og:locale" content="pt_BR">`                                |

<br>

| Título do Site         | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       |                                                                              |
| Microdata    |                                                                              |
| Opengraph    | `<meta property="og:site_name" content="Site do Homem Aranha">`              |
| Opengraph    | `<meta name="twitter:site" content="@spidey">`                               |

<br>

| Título do Artigo    | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       | `<title>Fluido de Teia - Site do Homem Aranha</title>`                       |
| Microdata    | `<meta itemprop="name" content="Fluido de Teia - Site do Homem Aranha">`     |
| Opengraph    | `<meta property="og:title" content="Fluido de Teia">`                        |

<br>

| Descrição    | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       | `<meta name="description" content="Site do Amigo da vizinhança">`            |
| Microdata    | `<meta itemprop="description" content="Site do Amigo da vizinhança">`        |
| Opengraph    | `<meta property="og:description" content="Site do Amigo da vizinhança">`     |

<br>

| URL do artigo    | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       | `<link rel="canonical" href="http://www.spidey.com/fluido-de-teia">`         |
| Microdata    | `<meta itemprop="url" content="http://www.spidey.com/fluido-de-teia">`       |
| Opengraph    | `<meta property="og:url" content="http://www.spidey.com/fluido-de-teia">`    |

<br>

| Imagem do artigo    | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       |                                                                              |
| Microdata    | `<meta itemprop="image" content="http://www.spidey.com/logo.png">`           |
| Opengraph    | `<meta property="og:image" content="http://www.spidey.com/logo.png">`        |
| Opengraph    | `<meta property="og:image:secure_url" content="https://www.spidey.com/logo.png">` |
| Opengraph    | `<meta property="og:image:width" content="200">`                             |
| Opengraph    | `<meta property="og:image:height" content="200">`                            |
| Opengraph    | `<meta property="og:image:type" content="image/png">`                        |

<br>

| Autor do artigo    | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       | `<meta name="author" content="https://rpdesignerfly.github.io">`             |
| Nativa       | `<link rel="author" href="https://rpdesignerfly.github.io">`                 |
| Microdata    | `<meta itemprop="author" content="https://rpdesignerfly.github.io">`         |
| Opengraph    | `<meta property="article:author" content="https://rpdesignerfly.github.io">` |
| Opengraph    | `<meta name="twitter:creator" content="@rpdesignerfly">`                     |

<br>

| Publicador/Editora do artigo    | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       | `<link rel="publisher" href="http://www.fb.com/comiccon">`                   |
| Microdata    | `<meta itemprop="publisher" content="http://www.fb.com/comiccon">`           |
| Opengraph    | `<meta property="article:publisher" content="http://www.fb.com/comiccon">`   |

<br>

| Data de publicação do artigo    | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       |                                                                              |
| Microdata    | `<meta itemprop="datePublished" content="1972-06-18T01:23:45Z">`             |
| Opengraph    | `<meta property="article:published_time" content="1972-06-18T01:23:45Z">`    |

<br>

| Taxonomia         | Notação                                                                      |
|:------------:|:-----------------------------------------------------------------------------|
| Nativa       |                                                                              |
| Microdata    | `<meta itemprop="keywords" content="superheroi, comics">`                    |
| Opengraph    | `<meta property="article:section" content="front page">`                     |
| Opengraph    | `<meta property="article:tag" content="superheroi, comics">`                 |


## 4.3. Para página de perfil



...

...

...




[Anterior](html-05-semantica-estrutural.md) ... [Próxima](html-08-implementando-postagens.md)
