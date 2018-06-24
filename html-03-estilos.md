# HTML - Estilos

* [Principal](readme.md)
* [Índice HTML](html.md)

# 1. Elemento link

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

# 2. Blocos de Estilos

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

[Anterior](html-02-metadados.md) ... [Próxima](html-04-scripts.md)