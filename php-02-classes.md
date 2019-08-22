# PHP - Classes e Namespaces

* [Principal](readme.md)
* [Índice PHP](php.md)

Para facilitar o entendimento, quando é usado o termo "classes", estamos nos referindo a toda a estrutura que compoe a arquitetura do PHP, ou seja, "classes", "interfaces", "traits", etc.

# 1. Estrutura de Arquivos

* **DEVE-SE** adicionar uma única classe em cada arquivo PHP;
* **DEVE-SE** nomear o arquivo da classe com o mesmo nome base da classe. 

> Se a classe for declarada como "**IronMan**", o arquivo correspondente **DEVE** se chamar "**IronMan.php**";

* **DEVE-SE** corresponder os namespaces com a navegação de diretórios no sistema de arquivos. 

> Se a classe com o namespace for **App\Marvel\IronMan**, então a estrutura **DEVE** ficar como **/path/do/projeto/App/Marvel/IronMan.php**.

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

# 2. Declaração de Namespace e Use

* **DEVE-SE** haver uma linha em branco após a declaração do **namespace**;
* **DEVE-SE** adicionar as declarações **use** sempre após a declaração do namespace;
* **DEVE-SE** adicionar a palavra-chave **use** em cada linha de declaração;
* **DEVE-SE** adicionar uma linha em branco depois do bloco de **use**'s.

```php
<?php
namespace App\Marvel;

use CaptainAmerica;
use SpiderMan as Spidey;
use DcComics\JusticeLeague\WonderWoman;

// ... mais código PHP ...
```

# 3. Declaração de Classes

* **DEVE-SE** declarar classes e namespaces sempre em **UpperCamelCase**. 

> Ou seja, **MinhaClasseFantastica**. Nunca *minhaClasseFantastica* ou *Minha_Classe_Fantastica*, ou outros formatos ainda mais bizarros.

* **DEVE-SE** declarar as palavras-chave **extends** e **implements** na mesma linha que o nome da classe;
* **DEVE-SE** colocar a chave de abertura para a classe em sua própria linha; 
* **DEVE-SE** colocar a chave de fechamento uma linha após o corpo da classe.

```php
<?php
namespace App\Marvel;

use CaptainAmerica;
use SpiderMan as Spidey;
use DcComics\JusticeLeague\WonderWoman;

class ClassName extends AvengersClass implements \ArrayAccess, \Countable
{
    // constantes, propriedades, métodos
}

```

# 4. Múltiplos implements

Listas de **implements** podem ser divididas em múltiplas linhas, onde cada linha subsequente é indentada uma vez. Ao fazer isto:

* **DEVE-SE** colocar o primeiro item da lista na linha seguinte;
* **DEVE-SE** colocar somente uma interface por linha.

```php
<?php
namespace App\Marvel;

use CaptainAmerica;
use SpiderMan as Spidey;
use DcComics\JusticeLeague\WonderWoman;

class IronMan extends AvengersClass implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // constantes, propriedades, métodos
}

```

# 5. Constantes

* **DEVE-SE** declarar constantes de classes totalmente com letras maiúsculas e separadas com underline (_).

```php
<?php
namespace App\Marvel;

class IronMan
{
    const VERSION = '42.0';
    const DATE_APPROVED = '1980-10-01';
}

```

# 6. Propriedades

* **DEVE-SE** declarar os nomes de propriedades em **lowerCamelCase**;
* **DEVE-SE** declarar as visibilidades para todas as propriedades;
* **NÃO DEVE-SE** utilizar a palavra-chave **var** pra declarar uma propriedade;
* **NÃO DEVE-SE** declarar mais que uma uma propriedade por linha;
* **NÃO DEVE-SE** prefixar os nomes de propriedades com **_** para indicar visibilidades *protected* ou *private*;

```php
<?php
namespace App\Marvel;

class IronMan
{
    public $markArmor = 42;
}

```

# 7. Métodos

* **DEVE-SE** declarar os nomes de métodos em **lowerCamelCase**;
* **DEVE-SE** declarar as visibilidades em todos os métodos;
* **NÃO DEVE-SE** prefixar os nomes de métodos com **_** para indicar visibilidades *protected* ou *private*;
* **NÃO DEVE-SE** declara as assinaturas de métodos com um espaço após o nome do método;
* **DEVE-SE** colocar a chave de abertura em sua própria linha;
* **DEVE-SE** colocar a chave de fechamento uma linha após o corpo do método;
* **NÃO DEVE-SE** adicionar um espaço depois do parenteses de abertura;
* **NÃO DEVE-SE** adicionar um espaço antes do parenteses de fechamento.

Note o posicionamento dos parenteses, virgulas, espaços e chaves, por exemplo:


```php
<?php
namespace App\Marvel;

class IronMan
{
    public function archReactor($arg1, &$arg2, $arg3 = [])
    {
        // corpo do método
    }
}

```

# 8. Argumentos de Métodos

* **DEVE-SE** declarar os nomes de argumentos em **snake_case**;
* **NÃO DEVE-SE** adicionar um espaço antes de cada vírgula na lista de argumentos;
* **DEVE-SE** adicionar um espaço após cada vírgula na lista de argumentos;
* **DEVE-SE** colocar os argumentos com valores default ao fim da lista de argumentos.

```php
<?php
namespace App\Marvel;

class IronMan
{
    public function archReactor($arg_one, &$arg_two, $arg_three = [])
    {
        // corpo do método
    }
}

```

Lista de argumentos PODEM ser divididas entre múltiplas linhas, onde cada linha subsequente é indentada uma vez. Ao fazer isso:

* **DEVE-SE** colocar o primeiro item da lista na linha seguinte;
* **DEVE-SE** colocar somente um argumento por linha;
* **DEVE-SE** colocar o parentese de fechamento e a chave de abertura juntas em sua própria linha com um espaço entre elas.

```php
<?php
namespace App\Marvel;

class IronMan
{
    public function superMegaBlasterArchReactor(
        ClassTypeHint $arg1,
        &$arg2,
        array $arg3 = []
    ) {
        // corpo do método
    }
}

```

# 8. abstract, final e static

Quando presente:

* **DEVE-SE** colocar as declarações **abstract** e **final** antes das declarações de visibilidade;
* **DEVE-SE** colocar a declaração **static** depois da declaração de visibilidade.

```php
<?php
namespace App\Marvel;

abstract class IronMan
{
    protected static $foo;

    abstract protected function helloJarvis();

    final public static function archReactor()
    {
        // corpo do método
    }
}

```

# 9. Chamadas de métodos

Ao fazer uma chamada de métodos:

* **NÃO DEVE-SE** adicionar um espaço entre o nome do método e o parenteses de abertura;
* **NÃO DEVE-SE** adicionar um espaço após o parenteses de abertura;
* **NÃO DEVE-SE** adicionar um espaço antes do parenteses de fechamento;
* **NÃO DEVE-SE** adicinar um espaço antes de cada vírgula na lista de argumentos;
* **DEVE-SE** adicionar um espaço após cada vírgula na lista de argumentos.

```php
<?php

bar();
$foo->bar($arg1);
Foo::bar($arg2, $arg3);

```

Listas de argumentos PODEM ser divididas em múltiplas linhas, onde cada linha subsequente é indentada uma vez. Ao fazer isto:

* **DEVE-SE** colocar o primeiro item da lista na linha seguinte;
* **DEVE-SE** colocar somente um argumento por linha.

```php
<?php

$foo->bar(
    $longArgument,
    $longerArgument,
    $muchLongerArgument
);

```

[Anterior](php-01-documento.md) ... [Próxima](php-03-estruturas.md)
