# IntObject

* Primitive Type: `int`, `integer`

## Usage

Provides an interface for a lot of internal operations and functions on integers.

**Example**

```php
use Typing\Type\IntObject;
use Exception;


$float = new IntObject(4.5);
if (8.0 !== $float->plus(3.5)->getScalarValue()) {
    throw new Exception('Bad math!');
}
```

## Extensions

!!! info "This section is optional."
    If you don't care about customizing the extensions, simply go on to the [methods](#methods) section.

By default, the order of extension loading is as follows:

```php
    /**
     * @return MathLibraryInterface[]
     */
    protected function getDefaultDelegates(): array
    {
        //Array is sorted in order of preference. Override in child class if so desired.
        return [
            'bcmath' => new BcMath($this->getRoundingStrategy()),
            'gmp' => new Gmp(),
            'spl' => new Spl($this->getRoundingStrategy()),
        ];
    }
```

You do not need to actually have any of these extensions installed. If one fails, or is not enabled,it will simply go to
the next, behaving like a chain, until it finds a library that can perform the operation.

If you want to only use specific libraries when using NumberTypes (Float | Int), then you need to pass it an instance of
a MathAdapter that only contains those libraries.

```php
use Typing\Math\DefaultMathAdapter;
use Typing\Math\Library\BcMath;
use Typing\Math\Library\MathLibraryInterface;
use Typing\Math\Library\Spl;
use Typing\Type\Collection;

$libraries = new Collection(array: [
    new BcMath(),
    new Spl(),
], type: MathLibraryInterface::class);

$adapter = new DefaultMathAdapter(delegates: $libraries)

$float = new IntObject(float: 5.0, adapter: $adapter);
```

I am working on implementing a symfony bundle, so the library can be customized without so much verbosity.

For other frameworks, PRs are welcome!

### BCMath

Make sure the BCMath extension (often `php-bcmath`) is installed and enabled if you'd like IntObjects to use this
library when performing arithmetic.

> Some methods are decorated instead of direct proxies to the library for compatibility purposes.

### Gmp

Make sure the GMP extension (often `php-gmp`) is installed and enabled if you'd like IntObjects to use this library
when performing arithmetic.

> Some methods are decorated instead of direct proxies to the library for compatibility purposes.

### Spl

This is just standard php arithmetic without any special operations.

## Methods

### Instance

---

#### plus

Adds a number to the current instance.

`plus(StringObject | NumberObjectInterface | string | float | int $num): NumberObjectInterface;`

**Usage**:

```php
$float = new IntObject(3.0);
assert(6.2 == $float->plus(3.2)->getScalarValue()); // true
```

---

#### minus

Subtracts a number from the current instance.

`minus(StringObject | NumberObjectInterface | string | float | int $num): NumberObjectInterface;`

**Usage**:

```php
$float = new IntObject(7.0);
assert(2.8 == $float->minus(4.2)->getScalarValue()); // true
```

---

#### multipliedBy

Multiplies the current instance by a number.

`multipliedBy(StringObject | NumberObjectInterface | string | float | int $num): NumberObjectInterface;`

**Usage**:

```php
$float = new IntObject(2.0);
assert(20.0 == $float->multipliedBy(10)->getScalarValue()); // true
```

---

#### dividedBy

Divides the current instance by a number.

`dividedBy(StringObject | NumberObjectInterface | string | float | int $num): NumberObjectInterface;`

**Usage**:

```php
$float = new IntObject(10.0);
assert(2.0 == $float->dividedBy(5)->getScalarValue()); // true
```

---

#### compare

Compares the current instance to the param passed. Same rules as spaceship `<=>` or `version_compare` for return values.

`compare(StringObject | NumberObjectInterface | string | float | int $num): NumberObjectInterface;`

**Usage**:

```php
$float = new IntObject(10.0);
assert(1 == $float->compare(5)->getScalarValue()); // true
```

---

#### modulo

Returns the remainder of the instance divided by the param.

`modulo(StringObject | NumberObjectInterface | string | float | int $num): NumberObjectInterface;`

**Usage**:

```php
$float = new IntObject(55.3);
assert(5.3 == $float->modulo(10)->getScalarValue()); // true
$float = new IntObject(10.0);
assert (0 == $float->modulo(2)->getScalarValue()); // true
```

---

#### power

Returns instance to the power of param.

`power(StringObject | NumberObjectInterface | string | float | int $num): NumberObjectInterface;`

**Usage**:

```php
$float = new IntObject(10);
assert(31622776.6 == $float->power(7.5)->getScalarValue()); // true
```

---

#### squareRoot

Returns the instance's square root.

`squareRoot(): NumberObjectInterface;`

**Usage**:

```php
$float = new IntObject(10);
assert(31622776.6 == $float->power(7.5)->getScalarValue()); // true
```

---

#### absolute

Returns the instance's absolute value.

`absolute(): NumberObjectInterface;`

**Usage**:

```php
$float = new IntObject(-15.5);
assert(15.5 == $float->absolute()->getScalarValue()); // true
```

---

#### negate

Returns the instance's opposite value.

`negate(): NumberObjectInterface;`

**Usage**:

```php
$float = new IntObject(-15.5);
assert(15.5 == $float->negate()->getScalarValue()); // true

$float = new IntObject(77.5);
assert(-77.5 == $float->negate()->getScalarValue()); // true
```

---

#### factorial

Returns the factorial value for instance. Arguments must be whole, positive numbers.

`factorial(): NumberObjectInterface;`

**Usage**:

```php
$float = new IntObject(10.0);
assert(3628800 == $float->factorial()->getScalarValue()); // true

$float = new IntObject(10.1);
$float->factorial(); // InvalidNumberException

$float = new IntObject(-10.0);
$float->factorial(); // InvalidNumberException
```

---

#### gcd

Returns the greatest common divider between the current instance and argument.

`gcd(StringObject | NumberObjectInterface | string | float | int $num): NumberObjectInterface;`

**Usage**:

```php
$float = new IntObject(50.0);
assert(10 == $float->gcd(10)->getScalarValue()); // true
```

---

#### root

!!! warning "Extension Required"
    `php-gmp` must be installed for this method to work.

Takes the nth root of the current instance and returns the integer component of the result.

`root(int $num): NumberObjectInterface`

**Usage**:

```php
$float = new IntObject(50.0);
assert(10 == $float->gcd(10)->getScalarValue()); // true
```

---

#### getNextPrime

Return the next prime number after current instance's value.

`getNextPrime(): NumberObjectInterface;`

**Usage**:

```php
$float = new IntObject(5.0);
assert(7 == $float->getNextPrime()->getScalarValue()); // true
```

---

#### isPrime

Returns true if the current instance is a prime number.

`isPrime(): bool;`

**Usage**:

```php
$float = new IntObject(5.0);
assert($float->isPrime()); // true

$float = new IntObject(6.0);
assert($float->isPrime()); // false
```

---

#### isPerfectSquare

Returns true if the current instance is a perfect square.

`isPerfectSquare(): bool;`

**Usage**:

```php
$float = new IntObject(4.0);
assert($float->isPerfectSquare()); // true

$float = new IntObject(6.0);
assert($float->isPerfectSquare()); // false

$float = new IntObject(9.0);
assert($float->isPerfectSquare()); // true
```

---

#### getPrecision

Gets the current precision. If null was passed, then it calculates the precision.

`getPrecision(): int;`

**Usage**:

```php
$float = new IntObject(4.0);
assert(1 === $float->getPrecision()); // true

$float = new IntObject(6.038);
assert(3 === $float->getPrecision()); // false

$float = new IntObject(9.0);
assert($float->isPerfectSquare()); // true
```

---

#### toIntObject

Converts the current instance to an IntObject.

`toIntObject(): IntObject;`

**Usage**:

```php
$float = new IntObject(4.05);
assert(new IntObject(4) == $float->toIntObject()); // true
```

---

#### toInt

Converts the current instance to a primitive int.

`toInt(): int;`

**Usage**:

```php
$float = new IntObject(4.04);
assert(4 === $float->toInt()); // true
```

---

#### toStringObject

Converts the current instance to a StringObject.

`toStringObject(): StringObject;`

**Usage**:

```php
$float = new IntObject(4.05);
assert(new StringObject('4.05') == $float->toStringObject()); // true
```

---

#### toString

Converts the current instance to a primitive string.

`toString(): string;`

**Usage**:

```php
$float = new IntObject(4.04);
assert('4.04' === $float->toString()); // true
```

---

### Static

---

#### box

Boxes a given variable to IntObject instances.

`::box(mixed &$pointer)`

**Usage**:

```php
$float = new IntObject(4.04);
IntObject::box($float);
$float = 7.77;
assert($float instanceof IntObject); // true
$float = false; // TypeError
```

---

#### fromPrimitive

Attempts to create a IntObject from a primitive value. Throws error if non_numeric passed.

`::fromPrimitive(mixed $mixed, ?int $precision = null): IntObject`

**Usage**:

```php
$float = IntObject::fromPrimitive('4.04');
assert($float instanceof IntObject); // true

$float = IntObject::fromPrimitive(false); // TypeError
```

---
