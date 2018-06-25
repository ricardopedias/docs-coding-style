# HTML - Semântica Textual

* [Principal](readme.md)
* [Índice HTML](html.md)


# 1. O elemento hgroup

**NÃO DEVE-SE** usar a tag `<hgroup>`. A [W3C removeu esta tag](http://lists.w3.org/Archives/Public/public-html-admin/2013Apr/0003.html).

Errado:

```html
<hgroup>
  <h1>Super Mario Bros.</h1>
  <h2>Mario e Luigi são heróis que vestem macacão, comem cogumelos, ficam gigantes e entram pelo cano.</h2>
</hgroup>
```

Correto:

```html
<h1>Super Mario Bros.</h1>
<p>Mario e Luigi são heróis que vestem macacão, comem cogumelos, ficam gigantes e entram pelo cano.</p>
```

# 2. O elemento abbr

**DEVE-SE** adicionar o atributo *"title"* na tag `<abbr>` (abreviação). O *"title"* contém o valor que explica a abreviação.

Errado:

```html
<abbr>RPD</abbr>
```

Correto:

```html
<abbr title="Raccoon City Police Department">RPD</abbr>
```

# 3. O elemento code

**DEVE-SE** especificar a linguagem de programação da tag `<code>` através do atributo "class", prefixando com a palavra "language-". Embora isso não seja muito formal, é mencionado na [especificação da W3C](https://www.w3.org/TR/html52/textlevel-semantics.html#the-code-element).

Errado:

```html
<code>&lt;!DOCTYPE html&gt;</code>
```

Correto:

```html
<code class="language-html">&lt;!DOCTYPE html&gt;</code>
```

# 4. Os elementos i, em, b e strong

As tags `<i>`, `<em>`, `<b>` e `<strong>` são comumente confundidas ou utilizadas erroneamente pelo fato de geralmente terem o mesmo tipo de renderização no navegador (as duas primeiras tendo o texto em itálico, e as duas últimas sendo em negrito). Mas seus significados diferem, sendo que:


**DEVE-SE** usar `<i>` para designar um texto de destaque diferenciado, como em termos especiais ou uso em taxonomia;

**DEVE-SE** usar `<em>` para dar ênfase em uma palavra (ou frase) que você falaria com entonação diferenciada do resto do texto e que poderia mudar seu significado.


```html
<p>
    A árvore, de nome em latin <i>Araucária brasiliensis</i> é bonita.
</p>
```


```html
<p>
    E ela jura que <em>não sabe</em>, não é mesmo?!
</p>
```


**DEVE-SE** usar `<b>` para textos que necessitem ter destaque, mas sem conotação ou explicação explícita; 
**DEVE-SE** usar `<strong>` para dar ênfase a uma palavra ou frase de alta importância.


```html
<p>
    O e-mail dela é <b>jill.valentine@gmail.com</b>
</p>
```


```html
<p>
    Pessoal, eu realmente preciso destes relatórios <strong>para amanhã sem falta</strong>!
</p>
```

As tags `<i>` e `<b>` tinham muita utilidade no início da era web, quando era comum que tags HTML servissem para estilizar visualmente o conteúdo de uma página.

Com a evolução da internet e dos navegadores, e com a criação da linguagem CSS, é ideal que o conteúdo seja estilizado via propriedades CSS, e não via tags (ou atributos) HTML, o que retira a necessidade de utilizar as tags acima para fins visuais e as torna úteis apenas para uso semântico e de usabilidade.

**NÃO DEVE-SE** usar a tag `<em>` para demonstrar alertas ou cuidado. 
**DEVE-SE** usar a tag `<strong>` para demonstrar alertas ou cuidado. 

Errado:

```html
<em>Atenção!</em>
```

Correto:

```html
<strong>Atenção!</strong>
```

# 5. O elemento br

**DEVE-SE** adicionar quebras de linhas após a tag `<br>`

Errado:

```html
<p>Mortal<br>Kombat<br>Trilogy</p>
```

Correto:

```html
<p>
    Mortal<br>
    Kombat<br>
    Trilogy
</p>
```

**NÃO DEVE-SE** usar tags `<br>` para quebrar linhas apenas para propósito visual.
**DEVE-SE** usar tags `<br>` para indicar quebra de linha **DENTRO** de conteúdos textuais apenas.

# 6. O elemento span

**DEVE-SE** usar o mínimo possível as tags `<span>`. 
**DEVE-SE** usar tags `<span>` somente como último recurso.


Errado:

```html
Ricardo <span class="lastname">Pereira Dias</span> 
```

Correto:

```html
Ricardo <em>Pereira Dias</em>
```

# 7. O elemento address

**DEVE-SE** usar a tag `<address>` somente para informações de contato.
**PODE-SE** usar a tag `<address>` para email, rede-social, endereço físico (nome da rua, bairro, etc), número de telefone, ou algo que vc possa entrar em contato.

Errado:

```html
<address>Sem direitos reservados.</address>
```

Correto:

```html
<address>Contato: <a href="https://twitter.com/gean">Shinarui Gean</a></address>
```

# 8. O elemento pre

**NÃO DEVE-SE** iniciar com nova linha na tag `<pre>`. A primeira nova linha é ignorada pelos navegadores , mas as seguintes são interpretadas.

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

# 9. O elemento blockquote

**DEVE-SE** usar a tag apropriada para o conteúdo do elemento `<blockquote>`. 

Errado:

```html
<blockquote>
    Eu trocaria uma mina de diamantes por um copo de água pura da nascente.
</blockquote>
```

Correto:

```html
<blockquote>
  <p>
  Eu trocaria uma mina de diamantes por um copo de água pura da nascente.
  </p>
</blockquote>
```

**NÃO DEVE-SE** incluir a atribuição diretamente na tag `<blockquote>`.

Errado:

```html
<blockquote>
  <p>
  Eu trocaria uma mina de diamantes por um copo de água pura da nascente.
  </p>

  <p>— Júlio Verne (Viagem ao Centro da Terra, 1864)</p>
</blockquote>
```html

Aceitável:

```html
<blockquote>
  <p>
  Eu trocaria uma mina de diamantes por um copo de água pura da nascente.
  </p>
</blockquote>

<p>— Júlio Verne (Viagem ao Centro da Terra, 1864)</p>
```

Correto: (recomendado pela WHATWG):

```html
<figure>
  <blockquote>
    <p>
    Eu trocaria uma mina de diamantes por um copo de água pura da nascente.
    </p>
  </blockquote>

  <figcaption>— Júlio Verne (Viagem ao Centro da Terra, 1864)</figcaption>
</figure>
```

Correto: (recomendado pela W3C):

```html
<blockquote>
  <p>
  Eu trocaria uma mina de diamantes por um copo de água pura da nascente.
  </p>

  <footer>— Júlio Verne (Viagem ao Centro da Terra, 1864)</footer>
</blockquote>
```

# 10. O elemento a (âncora)

**NÃO DEVE-SE** separar o mesmo link quando vários elementos estiverem agrupados (exceto se tratar-se de elementos interativos como controles de formulário, etc)

Errado:

```html
<h1><a href="https://whatwg.org/">WHATWG</a></h1>

<p><a href="https://whatwg.org/">Uma comunidade envolvida com HTML desde 2004.</a></p>
```

Correto:

```html
<a href="https://whatwg.org/">
  <h1>WHATWG</h1>

  <p>Uma comunidade envolvida com HTML desde 2004.</p>
</a>
```

**DEVE-SE** usar o atributo "download" para forçar o download de um recurso.

Errado:

```html
<a href="/downloads/mediakit.zip">Download do MediaKit</a>
```

Correto:

```html
<a download href="/downloads/mediakit.zip">Download do MediaKit</a>
```

**DEVE-SE** usar os atributos *"rel"*, *"hreflang"* e *"type"* sempre que for apropriado. Essas informações ajudam as aplicações sbre como lidar com o recurso vinculado no atributo "href".

Errado:

```html
<a href="/ja/pdf">PDF na versão Japonesa</a>
```

Correto:

```html
<a href="/ja/pdf" hreflang="ja" rel="alternate" type="application/pdf">PDF na versão Japonesa</a>
```

**DEVE-SE** ficar claro no texto do link sobre o recurso vinculado. Ou seja, o texto do link deve ser o rótulo de seu recurso vinculado. Isso ajuda o usuário e também o Google a determinar do que se trata o link. 

Errado:

```html
<p><a href="/pdf" rel="alternate" type="application/pdf">Clique aqui</a> para ver a versão em PDF.</p>
```

Correto:

```html
<p><a href="/pdf" rel="alternate" type="application/pdf">Versão em PDF</a> está disponível.</p>
```

[Anterior](html-05-semantica-estrutural.md) ... [Próxima](html-07-implementando-postagens.md)
