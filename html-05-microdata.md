# HTML - Microdata

* [Principal](readme.md)
* [Índice HTML](html.md)

# 1. Links 

**DEVE-SE** usar o elemento *link* para urls em microdatas. O valor do atributo href pode resolver um URL:

Errado:

```html
<section itemscope itemtype="http://schema.org/BlogPosting">
    <meta content="https://meusite.com.br/blog/superman" itemprop="url">
    <!-- mais código html -->
</section>
```

Certo:

```html
<section itemscope itemtype="http://schema.org/BlogPosting">
    <link href="/blog/superman" itemprop="url">
    <!-- mais código html -->
</section>
```

[Anterior](html-04-corpo.md) ... [Próxima](html-06-text-content.md)
