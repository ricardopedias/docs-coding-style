# HTML - Documento

* [Principal](readme.md)
* [Índice HTML](html.md)

# 1. Doctype

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

# 2. O Elemento Root

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

# 3. Estrutura padrão

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

[Anterior](html.md) ... [Próxima](html-02-metadados.md)

