# PHP - Estruturas de Controle

* [Principal](readme.md)
* [Índice PHP](php.md)

# 1. Regras Gerais

As regras gerais de estilo para estruturas de controle são as seguintes:

* **DEVE-SE** adicionar um espaço após a palavra-chave da estrutura de controle;
* **NÃO DEVE-SE** adicionar um espaço depois do parenteses de abertura;
* **NÃO DEVE-SE** adicionar um espaço antes do parenteses de fechamento;
* **DEVE-SE** adicionar um espaço entre o parenteses de fechamento e a chave de abertura;
* **DEVE-SE** indentar uma vez o corpo da estrutura;
* **DEVE-SE** colocar a chave de fechamento na linha após o corpo da estrutura;
* **DEVE-SE** envolver entre chaves o corpo de cada estrutura. 

> Isso padroniza como as estruturas se parecem e reduz a possibilidade de introduzir erros à medida que novas linhas são adicionadas ao corpo da estrutura.

# 2. if, elseif, else

* **DEVE-SE** colocar o **else** e o **elseif** na mesma linha que a chave de fechamento do corpo da estrutura anterior;
* **DEVE-SE** utilizar a palavra-chave **elseif** ao invés de **else if** para que todas as palavras-chave de controle se pareçam com uma só palavra.

Note o posicionamento dos parenteses, espaços e chaves, por exemplo:

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

# 3. switch, case

* **DEVE-SE** indentar uma vez a declaração **case** em relação ao **switch**;
* **DEVE-SE** indentar a palavra-chave de terminação **break** (ou qualquer outra palavra-chave de terminação) no mesmo nível que o corpo do **case**;
* **DEVE-SE** adicionar o comentário '`//sem break`' quando a passagem ao próximo case é intencional em um corpo de case que não está vazio.

Note o posicionamento dos parenteses, espaços e chaves, por exemplo: 


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

# 4. while, do while

Na estrutura **while**, note o posicionamento dos parenteses, espaços e chaves, por exemplo:

```php
<?php

while ($expr) {
    // corpo da estrutura
}

```

Similarmente, na estrutura **do while**, note o posicionamento dos parenteses, espaços e chaves.

```php
<?php

do {
    // corpo da estrutura
} while ($expr);

```

# 5. for

Na estrutura **for**, note o posicionamento dos parenteses, espaços e chaves, por exemplo:

```php
<?php

for ($i = 0; $i < 10; $i++) {
    // corpo do for
}

```

# 6. foreach

Na estrutura **foreach**, note o posicionamento dos parenteses, espaços e chaves, por exemplo:

```php
<?php


foreach ($iterable as $key => $value) {
    // corpo do foreach
}

```

# 7. try, catch

Na estrutura **try catch**, note o posicionamento dos parenteses, espaços e chaves, por exemplo:

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

[Anterior](php-02-classes.md) ... [Próxima](php-04-variaveis-funcoes.md)
