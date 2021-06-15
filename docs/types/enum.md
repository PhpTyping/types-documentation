# Enum

!!! danger "PHP 8.1 will have native Enums"
    PHP 8.1 is introducing native Enum structures and this class may have to be re-implemented or not needed at all.

* Primitive Type: `N/A`

## Credits

<a href="https://github.com/myclabs/php-enum">
  <img src="https://raw.githubusercontent.com/TheDevNetwork/Aux/master/images/my-c-labs.png" alt="Carbon" width="110px" />
</a>

> This is just a meta-class for php-enum.
> Documentation: https://github.com/myclabs/php-enum#documentation

## Usage

Usage is the same as base class.

**Example**

```php
<?php

namespace Foo;

use Typing\Type\Enum;

/**
 * Class MyEnum.
 *
 * @method static self PENDING()
 * @method static self RUNNING()
 * @method static self FINISHED()
 */
final class Status extends Enum
{
    private const PENDING = 'pending';
    private const RUNNING = 'running';
    private const FINISHED = 'finished';
}

...

$currentStatus = Status::PENDING();
echo $currentStatus; // 'pending'

```

> Or in Symfony Validator component attributes

```php
    #[Assert\NotBlank(message: 'A status is required.')]
    #[Assert\Choice(callback: [Status::class, 'toArray'])]
    private string $status;
```
