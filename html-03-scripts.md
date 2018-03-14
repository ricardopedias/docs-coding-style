# HTML - Scripts

* [Principal](readme.md)
* [Índice HTML](html.md)

Scripts sempre foram uma área onde muito cuidado é necessário, pois um erro pode travar todos os próximos scripts da página HTML. Para que isso não aconteça, segue-se algumas práticas que podem reduzir ou extinguir esses problemas no desenvolvimento.

# 1. Separação de contextos

Um prática importantíssima é separar os scripts em dois tipos de conteúdo: arquivos de declaração e arquivos de lógica.

**DEVE-SE** adicionar apenas funções ou objetos em um arquivo de declaração:

```js
// declaração da função 'marvinGaye'
function marvinGaye() 
{
    return 'Ohhh baby!';
}

// declaração da função 'michaelJackson'
function michaelJackson()
{
    return 'Uhhh'!
}

function yellow()
{
    return 'Tchick ti ká!!';
}
```

**NÃO DEVE-SE** adicionar declarações em arquivos de lógica, mas somente implementação lógica. O objetivo de arquivos deste tipo é apenas implementar a rotina, e nada mais.

```js

// atribui valor à variável
var singing_js = "lá lá lá";

// invoca marvinGaye
var one =  marvinGaye();

// invoca michaelJackson
var two = michaelJackson();

// abre uma janela de alerta com a frase 'Ohhh baby! Uhhh Tchick ti ká!!'
alert(one + ' ' + two + yellow() );

// finaliza com um 'lálálá'
console.log(singing_js);
```

# 2. Incluindo arquivos de scripts

**DEVE-SE** adicionar scripts com declarações na tag *head*. Bibliotecas, como *jquery*, *datepicker* e *cia*, geralmente são arquivos de declarações.

**DEVE-SE** adicionar scripts com lógica no final da tag *body*.


```html
<html lang="pt-BR">

    <head>
        <script src="/assets/js/jquery.min.js"></script>
        <script src="/assets/js/datepicker.min.js"></script>
    </head>

    <body>
        <main>
            <!-- mais código html -->
        </main>
        
        <script src="/assets/js/app.js"></script>
    </body>
    
</html>
```

**NÃO DEVE-SE** misturar scripts e links na tag *head*. Scripts **DEVEM** ser adicionados no final do bloco, após os links:

```html
<head>
    <script src="/js/jquery.min.js"></script>
    <link href="/css/screen.css" rel="stylesheet">
    <script src="/js/main.js"></script>
</head>
```

Certo:

```html
<head>
    <link href="/css/screen.css" rel="stylesheet">
    <script src="/js/jquery.min.js"></script>
    <script src="/js/main.js"></script>
</head>
```

# 3. Blocos de Scripts

**NÃO DEVE-SE** usar o atributo *type* para blocos de scripts. No HTML5, o valor padrão para o elemento script já é *text/javascript*. 

Igualmente, **NÃO DEVE-SE** usar o atributo *language*, pois é muito antigo e está depreciado há séculos:

Errado: 

```html
<script type="text/javascript">
    /* código javascript */
</script>
```

Erradíssimo: 

```html
<script language="javascript">
    /* código javascript */
</script>
```

Certo:

```html
<script>
    /* código javascript */
</script>
```

**NÃO DEVE-SE** adicionar comentários envolvendo o código javascript dentro da tag script. Isso é uma notação para navegadores muito antigos e não é mais necessária:

Errado:

```html
<script>
    /*<![CDATA[*/
      console.log('Thor, son of Odin');
    /*]]>*/
</script>
```

Erradíssimo:

```html
<script>
    <!--
      console.log('Thor, son of Odin');
    // -->
</script>
```

Certo:

```html
<script>
    console.log('Thor, son of Odin');
</script>
```

**NÃO DEVE-SE** usar injeção assíncrona do elemento *script* usando código javascript. **DEVE-SE** usar o atributo booleano *async* da tag *script*, que é melhor pela simplicidade e performance:

Errado:

```html
<script>
    var script = document.createElement("script");
    script.async = true;
    script.src = "//example.com/widget.js";
    document.getElementsByTagName("head")[0].appendChild(script);
</script>
```

Certo:

```html
<script async defer src="//example.com/widget.js"></script>
```

[Anterior](html-02-metadados.md) ... [Próxima](html-04-corpo.md)

