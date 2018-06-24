# HTML - Metadados

* [Principal](readme.md)
* [Índice HTML](html.md)

# 1. A tag head

**DEVE-SE** sempre adicionar a tag `<head>` no container `<html>`.

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

# 2. As tags de metadados

As tags usadas para metadados são title, meta, link e base.

* **PODE-SE** usar a tag `<meta>` em qualquer lugar dentro do container `<head>` e `<body>`;
* **PODE-SE** adicionar as tags `<link>` no container `<head>` ou em conjunto com microdatas dentro do `<body>`.
* **DEVE-SE** sempre inserir os outros metadados na tag `<head>`.


# 3. Codificação de Caracteres

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

**DEVE-SE** sempre usar ***UTF-8*** para codificação de caracteres. Isso liberará os caracteres especiais e os emojis sem necessidade de escapes:

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

**DEVE-SE** sempre adicionar a codificação de caracteres antes de todos os metadados no container `<head>`. A especificação obriga que a codificação de caracteres esteja entre os primeiros 1024 bytes do documento:

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

# 4. Elemento title

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

# 5. Elemento base

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

# 6. Microdatas

...


[Anterior](html-01-documento.md) ... [Próxima](html-03-estilos.md)

