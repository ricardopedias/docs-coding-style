# HTML - Implementando Listas de Postagens

* [Principal](readme.md)
* [Índice HTML](html.md)

# 1. Lista de postagens

* **DEVE-SE** envolver uma lista de postagens usando a tag `<section>`;
* **DEVE-SE** usar a tag `<h2>` nos títulos das postagens da lista;

```html
<main>

    <section>

        <h1>Postagens sobre Programação</h1>

        <p>Os artigos mais lidos do planeta Krypton</p>

        <article>
        
            <figure>
            
                <img src='avengers.png' alt='Infinity War'>
                
            </figure>

            <h2>Título do Primeira Postagem</h2>
            
            <p>
                <!-- resumo da postagem -->
            </p>
            
        </article>
        
        <article>
        
            <figure>
            
                <img src='justice-league.png' alt='Justice League'> 
            
            </figure>

            <h2>Título do Segunda Postagem</h2>
            
            <p>
                <!-- resumo da postagem -->
            </p>
            
        </article>
        
    <section>

    <aside>
    
        <!-- barra lateral -->
        
    </aside>

</main>
```


# 2. Postagens relacionadas

* **DEVE-SE** adicionar as postagens relacionados, ou qualquer lista de postagens dentro do bloco `<section>`;
* **NÃO DEVE-SE** adicionar o bloco `<section>` junto com o conteúdo da postagem, na tag `<article>`, mas fora dela;
* **DEVE-SE** usar a tag `<h2>` nos títulos das postagens da lista;

```html
<main>

    <article>

        <!-- conteúdo da postagem atual -->
        
    </article>

    <!-- bloco de relacionados fora do conteúdo da postagem -->
    
    <section>

        <h1>Postagens Relacionadas</h1>

        <article>
        
            <figure>
            
                <img src='avengers.png' alt='Infinity War'>
                
            </figure>

            <h2>Título do Primeira Postagem</h2>
            
            <p>
                <!-- resumo da postagem relacionada -->
            </p>
            
                 
        </article>
        
        <article>
       
            <!-- imagem, titulo e resumo da postagem relacionada -->
            
        </article>

        <article>
       
            <!-- imagem, titulo e resumo da postagem relacionada -->
            
        </article>
        
    <section>

    <aside>
    
        <!-- barra lateral -->
        
    </aside>

</main>
```



...

...

...

...

...

...

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



[Anterior](html-08-implementando-postagens.md) ... 

