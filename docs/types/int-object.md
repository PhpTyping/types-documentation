# IntObject

* Primitive Type: `int`, `integer`

## Usage

Provides an interface for a lot of internal operations and functions on integers.

**Example**

```php
use Typing\Type\IntObject;
use Exception;


$int = new IntObject(5);
if (8 !== $int->plus(3)->getScalarValue()) {
    throw new Exception('Bad math!');
}
```

## Methods

### Instance

#### plus

#### minus

#### multipliedBy

#### dividedBy

#### compare

#### modulus

#### power

#### squareRoot

#### absolute

#### negate

#### factorial

#### gcd

#### root

#### getNextPrime

#### isPrime

#### isPerfectSquare

#### getPrecision

#### toFloatObject

#### toFloat

#### toStringObject

#### toString

#### toBoolObject

#### toBool

### Static
#### box
`::box(mixed &$pointer)`

Boxes a given variable to BoolObjects.
