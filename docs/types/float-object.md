# FloatObject

* Primitive Type: `float`, `double`, `long`

## Usage

Provides an interface for a lot of internal operations and functions on floats.

**Example**

```php
use Typing\Type\FloatObject;
use Exception;


$float = new FloatObject(4.5);
if (8.0 !== $float->plus(3.5)->getScalarValue()) {
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

#### toIntObject

#### toInt

#### toStringObject

#### toString

### Static
#### box
`::box(mixed &$pointer)`

Boxes a given variable to FloatObject instances.
