# PHP - Estruturas de Controle

* [Principal](readme.md)
* [Íncide PHP](php.md)

# 1. Regras Gerais

As regras gerais de estilo para estruturas de controle são as seguintes:

* DEVE haver um espaço após a palavra-chave da estrutura de controle;
* NÃO DEVE haver um espaço depois do parenteses de abertura;
* NÃO DEVE haver um espaço antes do parenteses de fechamento;
* DEVE haver um espaço entre o parenteses de fechamento e a chave de abertura;
* O corpo da estrutura DEVE ser indentada uma vez;
* A chave de fechamento DEVE ser colocada na linha após o corpo da estrutura;
* O corpo de cada estrutura DEVE ser envolta por chaves. Isso padroniza como as estruturas se parecem e reduz a possibilidade de introduzir erros à medida que novas linhas são adicionadas ao corpo da estrutura.

# 2. if, elseif, else

* O **else** e o **elseif** DEVEM estar na mesma linha que a chave de fechamento do corpo da estrutura anterior;
* A palavra-chave **elseif** DEVE ser utilizada ao invés de **else if** para que todas as palavras-chave de controle se pareçam com uma só palavra.

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

* A declaração **case** DEVE ser identada uma vez do switch;
* A palavra-chave case (ou qualquer outra palavra-chave de terminação) DEVE ser indentada no mesmo nível que o corpo do case;
* DEVE haver um comentário como **//sem break** quando a passagem ao próximo case é intencional em um corpo de case que não está vazio.

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
