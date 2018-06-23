# HTML - Metadados

* [Principal](readme.md)
* [Índice HTML](html.md)

# 1. A tag head

**DEVE-SE** sempre adicionar a tag *head* no container *html*.

Errado:

```html
<!DOCTYPE html>
<html lang="pt-BR">

    <body>
        <!-- mais código html -->
    </body>
    
</html>
```

Correto
```html
<!DOCTYPE html>
<html lang="pt-BR">

    <head>
        <!-- tags de metadados -->
    </head>
    
    <body>
        <!-- mais código html -->
    </body>
    
</html>
```

**DEVE-SE** sempre inserir os metadados na tag *head*.

# 2. Codificação de Caracteres

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

# 3. Elemento title

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

# 4. Elemento base

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

# 5. Elemento link

**DEVE-SE** adicionar as tags *link* apenas no container *head* ou em conjunto com microdatas dentro do body.

Errado:

```html
<!DOCTYPE html>
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
<!DOCTYPE html>
<html lang="pt-BR">

    <head>
        <link href="/blog/ironman.html" rel="canonical">
    </head>

    <body>
        <!-- mais código html -->
    </body>
    
</html>
```

**NÃO DEVE-SE** misturar scripts e links na tag *head*. Links **DEVEM** ser adicionados no começo do bloco, antes dos scripts:

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

**DEVE-SE** omitir links que apontam para o arquivo *favicon.ico*. Todos os navegadores atuais encontram o *favicon.ico* automaticamente e assincronicamente. Basta colocar este arquivo no diretório raiz do site.

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

* **DEVE-SE** usar sempre os nomes de arquivos lincados em "slug case", ou seja, **"Meu_Arquivo.css" ou "MeuArquivo.css"** deve ser escrito como **"meu-arquivo.css"**; 
* **DEVE-SE** usar sempre os nomes de arquivos lincados em minúsculas, por convenção. 

> Servidores web no Unix (Apache, Nginx) são "case sensitive", ou seja, arquivos chamados "london.jpg" nao podem ser acessados como "London.jpg". Servidores web no windows (Microsoft IIS) não são "case sensitive", ou seja, "london.jpg" pode ser acessado como "London.jpg" ou "LONDON.jpg". Juntar minúsculas e maiúsculas vai gerar inconsistência no projeto, forçando-o a ser executado apenas em um tipo de sistema operacional (ou Windows ou Unix). Para evitar isso, use sempre os nomes de arquivos incluídos no html em minúsculas. 

Errado:

```html
<link href="/css/Principal.css" rel="stylesheet">
<link href="/css/AjustesIE.css" rel="stylesheet">
<link href="/css/TEMA.css" rel="stylesheet">
```

Correto:

```html
<link href="/css/principal.css" rel="stylesheet">
<link href="/css/ajustes-ie.css" rel="stylesheet">
<link href="/css/tema.css" rel="stylesheet">
```

# 6. Blocos de Estilos

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

[Anterior](html-01-documento.md) ... [Próxima](html-03-scripts.md)

