# HTML - Corpo

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

Suporte para versões anteriores do Internet Explorer pode ser adicionado com [html5shiv](https://github.com/aFarkas/html5shiv).

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

* **Não DEVE-SE** adicionar mais de uma tag `<main>` visível em um documento. 

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

# 4. O Layout

As tags semânticas existem para facilitar que os leitores de páginas html (navegadores de internet, por ex.) identifiquem o que significa cada conteúdo e possam utilizar esta informação para diversos fins, inclusive para ajudar usuários com alguma deficiência física.

As tags semânticas dão poder ao HTML e são adoradas pelos mecanismos de busca como o Google, por exemplo.

## 4.1. Estrutura básica

* **DEVE-SE** implementar o layout semântico segundo o esquema do HTML5;

```html
<!DOCTYPE html>
<html lang="pt-BR">

    <head>
        <!-- metadados -->
    </head>
    
    <body>

        <header>
            <!-- cabeçalho -->
        </header>

        <main>

             <!-- conteudo -->

            <aside>
                <!-- barra lateral -->
            </aside>

        </main>

        <footer>
            <!-- rodapé -->
        </footer>

    </body>
    
</html>
```

## 4.2. Estrutura de um Artigo

* **DEVE-SE** implementar o conteúdo textual (artigo, postagem, matéria, notícia, etc) usando a tag article;
* **DEVE-SE** envolver o título principal e seus parágrafos com a tag `<header>`;
* **DEVE-SE** envolver os subtítulos em cascata com seus parágrafos com a tag `<section>`;

Errado:

```html
<main>

    <h1>Descobrindo o HTML5</h1>

    <p> <!-- texto  --> </p>

    <p> <!-- texto  --> </p>
    
    <h2>Aprendendo Semântica</h2>
    
    <p> <!-- texto  --> </p>

    <h3>Conhecendo Acessibilidade</h3>
    
    <p> <!-- texto  --> </p>

    <aside>
        <!-- barra lateral -->
    </aside>

</main>
```

Correto:

```html
<main>

    <article>

        <header>
        
            <h1>Descobrindo o HTML5</h1>

            <p> <!-- texto  --> </p>

            <p> <!-- texto  --> </p>

        </header>

        <section>
    
            <h2>Aprendendo Semântica</h2>
    
            <p> <!-- texto  --> </p>

            <h3>Conhecendo Acessibilidade</h3>

            <p> <!-- texto  --> </p>
            
        </section>
        
    <article>

    <aside>
        <!-- barra lateral -->
    </aside>

</main>
```

...


```html
<html lang="pt-BR">

    <head>
        <!-- tags de metadados -->
    </head>
    
    <body>

        <header>

            <img src='logotipo.png' alt='...'>

            <nav>

                <ul>
                    <li><a href='#'>Home</a></li>
                    <li><a href='#'>About</a></li>
                    <li><a href='#'>Blog</a></li>
                    <li><a href='#'>Sign Up</a></li>
               </ul>
               
            </nav>
            
        </header>

        <main>

            <article>

                <header>
                    <h1>Semantic HTML</h1>
                    <p>By Troy McClure. Published January 3rd</p>
                </header>

                <aside class='advert'>
                    <img src='banner-do-anuncio.png'>
                </aside>

                <section>
                
                    <h2>The Document Outline</h2>
                    <p>
                        HTML5 includes several “sectioning content” 
                        elements that affect the document outline.
                    </p>

                    <figure>
                        <img src='semantic-elements.png' alt='...'>
                        <figcaption>
                            New HTML5 semantic elements
                        </figcaption>
                    </figure>

                    <h3>Headers</h3>
                    <p>
                        The <code>&lt;header&gt;</code> element is 
                        one such sectioning element.
                    </p>

                    <h3>Footers</h3>
                    <p>
                        And so is the <code>&lt;footer&gt;</code> element.
                    </p>
                    
                </section>

                <section>
                
                    <h2>Inline Semantic HTML</h2>
                    <p>
                        The <code>&lt;time&gt;</code> element is semantic, 
                        but it’s not sectioning content.
                    </p>
                    
                </section>

                <footer>
                
                    <p>
                        O Autor deste arqtigo é Ricardo Pereira, 
                        um programador residente na cidade de 
                        São José dos Campos - SP
                    </p>
                    
                </footer>

            </article>

            <aside>

                <h2>Sidebar</h2>
                <p>Some sidebar content</p>
                
                <nav>
                    <h3>HTML &amp; CSS Tutorial</h3>
                    <ul>
                        <li><a href='#'>Introduction</a></li>
                        <li><a href='#'>Basic Web Pages</a></li>
                        <li><a href='#'>etc...</a></li>
                    </ul>
                </nav>
                
                <nav>
                    <h3>JavaScript Tutorial</h3>
                    <ul>
                        <li><a href='#'>Introduction</a></li>
                        <li><a href='#'>Hello, JavaScript</a></li>
                        <li><a href='#'>etc...</a></li>
                    </ul>
                </nav>

            </aside>

        </main>

        <footer>

            <nav>
                <h3>JavaScript Tutorial</h3>
                <ul>
                    <li><a href='#'>Introduction</a></li>
                    <li><a href='#'>Hello, JavaScript</a></li>
                    <li><a href='#'>etc...</a></li>
                </ul>
            </nav>

            <p>
                © 2017 Todos os Direitos reservados
            </p>
            
        </footer>

    </body>
    
</html>
```



[Anterior](html-03-scripts.md) ... [Próxima](html-05-microdata.md)

