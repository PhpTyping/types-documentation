# DateTime

* Primitive Type: `N/A`

## Credits

<a href="https://github.com/briannesbitt/carbon">
  <img src="https://raw.githubusercontent.com/TheDevNetwork/Aux/master/images/carbon-logo.png" alt="Carbon" width="160px" />
</a>

> This is just a meta-class for Carbon with boxing support.  
> Documentation: https://carbon.nesbot.com/docs/

## Usage

Usage is the same as a carbon class.

**Example**

```php
<?php

namespace Foo;

use Typing\Type\DateTime;

$myDate = new DateTime();
DateTime::box($myDate);
$myDate = '2021-01-01';
assert($myDate instanceof DateTime); // True

```

## Methods

### Static

---

#### box

Boxes a given variable to a DateTime instance.

`::box(mixed &$pointer)`

**Usage**:

```php
use Typing\Type\DateTime;

$date = new DateTime();
DateTime::box($date);
$date = '2021-01-05';
assert($date instanceof DateTime); // true
$date = false; // TypeError
```

---

#### fromPrimitive

Attempts to create a DateTime from a primitive value.

`::fromPrimitive(mixed $mixed): Collection`

**Usage**:

```php
$date = DateTime::fromPrimitive('2021-01-01');
assert($date instanceof DateTime); // true
$date = DateTime::fromPrimitive(111); // TypeError
```

---
