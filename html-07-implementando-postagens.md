# HTML - Implementando uma Postagem

* [Principal](readme.md)
* [Índice HTML](html.md)

Considerando a implementação de um Blog, ou site de notícias, vamos definir as regras para implemantação de postagens (artigos, notícias, matérias, etc)

# 1. Estrutura de uma Postagem

* **DEVE-SE** implementar o conteúdo da postagem usando a tag `<article>`;

```html
<main>

    <article>

        <!-- conteúdo da postagem -->
        
    </article>

    <aside>
    
        <!-- barra lateral -->
        
    </aside>

</main>
```

* **DEVE-SE** envolver o título principal e seus parágrafos com a tag `<header>`;
* **DEVE-SE** envolver as informações adicionais da postagem (autor, referências, etc) com a tag `<footer>`;
* **DEVE-SE** envolver os subtítulos em cascata (h2, h3, etc) incluindo seus respectivos parágrafos com a tag `<section>`;

Errado:

```html
<main>

    <h1>Descobrindo o HTML5</h1>

    <p>Publicado em: 10/01/2018</p>

    <p> ... </p>
    
    <h2>Aprendendo Semântica</h2>
    
    <p> ... </p>

    <h3>Conhecendo Acessibilidade</h3>
    
    <p> ... </p>

    <h2>Referências</h2>
    
    <ul>
        <li>HTML5 W3C Recommendation</li>
        <li>WHATWG HTML Living Standard</li>
    </ul>

    <p>
        Esta postagem foi escrita por Ricardo Pereira Dias
    </p>

    <aside>
        <!-- barra lateral -->
    </aside>

</main>
```

Correto:

```html
<main>

    <article>

        <!-- título principal e seus parágrafos -->
        
        <header>
        
            <h1>Descobrindo o HTML5</h1>

            <p>
                Publicado em: 
                <time pubdate datetime="2018-10-01">10/01/2018</time>
            </p>

            <p> ... </p>

        </header>

        <!-- subtítulos em cascata -->
        
        <section>
    
            <h2>Aprendendo Semântica</h2>
    
            <p> ... </p>

            <h3>Conhecendo Acessibilidade</h3>

            <p> ... </p>
            
        </section>

        <!-- informações adicionais da postagem -->
        
        <footer>

            <h2>Referências</h2>
    
            <ul>
                <li>HTML5 W3C Recommendation</li>
                <li>WHATWG HTML Living Standard</li>
            </ul>

            <p>
                Esta postagem foi escrita por Ricardo Pereira Dias
            </p>
            
        </footer>
        
    </article>

    <aside>
        <!-- barra lateral -->
    </aside>

</main>
```

* **DEVE-SE** envolver as imagens com a tag `<figure>` e as legendas com a tag `<figcaption>`;

Errado:

```html
<article>

    <!-- mais conteudo -->

    <section>
    
        <h2>Aprendendo Semântica</h2>
    
        <p> ... </p>

        <p>
            <img src='avengers.png' alt='Infinity War'>
            <small>Poster Infinity War</small>
        </p>

        <h3>Conhecendo Acessibilidade</h3>

        <p> ... </p>

    </section>

    <!-- mais conteudo -->
    
</article>
```

Correto:

```html
<article>

    <!-- mais conteudo -->

    <section>
    
        <h2>Aprendendo Semântica</h2>
    
        <p> ... </p>

        <figure>
            <img src='avengers.png' alt='Infinity War'>
            <figcaption>Poster Infinity War</figcaption>
        </figure>

        <h3>Conhecendo Acessibilidade</h3>

        <p> ... </p>

    </section>

    <!-- mais conteudo -->
    
</article>
```

* **DEVE-SE** envolver com a tag `<aside>` partes que estejam diretamente ligadas ao conteúdo da postagem, como frases, trechos em destaque, listas de definições, etc;
* **NÃO DEVE-SE** envolver com a tag `<aside>` conteúdos como banners de anúncios, caixas de busca, artigos relacionados, pois nenhum destes está diretamente relacionado com o conteúdo da postagem;

Errado:

```html
    <article>

        <header>
        
            <!-- cabeçalho da postagem -->

        </header>

        <!-- propaganda da postagem -->
         
        <aside class='advert'>
        
            <img src='banner-propaganda.png'>
            
        </aside>

        <div class="quotes">
        
            <q>
                Trecho do artigo em destaque.
            </q>
            
        </div>

        <section>
    
            <h2>Aprendendo Semântica</h2>
    
            <p> ... </p>

            <h3>Conhecendo Acessibilidade</h3>

            <p> ... </p>
            
        </section>

        <footer>

            <!-- rodapé da postagem -->
            
        </footer>
        
    </article>
```

Correto:

```html
<main>

    <article>

        <header>
        
            <!-- cabeçalho da postagem -->

        </header>

        <!-- propaganda da postagem -->
         
        <div class='advert'>
        
            <img src='banner-propaganda.png'>
            
        </div>

        <aside class="quotes">
        
            <q>
                Trecho do artigo em destaque.
            </q>
            
        </aside>

        <section>
    
            <h2>Aprendendo Semântica</h2>
    
            <p> ... </p>

            <h3>Conhecendo Acessibilidade</h3>

            <p> ... </p>
            
        </section>

        <footer>

            <!-- rodapé da postagem -->
            
        </footer>
        
    </article>

    <aside>
        <!-- barra lateral -->
    </aside>

</main>
```

# 2. Os comentários

* **DEVE-SE** adicionar os comentários da postagem dentro do bloco `<section>`;
* **DEVE-SE** adicionar o bloco `<section>` junto com o conteúdo da postagem, na tag `<article>`;
* **DEVE-SE** envolver cada comentário também com a tag `<article>`;
* **DEVE-SE** usar `<h2>` para o titulo do bloco de comentários;
* **DEVE-SE** usar `<h3>` para o título de cada comentário;
* **DEVE-SE** envolver o titulo e as informações do comentário com `<header>`;
* **DEVE-SE** envolver o texto do comentário com a tag `<p>`.

```html
<article>

    <!-- conteudo do artigo -->
    
    <section>
    
        <h2>Commentários</h2>
        
        <article>
        
            <header>
            
                <h3>Comentário de: SubZero</h3>
                
                <p>
                    <time pubdate datetime="2009-10-10T19:10-08:00">
                    ~1 hora atrás
                    </time>
                </p>
                
            </header>
            
            <p>Eu amo congelar as pessoas enquanto elas dormem</p>
            
        </article>
    
        <article>
        
            <header>
            
                <h3>Comentário de: Ken Masters</h3>
                
                <p>
                    <time pubdate datetime="2009-10-10T19:15-08:00">
                    ~5 horas atrás
                    </time>
                </p>
                
            </header>
            
            <p>Um shoriuken é melhor do que dois hadoukens!</p>
            
        </article>
        
    </section>

</article>
```

[Anterior](html-06-semantica-textual.md) ... [Próxima](html-08-implementando-listas-de-postagens.md)
