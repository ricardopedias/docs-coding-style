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

# 1. Elementos semânticos

**DEVE-SE** evitar ao máximo o uso do elemento *div*. Use as tags semânticas, limitando o uso de *div* apenas como último recurso:

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

As tags semanticas são: 

* main
* header
* nav
* footer
* article
* section
* aside
* figure
* figcaption
* time
* mark

A tag `<main>` é suportada pelos navegadores:

* Chrome 26+
* Edge 12+
* Firefox 21+
* Opera 15+
* Safari 6.1+
* Android 4.4+
* Chrome Android 64+
* Firefox Android 57+
* Opera Mobile 37+
* iOS Safari 7.1+

As outras tags são suportadas pelos navegadores:

* Chrome 6+
* Edge 12+
* Firefox 4+
* Internet Explorer 9+
* Opera 11.5+
* Safari 5+
* Android 2.2+
* Chrome Android 64+
* Firefox Android 57+
* Opera Mobile 12+
* iOS Safari 4.1+

Referência: [caniuse.com](https://caniuse.com/#feat=html5semantic).

Suporte para versões anteriores do Internet Explorer pode ser adicionado com [html5shiv](https://github.com/aFarkas/html5shiv).

## 1.1. O Elemento main

A tag *main* não é um elemento de seção de conteúdo e não afeta o fluxo do documento. Ou seja, ela não tem *margin*, *padding*, *borda* ou qualquer outro valor padrão.

* **DEVE-SE** usar o elemento main para envolver o conteúdo principal do documento HTML.
* **NÃO DEVE-SE** adicionar a tag main como filha de elementos como aside, article, footer, header ou nav.
* **NÃO DEVE-SE** colocar mais do que **UMA** tag main no seu documento.

Errado:

```html
<html lang="pt-BR">

    <head>
        <!-- tags de metadados -->
    </head>
    
    <body>

        <!-- código html cabeçalho -->

        <div id="content">
        
            <!-- código html conteudo -->

            <!-- código html barra lateral -->

        </div>

        <!-- código html rodapé -->

    </body>
    
</html>
```

Certo:

```html
<html lang="pt-BR">

    <head>
        <!-- tags de metadados -->
    </head>
    
    <body>

        <!-- código html cabeçalho -->

        <main>
        
            <!-- código html conteudo -->

            <!-- código html barra lateral -->

        </main>

        <!-- código html rodapé -->

    </body>
    
</html>
```

## 1.2. A estrutura semântica

...

[Anterior](html-03-scripts.md) ... [Próxima](html-05-microdata.md)

