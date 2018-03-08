# Plexi Coding Style

*By [Ricardo Pereira Dias &copy;](https://github.com/rpdesignerfly)*

Este documento é um guia de codificação, que norteia os projetos desenvolvidos em PHP. Baseado nos padrões PSR-1, PSR-2 com pequenos acréscimos usados para o desenvolvimentos dos pacotes Plexi.

## Referências externas

* [PHP Standards Recommendations](https://www.php-fig.org)
* [PHP do Jeito Certo](http://br.phptherightway.com/)
* [Padrões PEAR](http://pear.php.net/manual/en/rfc.cs-enhancements.php)

# 1. Arquivos PHP

## 1.1. Regras gerais

* Códigos PHP devem ser criados sempre em UTF-8;
* Todos os arquivos PHP devem utilizar o padrão Unix LF (linefeed) de terminação de linhas;
* Deve-se usar apenas as tags padrões longas **<?php ?>** ou curtas **<?= ?>** para envolver código PHP;

## 1.2. Codificação somente em PHP

Além de respeitar as regras gerais, arquivos com código somente em PHP deve começar com **<?php** seguida de uma linha em branco ou o namespace da classe.

Devem terminar com uma única linha em branco e a tag de fechamento **?>** deve ser omitida:

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

## 1.3. Codificação mista (html | javascript | css + PHP)

Arquivos com codificação mista deve seguir as regras gerais:

```php

<?php
    $arch_reactor = new IronMan;
?>

<div>
    <?= $arch_reactor->mark ?>
</div>

<?php
    var_dump($arch_reactor);
?>

```

## 1.4. Declarações de Símbolos x Implementação de Lógica

Em arquivos PHP pode-se declarar simbolos (classes, funções, constantes, etc.) ou implementar lógica. Mas jamais os dois contextos ao mesmo tempo.

### Arquivos com Declarações

Arquivos com declarações devem sem tratados como bibliotecas de funcionalidades, e não podem possuir efeitos colaterais. Em outras palavras, ao incluir um arquivo com declarações, nada deve acontecer até que alguma função, classe ou constante seja invocada.

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

Arquivos com implementação de lógica nunca devem conter declarações de funções, classes ou constantes. O objetivo de arquivos deste tipo é apenas implementar a rotina lógica, e nada mais.

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

// libera a frase 'Ohhh baby! Uhhh Tchick ti ká!!'
echo "$one $two" . yellow();

// finaliza com um 'lálálá'
echo SINGING_PHP;

```


# 2. Classes e Namespaces

O termo "classes" se refere a todas as classes, interfaces e traits.

## 2.1. Estrutura de Arquivos

Cada classe deve ser contida total e unicamente em seu próprio arquivo PHP, que deve possuir o mesmo nome base da classe. Se a classe for declarada como "IronMan", o arquivo correspondente deve se chamar "IronMan.php".

Os namespaces devem corresponder à navegação de diretórios no sistema de arquivos. Se a classe com o namespace for App\Marvel\IronMan, então a estrutura deve ficar /path/do/projeto/App/Marvel/IronMan.php.

```
App
 |
 +---Marvel
 |     |
 |     +---IronMan.php    // new App\Marvel\IronMan;
 |     +---SpiderMan.php  // new App\Marvel\SpiderMan;
 |
 +---DcComics
       |
       +---Superman.php    // new App\DcComics\Superman;
       +---WonderWoman.php // new App\DcComics\WonderWoman;
```

## 2.2. Declaração de Namespace e Use

* Deve haver uma linha em branco após a declaração do **namespace**.
* As declarações **use** devem estar sempre após a declaração do namespace.
* Deve haver uma palavra-chave **use** em cada linha de declaração.
* Deve haver uma linha em branco depois do bloco de **use**'s.

Veja o exemplo:

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

// ... mais código PHP ...
```

## 2.3. Declaração de Classe

* Classes e Namespaces devem ser declaradas sempre em **StudlyCaps**, ou seja, **MinhaClasseFantastica**. Nunca *minhaClasseFantastica* ou *Minha_Classe_Fantastica*, ou outros formatos ainda mais bizarros.
* As palavras-chave **extends** e **implements** devem ser declaradas na mesma linha que o nome da classe.
* A chave de abertura para a classe deve ser colocada em sua própria linha; 
* A chave de fechamento deve ser coloca na linha após o corpo da classe.

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements \ArrayAccess, \Countable
{
    // constantes, propriedades, métodos
}

```

Listas de **implements** podem ser divididas em múltiplas linhas, onde cada linha subsequente é indentada uma vez. Quando fazendo isto, o primeiro item da lista deve ser colocado na linha seguinte e deve haver somente uma interface por linha.

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // constantes, propriedades, métodos
}

```

## 2.4. Constantes

Constantes de classes devem ser declaradas totalmente com letras maiúsculas
separadas com underscore.

Por exemplo:

```php
<?php
namespace App\Marvel;

class IronMan
{
    const VERSION = '42.0';
    const DATE_APPROVED = '1980-10-01';
}

```

=====================

## 2.5. Propriedades

Visibilidades DEVEM ser declaradas para todas as propriedades.

A palavra-chave var NÃO DEVE ser utilizada pra declarar uma propriedade.

NÃO DEVE haver mais de uma propriedade declarada por linha.

Nomes de propriedades NÃO DEVERIAM ser prefixadas com _ para indicar visibilidades protected ou private.

Uma declaração de propriedade se parece com o seguinte:

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public $foo = null;
}
```

Este guia intencionalmente evita qualquer recomentação em relação ao uso de
nomes de propriedades utilizando `$StudlyCaps`, `$camelCase` ou `$under_score`.

Qualquer que seja a convenção de nomeação utilizada, esta DEVE ser aplicada
consistentemente dentro de um escopo razoável. Este escopo podendo ser à nível
de vendor, pacotes, classes ou métodos.

## 2.6. Métodos

Visibilidades DEVEM ser declaradas em todos os métodos.

Nomes de métodos NÃO DEVERIAM ser prefixadas com _ para indicar visibilidades protected ou private.

Assinaturas de métodos NÃO DEVEM ser declaradas com um espaço após o nome do método. A chave de abertura DEVE ser colocada em sua própria linha e a chave de fechamento DEVE ser colocada na linha após o corpo do método. NÃO DEVE haver um espaço depois do parenteses de abertura e NÃO DEVE haver um espaço antes do parenteses de fechamento.

Uma declaração de método se parece com o seguinte. Note o posicionamento dos parenteses, virgulas, espaços e chaves:

Nomes de métodos DEVEM ser declaradas em `camelCase()`.

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // corpo do método
    }
}

```

## 2.7. Argumentos de Métodos

Na lista de argumentos, NÃO DEVE haver um espaço antes de cada vírgula e DEVE haver um espaço após cada vírgula.

Argumentos de métodos com valores default DEVEM ser colocados ao fim da lista de argumentos.

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function foo($arg1, &$arg2, $arg3 = [])
    {
        // corpo do método
    }
}

```

Lista de argumentos PODEM ser divididas entre múltiplas linhas, onde cada linha subsequente é indentada uma vez. Quando fazendo isto, o primeiro item da lista DEVE estar na linha seguinte e DEVE haver somente um argumento por linha.

Quando a lista de argumento é dividida em multiplas linhas, o parenteses de fechamento e a chave abertura DEVEM ser colocadas juntas em sua própria linha com um espaço entre elas.

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function aVeryLongMethodName(
        ClassTypeHint $arg1,
        &$arg2,
        array $arg3 = []
    ) {
        // corpo do método
    }
}

```

## 2.8. abstract, final e static

Quando presente, as declarações abstract e final DEVEM preceder as declarações de visibilidade.

Quando presente, a declaração static DEVEM vir depois da declaração de visibilidade.

```php
<?php
namespace Vendor\Package;

abstract class ClassName
{
    protected static $foo;

    abstract protected function zim();

    final public static function bar()
    {
        // corpo do método
    }
}

```

## 2.9. Method and Function Calls

Quando fazendo uma chamada de métodos ou funções, NÃO DEVE haver um espaço entre o nome do método e o parenteses de abertura, NÃO DEVE haver um espaço após o parenteses de abertura e NÃO DEVE haver um espaço antes do parenteses de fechamento. Na lista de argumentos, NÃO DEVE haver um espaço antes de cada vírgula e DEVE haver um espaço após cada vírgula.

```php
<?php
bar();
$foo->bar($arg1);
Foo::bar($arg2, $arg3);

```

Listas de argumentos PODEM ser divididas em múltiplas linhas, onde cada linha subsequente é indentada uma vez. Quando fazendo isto, o primeiro item da lista DEVE estar na linha seguinte e DEVE haver somente um argumento por linha.

```php
<?php
$foo->bar(
    $longArgument,
    $longerArgument,
    $muchLongerArgument
);

```

# 3. Estruturas de Controle

As regras gerais de estilo para estruturas de controle são as seguintes:

DEVE haver um espaço após a palavra-chave da estrutura de controle
NÃO DEVE haver um espaço depois do parenteses de abertura
NÃO DEVE haver um espaço antes do parenteses de fechamento
DEVE haver um espaço entre o parenteses de fechamento e a chave de abertura.
O corpo da estrutura DEVE ser indentada uma vez
A chave de fechamento DEVE ser colocada na linha após o corpo da estrutura
O corpo de cada estrutura DEVE ser envolta por chaves. Isso padroniza como as estruturas se parecem e reduz a possibilidade de introduzir erros à medida que novas linhas são adicionadas ao corpo da estrutura.

## 3.1. if, elseif, else

Uma estrutura if se parece com o seguinte. Note o posicionamento dos parenteses, espaços e chaves; e que else e elseif estão na mesma linha que a chave de fechamento do corpo da estrutura anterior.

```php
<?php
if ($expr1) {
    // corpo do if
} elseif ($expr2) {
    // corpo do elseif
} else {
    // corpo do else
}

```

A palavra-chave elseif DEVERIA ser utilizada ao invés de else if para que todas as palavras-chave de controle se pareçam com uma só palavra.

# 3.2. switch, case

Uma estrutura switch se parece com o seguinte. Note o posicionamento dos parenteses, espaços e chaves. A declaração case DEVE ser identada uma vez do switch e a palavra-chave case (ou qualquer outra palavra-chave de terminação) DEVE ser indentada no mesmo nível que o corpo do case. DEVE haver um comentário como //sem break quando a passagem próximo case é intencional em um corpo de case que não está vazio.

```php
<?php
switch ($expr) {
    case 0:
        echo 'Primeiro case, com um break';
        break;
    case 1:
        echo 'Segundo case, passando para o próximo case';
        // sem break
    case 2:
    case 3:
    case 4:
        echo 'Terceiro case, return ao invés de break';
        return;
    default:
        echo 'Default case';
        break;
}

```

## 3.3. while, do while

Uma estrutura while se parece com o seguinte. Note o posicionamento dos parenteses, espaços e chaves.

```php
<?php
while ($expr) {
    // corpo da estrutura
}

```

Similarmente, uma estrutura do while se parece com o seguinte. Note o posicionamento dos parenteses, espaços e chaves.

```php
<?php
do {
    // corpo da estrutura
} while ($expr);

```

## 3.4. for

Uma estrutura for se parece com o seguinte. Note o posicionamento dos parenteses, espaços e chaves.

```php
<?php
for ($i = 0; $i < 10; $i++) {
    // corpo do for
}

```

## 3.5. foreach

Uma estrutura foreach se parece com o seguinte. Note o posicionamento dos parenteses, espaços e chaves.

```php
<?php
foreach ($iterable as $key => $value) {
    // corpo do foreach
}

```

## 3.6. try, catch

Uma estrutura try catch se parece com o seguinte. Note o posicionamento dos parenteses, espaços e chaves.

```php
<?php
try {
    // corpo do try
} catch (FirstExceptionType $e) {
    // corpo do catch
} catch (OtherExceptionType $e) {
    // corpo do catch
}

```

# 4. Closures

Closures DEVEM ser declaradas com um espaço após a palavra-chave function, e um espaço antes e depois da palavra-chave use.

A chave de abertura DEVE ser colocada na mesma linha e a chave de fechamento DEVE ser colocada na linha seguinte ao fim do corpo da closure.

NÃO DEVE haver um espaço após o parentese de abertura da lista de argumentos ou variáveis e NÃO DEVE haver um espaço antes do parentese de fechamento da lista de argumentos ou variáveis.

Na lista de argumentos e lista de variáveis, NÃO DEVE haver um espaço antes de cada vírgula e DEVE haver um espaço após cada vírgula.

Argumentos de closures com valores default DEVEM ser colocados ao fim da lista de argumentos.

Uma declaração de closure se parece com o seguinte. Note o posicionamento dos parenteses, vírgulas, espaços e chaves:

```php
<?php
$closureWithArgs = function ($arg1, $arg2) {
    // corpo
};

$closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
    // corpo
};

```

Listas de argumentos e variáveis PODEM ser dividas em múltiplas linhas, onde cada linha subsequente é indentada uma vez. Quando fazendo isto, o primeiro item da lista DEVE estar na próxima linha e DEVE haver somente um argumento ou variável por linha.

Quando uma lista finalizando (sendo argumentos ou variáveis) é divida em múltiplas linhas, o parentese de fechamento e a chave abertura DEVEM ser colocados em sua própria linha com um espaço entre eles.

A seguir estão exemplos de closures com e sem listas de argumentos e variáveis que se dividem por múltiplas linhas.

```php
<?php
$longArgs_noVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) {
   // corpo
};

$noArgs_longVars = function () use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // corpo
};

$longArgs_longVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // corpo
};

$longArgs_shortVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use ($var1) {
   // corpo
};

$shortArgs_longVars = function ($arg) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // corpo
};

```

Note que as regras de formatação também se aplicam em closures que são utilizadas diretamente numa chamada de função ou método como um argumento.

```php
<?php
$foo->bar(
    $arg1,
    function ($arg2) use ($var1) {
        // corpo
    },
    $arg3
);

```
