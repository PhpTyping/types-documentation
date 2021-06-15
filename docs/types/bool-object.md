# BooleanObject

* Primitive Type: `bool`, `boolean`

## Usage

Provides a specific map of strings that can map to boolean. This is useful when dealing with classes that provide
boolean values as strings, such as Symfony's Command and QueryParam components.

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

---

#### isTrue

Returns `true` when the current value is identical to `true`.

`isTrue(): bool`

**Usage**:

```php
$isMyBool = new BoolObject(true);
assert($isMyBool->isTrue()); // true
```

---

#### isFalse

Returns `true` when the current value is identical to `false`.

`isFalse(): bool`

**Usage**:

```php
$isMyBool = new BoolObject(true);
assert($isMyBool->isFalse()); // false
```

---

#### getScalarValue

Returns the current scalar value `true` or `false`.

`getScalarValue(): bool`

**Usage**:

```php
$isMyBool = new BoolObject(true);
assert(true === $isMyBool->getScalarValue()); // true
```

---

#### toString

Returns the current scalar value as a string (`'true'`, or `'false'`).

`toString(): string`

**Usage**:

```php
$isMyBool = new BoolObject(true);
assert('true' === $isMyBool->toString()); // true
```

---

#### toInt

Returns `1` for `true` and `0` for `false`.

`toInt(): int`

**Usage**:

```php
$isMyBool = new BoolObject(true);
assert(1 === $isMyBool->toInt()); // true
```

---

### Static

---

#### box

Boxes a given variable to FloatObject instances.

`::box(mixed &$pointer)`

**Usage**:

```php
$isMyBool = new BoolObject(true);
BoolObject::box($isMyBool);
assert($isMyBool instanceof BoolObject); // true
$isMyBool = 'uhoh'; // TypeError
```

---

#### fromPrimitive

Attempts to create a BoolObject from a primitive value.

`::fromPrimitive(mixed $mixed): BoolObject`

**Usage**:

```php
$isMyBool = BoolObject::fromPrimitive('on');
assert($isMyBool instanceof FloatObject); // true
assert($isMyBool->isTrue()); // true
```

---
