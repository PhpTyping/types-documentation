# Enum

* Primitive Type: `N/A`

## Credits

<a href="https://github.com/myclabs/php-enum">
  <img src="https://raw.githubusercontent.com/TheDevNetwork/Aux/master/images/my-c-labs.png" alt="Carbon" width="110px" />
</a>

> This is just a meta-class for php-enum.
> <br/>
> Documentation: https://github.com/myclabs/php-enum#documentation


## Usage

Usage is the same as a php-enum.

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

$currentStatus = Status::PENDING();

echo $currentStatus; // 'pending'

```

## Methods
### Static
#### getSupported

`::getSupported(): array`

Alias for `::toArray()`
