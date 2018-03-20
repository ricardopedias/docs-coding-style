# HTML - Conteúdo Textual

* [Principal](readme.md)
* [Índice HTML](html.md)

# 1. Tags i, em, b e strong

As tags `<i>`, `<em>`, `<b>` e `<strong>` são comumente confundidas ou utilizadas erroneamente pelo fato de geralmente terem o mesmo tipo de renderização no browser (as duas primeiras tendo o texto em itálico, e as duas últimas sendo em negrito). Mas seus significados diferem, sendo que:

## 1.1. `<i>`

Utilizado para designar um texto de destaque diferenciado, como em termos especiais ou uso em taxonomia.

```html
<p>
    A arvore, de nome em latin <i>Araucária brasiliensis</i>
</p>
```

## 1.2. `<em>`

Utilizado para dar ênfase em uma palavra (ou frase) que você falaria com entonação diferenciada do resto do texto e que mudaria seu significado.

```html
<p>
    E ela jura que <em>não</em> sabe, não é mesmo?!
</p>
```

## 1.3. `<b>`

Direcionado a textos que necessitem ter destaque, mas sem conotação ou explicação explícita.

```html
<p>
    O e-mail dela é <b>fulana@email.com</b>
</p>
```

## 1.4. `<strong>`

Utilizado para dar ênfase a uma palavra ou frase de alta importância.

```html
<p>
    Pessoal, eu realmente preciso destes relatórios <strong>para amanhã sem falta</strong>!
</p>
```

As tags `<i>` e `<b>` tinham muita utilidade no início da era web, quando era comum que tags HTML servissem para estilizar visualmente o conteúdo de uma página.

Com a evolução da internet e dos navegadores, e com a criação da linguagem CSS, é ideal que o conteúdo seja estilizado via propriedades CSS, e não via tags (ou atributos) HTML, o que retira a necessidade de utilizar as tags acima para fins visuais e as torna úteis apenas para uso semântico e de usabilidade.


[Anterior](html-07-microdata.md) ... 
