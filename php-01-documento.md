# PHP - Documento

* [Principal](readme.md)
* [Índice PHP](php.md)

# 1. Regras Gerais

## 1.1. Abertura do documento

* **DEVE-SE** criar arquivos PHP sempre em UTF-8;
* **DEVE-SE** utilizar o padrão Unix LF (linefeed) de terminação de linhas em todos os arquivos PHP;
* **DEVE-SE** usar apenas as tags padrões longas **<?php ?>** ou curtas **<?= ?>** para envolver código PHP. Outras variações como `<% %>` ou `<script language="php">` **NÃO DEVEM** ser usadas;

## 1.2. Linhas

* **NÃO DEVE** haver um limite rígido no comprimento da linha;
* **DEVE-SE** determinar o limite suave (barra vertical delimitadoa em IDEs) de 120 caracteres; O ideal é que as linhas possuam sempre que possível, o máximo de 80 caracteres; linhas mais longas do que isso deveriam
ser divididas em várias linhas subseqüentes de no máximo 80 caracteres cada.

* **NÃO DEVE** haver espaços em branco no final de linhas não em branco;
* **PODE-SE** adicionar linhas em branco para melhorar a legibilidade e para separar blocos de código.

## 1.3. Indentação

* **NÃO DEVE-SE** usar tabulações para indentar o código;
* **DEVE-SE** indentar o código com 4 espaços;

> **Nota:** A maioria dos editores de código e IDEs permitem a configuração das tabulações. Procure, sempre configurar para que as tabulações sejam substituídas por 4 espaços. Isso impede que sejam misturados espaços e tabulações, evitando problemas com diffs, patches, histórico e anotações. 

## 1.4. Palavras Chave

* **DEVE-SE** escrever as palavras chave do PHP sempre em lower case. Palavras reservadas como ***true***, ***false*** e ***null*** **DEVEM SEMPRE** ser escritas em lower case.

# 2. Arquivos com código somente em PHP

* **DEVE-SE** sempre começar um arquivo com a tag **<?php**;
* **DEVE-SE** adicionar uma linha em branco após a tag **<?php**, quando não houver namespace;
* **DEVE-SE** adicionar o namespace após a tag **<?php** e uma linha em branco após o namespace, quando ele existir;
* **NÃO DEVE-SE** utilizar a tag de o fechamento **?>** em arquivos com código somente em PHP;
* **DEVE-SE** adicionar uma única linha em branco após o término do código PHP;

```php
<?php
                      // sem namespace: linha em branco após <?php
class IronMan
{
    public $mark = 42;
}

```

```php
<?php
namespace App\Marvel; // com namespace: 
                      // linha em branco após namespace
class IronMan
{
    public $mark = 42;
}

```

# 3. Arquivos com código misto (html | javascript | css + PHP)

* **DEVE-SE** separar o máximo possível o código de servidor (PHP) do código do cliente (html, css ou javascript);
* **DEVE-SE** criar dois blocos, onde o primeiro predomine o PHP e o outro, as outras linguagens.
* **DEVE-SE** usar a notação de templates do PHP (`<?= $variavel; ?>`, `<?php if(true): ?>`, `<?php endif; ?>`, etc) ao misturar com HTML.

Errado:

```php

<script>
    alert('Bem vindo à página HTML');
</script>

<?php
    $title = 'Título da Página';
?>

<h1>
    <?php 
        echo $title; 
    ?>
</h1>

<?php
    $arch_reactor = [
        'one',
        'two',
        'three',
    ];
?>

<p>
    Texto de párágrafo
</p>

<h2>Subtítulo</h2>

<ul>
<?php
    foreach($arch_reactor as $name) {
        echo "<li>";
        echo $name;
        echo "</li>";
    }
?>
</ul>

<p>
    Texto de párágrafo
</p>

```

Certo:

```php
<?php

    // Bloco 1:
    // Predomina o código PHP

    $title = 'Título da Página';
    
    $arch_reactor = [
        'one',
        'two',
        'three',
    ];
    
?>

<!-- 
    Bloco 2
    Predomina o código HTML
-->

<h1>
    <?= $title; ?> <!-- notação de template -->
</h1>

<p>
    Texto de párágrafo
</p>

<h2>Subtítulo</h2>

<ul>
    <?php foreach($arch_reactor as $name): ?> <!-- notação de template -->
    
        <li>
            <?= $name ?> <!-- notação de template -->
        </li>
        
    <?php endforeach; ?> <!-- notação de template -->

</ul>

<p>
    Texto de párágrafo
</p>

<script>
    alert('Bem vindo à página HTML');
</script>

```

# 4. Declarações de Símbolos x Implementação de Lógica

Em arquivos PHP pode-se declarar simbolos (classes, funções, constantes, etc.) ou implementar lógica. Mas JAMAIS os dois contextos ao mesmo tempo.

## 4.1. Arquivos com Declarações

* **DEVE-SE** tratar os arquivos com declarações como bibliotecas de funcionalidades;
* **NÃO DEVE-SE** adicionar efeitos colaterais em arquivos de declarações. Em outras palavras, ao incluir um arquivo com declarações, nada deve ser mudado ou exibido ao usuário até que alguma função, classe ou constante seja invocada. Chamadas às funções **echo**, **print**, **print_r**, **var_dump** e cia, não devem existir no corpo de arquivos de declarações.

Um arquivo com declarações se parece assim:

```php
<?php

// declaração da constante SINGING_PHP
define('SINGING_PHP', 'lálálá');

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

// declaração condicional da função 'yellow'
if (! function_exists('yellow')) {

    function yellow()
    {
        return 'Tchick ti ká!!';
    }
}

```

## 4.2. Arquivos com Implementação de Lógica

* **NÃO DEVE-SE** adicionar declarações de funções, classes ou constantes em arquivos de implementação de lógica. O objetivo de arquivos deste tipo é apenas implementar a rotina lógica, e nada mais.

```php
<?php

// muda o comportamento da reportação de erros
ini_set('error_reporting', E_ALL);

// inclui o arquivo com declarações
include "library.php";

// invoca marvinGaye
$one =  marvinGaye();

// invoca michaelJackson
$two = michaelJackson();

// exibe ao usuário a frase 'Ohhh baby! Uhhh Tchick ti ká!!'
echo "$one $two" . yellow();

// exibe ao usuário um 'lálálá'
echo SINGING_PHP;

```

[Anterior](php.md) ... [Próxima](php-02-classes.md)
