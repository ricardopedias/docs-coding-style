# HTML - Semântica Estrutural

* [Principal](readme.md)
* [Índice HTML](html.md)

# 1. Regras Gerais

**DEVE-SE** sempre adicionar a *body* no container *html*.

Errado:

```html
<!DOCTYPE html>
<html lang="pt-BR">

    <head>
        <!-- tags de metadados -->
    </head>
    
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

**DEVE-SE** evitar ao máximo o uso do elemento *div*. Use as tags semânticas, limitando o uso de *div* apenas como último recurso:

Errado:

```html

<div id="content">

    <div id="post">
    
        <!-- mais código html -->
        
    </div>        

</div>

```

Certo:

```html
<main>

    <article>
    
        <!-- mais código html -->
        
    </article>
    
</main>
```

# 2. Tags Semânticas

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
* Internet Explorer **Não suportada**
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

Para corrigir o suporte a todas as tags semânticas para os Internet Explorer's menores que a versão 9, é preciso adicionar o script [html5shiv](https://github.com/aFarkas/html5shiv).

```html
<!--[if lt IE 9]>
	<script src="assets/js/html5shiv.js"></script>
<![endif]-->
```

Para corrigir o suporte à tag `<main>` para os Internet Explorer's superiores a versão 9, é preciso aplicar o estilo `display:block` através do CSS: 

```css
main { display: block; }
```

# 3. O Elemento main

A tag `<main>` de um documento inclui conteúdo exclusivo desse documento e exclui o conteúdo que é repetido em um conjunto de documentos, como links de navegação do site, informações de direitos autorais, logotipos do site, banners e formulários de pesquisa (a menos que o documento ou a função principal do aplicativo é o de um formulário de pesquisa).

A tag `<main>` não é um elemento de seção e conteúdo e não afeta o fluxo do documento. Ou seja, ela não tem *margin*, *padding*, *borda* ou qualquer outro valor padrão.

* **DEVE-SE** usar o elemento main para envolver o conteúdo principal do documento HTML.

Errado:

```html
<!DOCTYPE html>
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
<!DOCTYPE html>
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

* **NÃO DEVE-SE** adicionar mais de uma tag `<main>` visível em um documento. 

> Se mais de uma tag `<main>` estiver presente em um documento, todas as outras instâncias devem ser declaradas como ocultas usando o atributo hidden.

Errado:

```html
<!DOCTYPE html>
<html lang="pt-BR">

    <head>
        <!-- tags de metadados -->
    </head>
    
    <body>

        <main>...</main>
        <main>...</main>
        <main>...</main>
        
    </body>
    
</html>
```    

Correto

```html
<html lang="pt-BR">

    <head>
        <!-- tags de metadados -->
    </head>
    
    <body>

        <main>...</main>
        <main hidden>...</main>
        <main hidden>...</main>
        
    </body>
    
</html>
``` 

* **NÃO DEVE-SE** adicionar a tag main como filha de elementos como aside, article, footer, header ou nav.

Errado:

```html
<article>

    <main>        
        <!-- código html conteudo -->
    </main>

</article>
```

Aceitável:

```html

<div>
    <main>

        <article>        
            <!-- código html conteudo -->
        </article>

    </main>
</div>
```

Certo:

```html
<main>

    <article>        
        <!-- código html conteudo -->
    </article>

</main>
```

# 4. A Estrutura básica

As tags semânticas existem para facilitar que os leitores de páginas html (navegadores de internet, por ex.) identifiquem o que significa cada conteúdo e possam utilizar esta informação para diversos fins, inclusive para ajudar usuários com alguma deficiência física.

As tags semânticas dão poder ao HTML e são adoradas pelos mecanismos de busca como o Google, por exemplo.

* **DEVE-SE** implementar o layout semântico segundo o esquema do HTML5;

```html
<!DOCTYPE html>
<html lang="pt-BR">

    <head>
        <!-- metadados -->
    </head>
    
    <body>

        <header>
            <!-- cabeçalho do documento -->
        </header>
        
        <nav>
            <!-- menu principal do documento -->
        </nav>

        <main>

             <!-- conteudo -->

            <aside>
                <!-- barra lateral -->
            </aside>

        </main>

        <footer>
            <!-- rodapé do documento -->
        </footer>

    </body>
    
</html>
```

[Anterior](html-04-scripts.md) ... [Próxima](html-06-semantica-textual.md)

