# HTML

## Sumário

* [PHP](php.md)
* [HTML](html.md)

## Referências externas

* [HTML5 W3C Recommendation](https://www.w3.org/TR/html52/)
* [WHATWG HTML Living Standard](https://html.spec.whatwg.org/)

## 1. Doctype

**DEVE-SE** sempre adicionar a notação *doctype*:

Errado:

```html
<html>
    <!-- mais código html -->
</html>
```

Certo:

```html
<!DOCTYPE html>
<html>
    <!-- mais código html -->
</html>
```

**NÃO DEVE-SE** usar doctypes antigos, pois um doctype não usa mais *DTDs*: 

Errado:

```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN"
      "http://www.w3.org/TR/html4/strict.dtd">
```

Certo:

```html
<!DOCTYPE html>
```

**NÃO DEVE-SE** usar declarações XML:

Errado:

```html
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<!DOCTYPE html>
```

Certo:

```html
<!DOCTYPE html>
```

## 2. O Elemento Root

**DEVE-SE** adicionar o atributo *lang* na tag *html*, pois ele auxilia os leitores de tela na tradução de um documento:

Errado:

```html
<html>
```

Certo:

```html
<html lang="pt-BR">
```

**DEVE-SE** escolher o menor valor possível ao setar o atributo *lang*. Por exemplo, japonês (*ja-JP*) só pode ser usado no japão, então não é necessário adicionar o código do país (*JP*):

Errado:

```html
<html lang="ja-JP">
```

Certo:

```html
<html lang="ja">
```

Já o português é usado no Brasil (*pt-BR*) e em Portugal (*pt-PT*), então é coerente especificar o código do país para o Brasil, mas omitir o de portugal:

Certo:

```html
<html lang="pt"><!-- português de Portugal -->
```

```html
<html lang="pt-BR"><!-- português do Brasil -->
```

**NÃO DEVE-SE** nunca omitir as tags de fechamento:

Errado:

```html
<html lang="pt-BR">
    <!-- mais código html -->
```

Certo:

```html
<html lang="pt-BR">
    <!-- mais código html -->
</html>
```

## 3. Estrutura padrão

**NÃO DEVE-SE** alterar a estrutura padrão do HTML em nenhuma hipótese. A estrutura padrão é composta por dois containers (*head* e *body*) e novas tags devem ser acomodadas dentro do container correto.

```html
<html lang="pt-BR">

    <head>
        <!-- mais código html -->
    </head>

    <body>
        <!-- mais código html -->
    </body>
    
</html>
```

Errado:

```html
<html lang="pt-BR">

    <head>
        <meta charset="UTF-8">
    </head>

    <link rel="stylesheet" type="text/css" href="theme.css">

    <h1>Strongest Avenger</h1>

    <body>
        <!-- mais código html -->
    </body>

    <script src="jquery.js"></script>
    
</html>
```

Certo:

```html
<html lang="pt-BR">

    <head>
        <meta charset="UTF-8">
        <link rel="stylesheet" type="text/css" href="theme.css">
        <script src="jquery.js"></script>
    </head>

    <body>
        <h1>Strongest Avenger</h1>
        <!-- mais código html -->
    </body>
    
</html>
```

**DEVE-SE** sempre adicionar as tags *head* e *body* no container *html*.

Errado:

```html
<html lang="pt-BR">

    <head>
        <!-- tags de metadados -->
    </head>
    
</html>
```

Correto
```html
<html lang="pt-BR">

    <head>
        <!-- tags de metadados -->
    </head>
    
    <body>
        <!-- mais código html -->
    </body>
    
</html>
```

## 4. Os Meta Dados

**DEVE-SE** sempre inserir os metadados na tag *head*.

### 4.1. Codificação de Caracteres

**DEVE-SE** sempre adicionar codificação de caracteres, pois a codificação padrão pode variar entre navegadores:

Errado:

```html
<head>
    <title>The Incredible Hulk</title>
</head>
```

Correto:

```html
<head>
    <meta charset="UTF-8">
    <title>The Incredible Hulk</title>
</head>
```

**DEVE-SE** sempre usar *UTF-8* para codificação de caracteres. Isso liberará os caracteres especiais e os emojis sem necessidade de escapes:

Errado:

```html
<head>
    <meta charset="ISO-8859-1">
</head>
```

Correto:

```html
<head>
    <meta charset="UTF-8">
</head>
```

**NÃO DEVE-SE** usar codificação de caracteres antiga. Http headers correspondentes já são enviados automaticamente pelos servidores com as informações do antigo Content-Type:

Errado:

```html
<head>
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
</head>
```

Correto:

```html
<head>
    <meta charset="UTF-8">
</head>
```

**DEVE-SE** sempre adicionar a codificação de caracteres antes de todos os metadados. A especificação obriga que a codificação de caracteres esteja entre os primeiros 1024 bytes do documento:

Errado:

```html
<head>
    <meta content="width=device-width" name="viewport">
    <meta charset="UTF-8">
</head>
```

Correto:

```html
<head>
    <meta charset="UTF-8">
    <meta content="width=device-width" name="viewport">
</head>
```

### 4.2. Elemento title

**DEVE-SE** sempre adicionar o elemento *title*. O valor para o elemento *title* é usado por várias aplicações, não somente para o navegador web.

Errado:

```html
<head>
    <meta charset="UTF-8">
</head>
```

Certo:

```html
<head>
    <meta charset="UTF-8">
    <title>The Incredible Hulk</title>
</head>
```

### 4.3. Elemento base

**NÃO DEVE-SE** adicionar a tag *base*! Um caminho absoluto ou relativo é mais seguro tanto para desenvolvedores como para os leitores de tela.

Errado:

```html
<head>
    <base href="/blog/">
    <link href="ironman.html" rel="canonical">
</head>
```

Certo:

```html
<head>
    <link href="/blog/ironman.html" rel="canonical">
</head>
```

### 4.4. Elemento link

**DEVE-SE** adicionar as tags *link* apenas no container *head* ou em conjunto com microdatas dentro do body.

Errado:

```html
<html lang="pt-BR">

    <head>
        <!-- tags de metadados -->
    </head>

    <body>
        <link href="/blog/ironman.html" rel="canonical">
    </body>
    
</html>
```

Certo:

```html
<html lang="pt-BR">

    <head>
        <link href="/blog/ironman.html" rel="canonical">
    </head>

    <body>
        <!-- mais código html -->
    </body>
    
</html>
```

**DEVE-SE** sempre adicionar o atributo *title* para folhas de estilos alternativos. Usar títulos humanamente legíveis ajuda as pessoas na hora de selecionar o estilo apropriado:

Errado:

```html
<head>
    <link href="/css/screen.css" rel="stylesheet">
    <link href="/css/high-contrast.css" rel="alternate stylesheet">
</head>
```

Certo:

```html
<head>
    <link href="/css/screen.css" rel="stylesheet">
    <link href="/css/high-contrast.css" rel="alternate stylesheet" title="Maior Contraste">
</head>
```

**DEVE-SE** sempre especificar os MIME types para arquivos alternativos. Isso ajuda as aplicações a determinarem como interpretar este aquivo:

Errado:

```html
<head>
    <link href="/pdf" rel="alternate">
    <link href="/feed" rel="alternate">
    <link href="/css/screen.css" rel="stylesheet">
</head>
```

Certo:

```html
<head>
    <link href="/pdf" rel="alternate" type="application/pdf">
    <link href="/feed" rel="alternate" type="application/rss+xml">
    <link href="/css/screen.css" rel="stylesheet">
</head>
```

**DEVE-SE** omitir links que apontam para o arquivo *favicon.ico*. Todos os navegadores atuais encontram o favicon.icon automaticamente e assincronicamente. Basta colocar este arquivo no diretório raiz do site.

Errado:

```html
<head>
    <link href="/favicon.ico" rel="icon" type="image/vnd.microsoft.icon">
</head>
```

Certo:

```html
<head>
    <!-- favicon.ico omitido! Colocado no diretório raiz -->
</head>
```

### 4.5. Blocos de Estilos

**DEVE-SE** omitir o atributo *type* para blocos de estilos. No HTML5, o valor padrão para o elemento style já é *text/css*:

Errado:

```html
<head>
    <style type="text/css">
        /* estilos CSS */
    </style>
</head>
```

Certo:

```html
<head>
    <style>
        /* estilos CSS */
    </style>
</head>
```

**NÃO DEVE-SE** adicionar comentários envolvendo o código CSS dentro da tag style. Isso é uma notação para navegadores muito antigos e não é mais necessária:

Errado:

```html
<head>
    <style>
    <!--
        body { 
            background: #eee; 
        }
    -->
    </style>
</head>
```

Certo:

```html
<head>
    <style>
        body { 
            background: #eee; 
        }
    </style>
</head>
```


## 5. Scripts

Scripts sempre foram uma área onde muito cuidado é necessário, pois um erro pode travar todos os próximos scripts da página HTML. Para que isso não aconteça, segue-se algumas práticas que podem reduzir ou extinguir esses problemas no desenvolvimento.

### 5.1. Separação de contextos

Um prática importantíssima é separar os scripts em dois tipos de conteúdo: arquivos de declaração e arquivos de lógica.

**DEVE-SE** adicionar apenas funções ou objetos em um arquivo de declaração:

```js
// declaração da função 'marvinGaye'
function marvinGaye() 
{
    return 'Ohhh baby!';
}

// declaração da função 'michaelJackson'
function michaelJackson()
{
    return 'Uhhh'!
}

function yellow()
{
    return 'Tchick ti ká!!';
}
```

**NÃO DEVE-SE** adicionar declarações em arquivos de lógica, mas somente implementação lógica. O objetivo de arquivos deste tipo é apenas implementar a rotina, e nada mais.

```js

// atribui valor à variável
var singing_js = "lá lá lá";

// invoca marvinGaye
var one =  marvinGaye();

// invoca michaelJackson
var two = michaelJackson();

// abre uma janela de alerta com a frase 'Ohhh baby! Uhhh Tchick ti ká!!'
alert(one + ' ' + two + yellow() );

// finaliza com um 'lálálá'
console.log(singing_js);
```

### 5.2. Incluindo arquivos de scripts

**DEVE-SE** adicionar scripts com declarações na tag *head*. Bibliotecas, como *jquery*, *datepicker* e *cia*, geralmente são arquivos de declarações.

**DEVE-SE** adicionar scripts com lógica no final da tag *body*.


```html
<html lang="pt-BR">

    <head>
        <script src="/assets/js/jquery.min.js"></script>
        <script src="/assets/js/datepicker.min.js"></script>
    </head>

    <body>
        <main>
            <!-- mais código html -->
        </main>
        
        <script src="/assets/js/app.js"></script>
    </body>
    
</html>
```

**NÃO DEVE-SE** misturar scripts e links na tag *head*. Scripts **DEVEM** ser adicionados no final do bloco, após os links:

```html
<head>
    <script src="/js/jquery.min.js"></script>
    <link href="/css/screen.css" rel="stylesheet">
    <script src="/js/main.js"></script>
</head>
```

Certo:

```html
<head>
    <link href="/css/screen.css" rel="stylesheet">
    <script src="/js/jquery.min.js"></script>
    <script src="/js/main.js"></script>
</head>
```

### 5.3. Blocos de Scripts

**NÃO DEVE-SE** usar o atributo *type* para blocos de scripts. No HTML5, o valor padrão para o elemento style já é *text/javascript*. 

Igualmente, **NÃO DEVE-SE** usar o atributo *language*, pois é muito antigo e está depreciado há séculos:

Errado: 

```html
<script type="text/javascript">
    /* código javascript */
</script>
```

Erradíssimo: 

```html
<script language="javascript">
    /* código javascript */
</script>
```

Certo:

```html
<script>
    /* código javascript */
</script>
```

**NÃO DEVE-SE** adicionar comentários envolvendo o código javascript dentro da tag script. Isso é uma notação para navegadores muito antigos e não é mais necessária:

Errado:

```html
<script>
    /*<![CDATA[*/
      console.log('Thor, son of Odin');
    /*]]>*/
</script>
```

Erradíssimo:

```html
<script>
    <!--
      console.log('Thor, son of Odin');
    // -->
</script>
```

Certo:

```html
<script>
    console.log('Thor, son of Odin');
</script>
```

**NÃO DEVE-SE** usar injeção assíncrona do elemento *script* usando código javascript. **DEVE-SE** usar o atributo booleano *async* da tag *script*, que é melhor pela simplicidade e performance:

Errado:

```html
<script>
    var script = document.createElement("script");
    script.async = true;
    script.src = "//example.com/widget.js";
    document.getElementsByTagName("head")[0].appendChild(script);
</script>
```

Certo:

```html
<script script async defer src="//example.com/widget.js"></script>
```

## 6. Corpo do Documento

### 6.1. O Elemento main

**DEVE-SE** usar o elemento main para envolver o contepudo principal do documento HTML.

Errado:

```html
<div id="content">
    <!-- mais código html -->
</div>
```

Certo:

```html
<main>
    <!-- mais código html -->
</main>
```

### 6.2. Elementos semânticos

**DEVE-SE** evitar ao máximo o uso do elemento *div*. Use *div* apenas como último recurso:

Errado:

```html
<div class="chapter">
    <!-- mais código html -->
</div>
```

Certo:

```html
<section>
    <!-- mais código html -->
</section>
```

## 7. Microdata 

**DEVE-SE** usar o elemento *link* para urls em microdatas. O valor do atributo href pode resolver um URL:

Errado:

```html
<section itemscope itemtype="http://schema.org/BlogPosting">
    <meta content="https://meusite.com.br/blog/superman" itemprop="url">
    <!-- mais código html -->
</section>
```

Certo:

```html
<section itemscope itemtype="http://schema.org/BlogPosting">
    <link href="/blog/superman" itemprop="url">
    <!-- mais código html -->
</section>
```

