# Collection

* Primitive Type: `array`

## Credits

<a href="https://github.com/doctrine">
  <img src="https://raw.githubusercontent.com/TheDevNetwork/Aux/master/images/doctrine-logo.png" alt="Doctrine Collections & Doctrine Inflector" width="100px" />
</a>

!!! info "Doctrine Collection Implementation"
    This class implements an extended `Collection` interface, and has extends on the `ArrayCollection` implementation.

## Usage

Provides a wrapper around arrays that exposes most if not all native array functions. Also implements the following
interfaces:

**Native**

* `Countable`
* `IteratorAggregate`
* `ArrayAccess`

**Vendor Library**

* `Doctrine\Common\Collections\Collection`

**Library**

* `Typing\Type\TypedCollectionInterface`

**Example**

```php
<?php

namespace Foo;

use Doctrine\Common\Collections\Collection as CollectionInterface;
use Typing\Type\Collection;
use Typing\Type\TypedCollectionInterface;
use Typing\Type\StringObject;


$typedCollection = new Collection(['foo', 'bar'], StringObject::class); // A collection of StringObjects
assert($typedCollection instanceof CollectionInterface); // true
assert($typedCollection instanceof TypedCollectionInterface); // true
foreach ($typedCollection as $stringObject) {
    echo $stringObject->classify(), PHP_EOL;
    // Prints:
    // Foo
    // Bar 
    assert($stringObject instanceof StringObject); // True
}

$typedPrimitiveCollection = new Collection([true, false, true], 'string'); // Error
```

## Methods

### Instance

---

#### unshift

---

#### first

---

#### last

---

#### isAssociative

---

#### key

---

#### next

---

#### current

---

#### remove

---

#### removeElement

---

#### offsetExists

---

#### offsetGet

---

#### offsetSet

---

#### offsetUnset

---

#### containsKey

---

#### contains

---

#### exists

---

#### indexOf

---

#### get

---

#### getKeys

---

#### getValues

---

#### count

---

#### set

---

#### add

---

#### isEmpty

---

#### getIterator

---

#### map

---

#### filter

---

#### forAll

---

#### partition

---

#### clear

---

#### slice

---

#### matching

---

#### unique

---

#### merge

---

#### implode

---

#### toArray

---

#### getType

---

#### isTyped

---

#### isOfType

---

#### hasType

---

### Static

---

#### box

Boxes a given variable to a Collection instance.

Any value assigned to the boxed variable behaves as PHP normally does, by creating an array and passing that value as
the first element, except it does to as a collection instead of an array.

`::box(mixed &$pointer)`

**Usage**:

```php
$collection = new Collection([]);
Collection::box($collection);
$collection = ['my', 'new', 'collection'];
assert($collection instanceof Collection); // true
assert(3 === $collection->count()); // true
$collection = new stdClass(); // == new Collection([new stdClass()])
assert(1 === $collection->count()); // true
assert(stdClass::class === $collection->getType()); // true
```

---

#### fromPrimitive

Attempts to create a BoolObject from a primitive value.

`::fromPrimitive(mixed $mixed): Collection`

**Usage**:

```php
$collection = Collection::fromPrimitive('foo');
assert($collection instanceof Collection); // true
assert(1 === $collection->count()); // true
```

---
