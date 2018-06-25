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

# 2. Metadados de Cabeçalho

* **PODE-SE** usar a tag `<meta>` em qualquer lugar dentro do container `<head>` e `<body>`;
* **PODE-SE** adicionar as tags `<link>` no container `<head>` ou em conjunto com microdatas dentro do `<body>`.
* **DEVE-SE** sempre inserir os outros metadados no seu devido contexto.


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

**NÃO DEVE-SE** usar o formato antigo de codificação de caracteres. O mimetype (text/html) já é declarados automaticamente:

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

**DEVE-SE** sempre adicionar a codificação de caracteres antes de todos os metadados no container `<head>`. A especificação obriga que a codificação de caracteres esteja entre os [primeiros 1024 bytes do documento](https://www.w3.org/TR/2012/CR-html5-20121217/document-metadata.html#charset):

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

**DEVE-SE** sempre adicionar a tag `<title>`. O valor desta tag é usado por várias aplicações, não somente pelo navegador web.

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

**NÃO DEVE-SE** adicionar a tag `<base>`! Um caminho absoluto ou relativo é mais seguro tanto para a consistência do código HTML como para os leitores de tela.

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

