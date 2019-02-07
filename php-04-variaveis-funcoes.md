# PHP - Variáveis e Funções

* [Principal](readme.md)
* [Índice PHP](php.md)

# 1. Declaração de variáveis

As variáveis:

* **DEVEM** ser declaradas em **lowerCamelCase**;

```php
<?php

$argOne = "Programar ";
$argTwo = "é bom ";
$argThree = "demais!";
```

# 2. Declaração de funções

As funções:

* **DEVEM** ser declaradas em **snake_case** para não se confundirem com métodos;
* **NÃO DEVE-SE** adicionar um espaço antes de cada vírgula na lista de argumentos;
* **DEVE-SE** adicionar um espaço após cada vírgula na lista de argumentos;
* **DEVE-SE** colocar os argumentos com valores default ao fim da lista de argumentos.

```php
<?php

public function arch_reactor($arg_one, &$arg_two, $arg_three = [])
{
    // corpo da função
}
```

Lista de argumentos **PODEM** ser divididas em múltiplas linhas, onde cada linha subsequente é indentada uma vez. Ao fazer isso:

* **DEVE-SE** colocar o primeiro item da lista na linha seguinte;
* **DEVE-SE** colocar somente um argumento por linha;
* **DEVE-SE** colocar o parentese de fechamento e a chave de abertura juntas em sua própria linha com um espaço entre elas.

```php
<?php

public function super_mega_blaster_arch_reactor(
    ClassTypeHint $arg1,
    &$arg2,
    array $arg3 = []
) {

    // corpo da função
    
}
```

# 2. Chamadas de funções

Ao fazer uma chamada de função:

* **NÃO DEVE-SE** adicionar um espaço entre o nome da função e o parentese de abertura;
* **NÃO DEVE-SE** adicionar um espaço após o parentese de abertura;
* **NÃO DEVE-SE** adicionar um espaço antes do parenteses de fechamento;
* **NÃO DEVE-SE** adicionar um espaço antes de cada vírgula na lista de argumentos;
* **DEVE-SE** adicionar um espaço após cada vírgula na lista de argumentos.

```php
<?php

arch_reactor();
arch_reactor($arg2);
arch_reactor($arg2, $arg3);
```

# 3. Declaração de funções anônimas (closures)

* **DEVE-SE** declarar closures (funções anônimas) com um espaço após a palavra-chave *function*, e um espaço antes e depois da palavra-chave *use*;
* **DEVE-SE** colocar a chave de abertura na mesma linha;
* **DEVE-SE** colocar a chave de fechamento na linha seguinte ao fim do corpo da closure;
* **NÃO DEVE** haver um espaço após o parentese de abertura da lista de argumentos ou variáveis;
* **NÃO DEVE** haver um espaço antes do parentese de fechamento da lista de argumentos ou variáveis;
* **NÃO DEVE** haver um espaço antes de cada vírgula na lista de argumentos e lista de variáveis;
* **DEVE** haver um espaço após cada vírgula;
* **DEVE-SE** colocar os argumentos com valores default ao fim da lista de argumentos.

Na declaração de **closure**, note o posicionamento dos parenteses, vírgulas, espaços e chaves:

```php
<?php

$closureWithArgs = function ($arg1, $arg2) {

    // corpo da closure
    
};

$closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {

    // corpo da closure
    
};

```

Listas de argumentos e variáveis **PODEM** ser dividas em múltiplas linhas, onde cada linha subsequente é indentada uma vez. Ao fazer isso:

* **DEVE-SE** colocar o primeiro item da lista na linha seguinte;
* **DEVE-SE** colocar somente um argumento ou variável por linha;
* **DEVE-SE** colocar o parentese de fechamento e a chave de abertura juntas em sua própria linha com um espaço entre elas.

Exemplos de argumentos sem a palavra-chave *"use"*:

```php
<?php

$longArgsNoVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) {

   // corpo da closure
   
};
```

Exemplos de variáveis na palavra-chave *"use"* sem argumentos na função:

```php
<?php

$noArgsLongCars = function () use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {

   // corpo da closure
   
};
```

Exemplos de argumentos na função e variáveis na palavra-chave *"use"*:

```php
<?php

$longArgsLongVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {

   // corpo da closure
   
};

$longArgsShortVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use ($var1) {

   // corpo da closure
   
};

$shortArgsLongVars = function ($arg) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {

   // corpo da closure
   
};

```


As regras de formatação também se aplicam em closures que são utilizadas diretamente numa chamada de função ou método como um argumento:

```php
<?php

$foo->bar(
    $arg1,
    function ($arg2) use ($var1) {
    
        // corpo da closure
        
    },
    $arg3
);

```

[Anterior](php-03-estruturas.md) ... 
