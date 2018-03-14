# HTML - Corpo

* [Principal](readme.md)
* [Índice HTML](html.md)

**DEVE-SE** sempre adicionar a *body* no container *html*.

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

# 1. O Elemento main

**DEVE-SE** usar o elemento main para envolver o conteúdo principal do documento HTML.

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

# 2. Elementos semânticos

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

[Anterior](html-03-scripts.md) ... [Próxima](html-05-microdata.md)

