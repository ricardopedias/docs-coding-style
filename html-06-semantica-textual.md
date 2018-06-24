# HTML - Semântica Textual

* [Principal](readme.md)
* [Índice HTML](html.md)


## hgroup

* **NÃO DEVE-SE** usar a tag `<hgroup>`. A [W3C removeu esta tag](http://lists.w3.org/Archives/Public/public-html-admin/2013Apr/0003.html).

Errado:

```html
<hgroup>
  <h1>HTML Best Practices</h1>
  <h2>For writing maintainable and scalable HTML documents.</h2>
</hgroup>
```

Correto:

```html
<h1>HTML Best Practices</h1>
<p>For writing maintainable and scalable HTML documents.</p>
```

## abbr

* **DEVE-SE** adicionar o atributo "title" na tag `<abbr>`.
There is no other way to represent its expansion.

Errado:

```html
<abbr>RPD</abbr>
```

Correto:

```html
<abbr title="Ricardo Pereira Dias">RPD</abbr>
```

## code

* **DEVE-SE** especificar a linguagem de programação da tag `<code>` através do atributo "class", prefixando com a palavra "language-". Embora isso não seja muito formal, é mencionado na [especificação da W3C](https://www.w3.org/TR/html52/textlevel-semantics.html#the-code-element).

Errado:

```html
<code>&lt;!DOCTYPE html&gt;</code>
```

Correto:

```html
<code class="language-html">&lt;!DOCTYPE html&gt;</code>
```

## i, em, b e strong

As tags `<i>`, `<em>`, `<b>` e `<strong>` são comumente confundidas ou utilizadas erroneamente pelo fato de geralmente terem o mesmo tipo de renderização no browser (as duas primeiras tendo o texto em itálico, e as duas últimas sendo em negrito). Mas seus significados diferem, sendo que:


* **DEVE-SE** usar `<i>` para designar um texto de destaque diferenciado, como em termos especiais ou uso em taxonomia;

* **DEVE-SE** usar `<em>` para dar ênfase em uma palavra (ou frase) que você falaria com entonação diferenciada do resto do texto e que mudaria seu significado.


```html
<p>
    A arvore, de nome em latin <i>Araucária brasiliensis</i>
</p>
```


```html
<p>
    E ela jura que <em>não</em> sabe, não é mesmo?!
</p>
```


* **DEVE-SE** usar `<b>` para textos que necessitem ter destaque, mas sem conotação ou explicação explícita;
* 
* **DEVE-SE** usar `<strong>` para dar ênfase a uma palavra ou frase de alta importância.


```html
<p>
    O e-mail dela é <b>fulana@email.com</b>
</p>
```


```html
<p>
    Pessoal, eu realmente preciso destes relatórios <strong>para amanhã sem falta</strong>!
</p>
```

As tags `<i>` e `<b>` tinham muita utilidade no início da era web, quando era comum que tags HTML servissem para estilizar visualmente o conteúdo de uma página.

Com a evolução da internet e dos navegadores, e com a criação da linguagem CSS, é ideal que o conteúdo seja estilizado via propriedades CSS, e não via tags (ou atributos) HTML, o que retira a necessidade de utilizar as tags acima para fins visuais e as torna úteis apenas para uso semântico e de usabilidade.

* **NÃO DEVE-SE** usar a tag `<em>` para demonstrar alertas ou cuidado. 
* **DEVE-SE** usar a tag `<strong>` para demonstrar alertas ou cuidado. 

Errado:

```html
<em>Caution!</em>
```

Correto:

```html
<strong>Caution!</strong>
```

## br

* **DEVE-SE** adicionar quebras de linhas após a tag `<br>`

Errado:

```html
<p>Ricardo<br>Pereira<br>Dias</p>
```

Correto:

```html
<p>
    Ricardo<br>
    Pereira<br>
    Dias
</p>
```

* **NÃO DEVE-SE** usar tags `<br>` para quebrar linhas apenas para propósito visual.
* **DEVE-SE** usar tags `<br>` para indicar quebra de linha **DENTRO** de conteúdos textuais apenas.

Errado:

```html
<p>
    <label>Rule name: <input name="rule-name" type="text"></label><br>
    <label>Rule description:<br>
    <textarea name="rule-description"></textarea></label>
</p>
```

Correto:

```html
<p><label>Rule name: <input name="rule-name" type="text"></label></p>
<p><label>Rule description:<br>
<textarea name="rule-description"></textarea></label></p>
```

## span

* **DEVE-SE** usar o mínimo possível as tags `<span>`. 
* **DEVE-SE** usar tags `<span>` somente como último recurso.


Errado:

```html
Ricardo <span class="lastname">Pereira Dias</span> 
```

Correto:

```html
Ricardo <em>Pereira Dias</em>
```

## address

* **DEVE-SE** usar a tag `<address>` somente para informações de contato.
* **PODE-SE** usar a tag `<address>` para email, rede-social, endereço físico (nome da rua, bairro, etc), número de telefone, ou algo que vc possa entrar em contato.

Errado:

```html
<address>No rights reserved.</address>
```

Correto:

```html
<address>Contact: <a href="https://twitter.com/hail2u_">Kyo Nagashima</a></address>
```

## pre

* **NÃO DEVE-SE** iniciar com nova linha na tag `<pre>`. A primeira nova linha é ignorada pelos navegadores , mas as seguintes são interpretadas.

Errado:

```html
<pre>
&lt;!DOCTYPE html&gt;
</pre>
```

Correto:

```html
<pre>&lt;!DOCTYPE html&gt;
</pre>
```

## blockquote

* **DEVE-SE** usar a tag apropriada para o conteúdo do elemento `<blockquote>`. 

Errado:

```html
<blockquote>For writing maintainable and scalable HTML documents.</blockquote>
```

Correto:

```html
<blockquote>
  <p>For writing maintainable and scalable HTML documents.</p>
</blockquote>
```

* **NÃO DEVE-SE** incluir a atribuição diretamente na tag `<blockquote>`.

Errado:

```html
<blockquote>
  <p>For writing maintainable and scalable HTML documents.</p>

  <p>— HTML Best Practices</p>
</blockquote>
```html

Aceitável:

```html
<blockquote>
  <p>For writing maintainable and scalable HTML documents.</p>
</blockquote>

<p>— HTML Best Practices</p>
```

Correto: (recomendado pela WHATWG):

```html
<figure>
  <blockquote>
    <p>For writing maintainable and scalable HTML documents.</p>
  </blockquote>

  <figcaption>— HTML Best Practices</figcaption>
</figure>
```

Correto: (recomendado pela W3C):

```html
<blockquote>
  <p>For writing maintainable and scalable HTML documents.</p>

  <footer>— HTML Best Practices</footer>
</blockquote>
```

## a

* **NÃO DEVE-SE** separar o mesmo link quando vários elementos estiverem agrupados (exceto se tratar-se de elementos interativos como controles de formulário, etc)

Errado:

```html
<h1><a href="https://whatwg.org/">WHATWG</a></h1>

<p><a href="https://whatwg.org/">A community maintaining and evolving HTML since 2004.</a></p>
```

Correto:

```html
<a href="https://whatwg.org/">
  <h1>WHATWG</h1>

  <p>A community maintaining and evolving HTML since 2004.</p>
</a>
```

* **DEVE-SE** usar o atributo "download" para forçar o download de um recurso.

Errado:

```html
<a href="/downloads/offline.zip">offline version</a>
```

Correto:

```html
<a download href="/downloads/offline.zip">offline version</a>
```

* **DEVE-SE** usar os atributos "rel", "hreflang" e "type" sempre que for apropriado. Essas informações ajudam as aplicações sbre como lidar com o recurso vinculado no atributo "href".

Errado:

```html
<a href="/ja/pdf">Japanese PDF version</a>
```

Correto:

```html
<a href="/ja/pdf" hreflang="ja" rel="alternate" type="application/pdf">Japanese PDF version</a>
```

* **DEVE-SE** ficar claro no texto do link sobre o recurso vinculado. Ou seja, o texto do link deve ser o rótulo de seu recurso vinculado.

Errado:

```html
<p><a href="/pdf" rel="alternate" type="application/pdf">Click here</a> to view PDF version.</p>
```

Correto:

```html
<p><a href="/pdf" rel="alternate" type="application/pdf">PDF version</a> is also available.</p>
```

[Anterior](html-05-semantica-estrutural.md) ... [Próxima](html-07-implementando-postagens.md) ... html-08-implementando-listas-de-postagens.md
