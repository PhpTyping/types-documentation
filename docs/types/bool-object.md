# BooleanObject

* Primitive Type: `bool`, `boolean`

## Usage

Provides a specific map of strings that can map to boolean. This is useful when dealing with
classes that provide boolean values as strings, such as Symfony's Command and QueryParam components.

**Example**

```php
<?php

namespace Foo;

use Typing\Type\BooleanObject;

$bool = new BooleanObject(true);
assert $bool->isTrue();
$string = $bool->toString(); //'true'
BooleanObject::box($bool);
$bool = 7; // Throws TypeError
$fromString = BooleanObject::fromPrimitive('yes'); //'true', 'yes','1', 'on' => true, 'no', 'off', 'false', '0' => false
$fromString = new BooleanObject('on'); // true
$errorString = BooleanObject::fromPrimitive('is_this_really_bool?'); //TypeError
```

**String Map**

```php
public const STRING_MAP = [
    'true' => true,
    'on' => true,
    'yes' => true,
    '1' => true,
    'no' => false,
    'off' => false,
    'false' => false,
    '0' => false,
];
```

## Methods

### Instance

#### isTrue
`isTrue(): bool`

Returns `true` when the current value is identical to `true`.

#### isFalse

`isFalse(): bool`

Returns `true` when the current value is identical to `false`.


#### getScalarValue

`getScalarValue(): bool`

Returns the current scalar value `true` or `false`.

#### toString

`toString(): string`

Returns the current scalar value as a string (`'true'`, or `'false'`).

#### toInt

`toInt(): int`

Returns `1` for `true` and `0` for `false`.

### Static

#### box
`::box(mixed &$pointer)`

Boxes a given variable to BoolObject instances.

#### fromPrimitive

`::fromPrimitive(string|bool $primitive)`

Returns a BooleanObject from a primitive scalar.
