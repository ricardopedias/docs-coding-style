# PHP - Variáveis e Funções

* [Principal](readme.md)
* [Íncide PHP](php.md)

# 1. Funções anônimas

* Closures DEVEM ser declaradas com um espaço após a palavra-chave function, e um espaço antes e depois da palavra-chave use;
* A chave de abertura DEVE ser colocada na mesma linha e a chave de fechamento DEVE ser colocada na linha seguinte ao fim do corpo da closure;
* NÃO DEVE haver um espaço após o parentese de abertura da lista de argumentos ou variáveis e NÃO DEVE haver um espaço antes do parentese de fechamento da lista de argumentos ou variáveis;
* Na lista de argumentos e lista de variáveis, NÃO DEVE haver um espaço antes de cada vírgula e DEVE haver um espaço após cada vírgula;
* Argumentos de closures com valores default DEVEM ser colocados ao fim da lista de argumentos

Na declaração de **closure**, note o posicionamento dos parenteses, vírgulas, espaços e chaves:

```php
<?php

$closure_with_args = function ($arg1, $arg2) {
    // corpo
};

$closure_with_args_and_vars = function ($arg1, $arg2) use ($var1, $var2) {
    // corpo
};

```

Listas de argumentos e variáveis PODEM ser dividas em múltiplas linhas, onde cada linha subsequente é indentada uma vez. Ao fazer isso:

* O primeiro item da lista DEVE estar na próxima linha;
* DEVE haver somente um argumento ou variável por linha.
* Quando uma lista finalizando (sendo argumentos ou variáveis) é divida em múltiplas linhas, o parentese de fechamento e a chave abertura DEVEM ser colocados em sua própria linha com um espaço entre eles.

A seguir estão exemplos de closures com e sem listas de argumentos e variáveis que se dividem por múltiplas linhas:

```php
<?php

$long_args_no_vars = function (
    $long_argument,
    $longer_argument,
    $much_longer_argument
) {
   // corpo
};

$no_args_long_vars = function () use (
    $long_var1,
    $longer_var2,
    $much_longer_var3
) {
   // corpo
};

$long_args_long_vars = function (
    $long_argument,
    $longer_argument,
    $much_longer_argument
) use (
    $long_var1,
    $longer_var2,
    $much_longer_var3
) {
   // corpo
};

$long_args_short_vars = function (
    $long_argument,
    $longer_argument,
    $much_longer_argument
) use ($var1) {
   // corpo
};

$short_args_lon_vars = function ($arg) use (
    $long_var1,
    $longer_var2,
    $much_longer_var3
) {
   // corpo
};

```

Note que as regras de formatação também se aplicam em closures que são utilizadas diretamente numa chamada de função ou método como um argumento:

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

[Anterior](php-03-estruturas.md) ... 