# Collection

* Primitive Type: `array`

## Credits

<a href="https://github.com/doctrine">
  <img src="https://raw.githubusercontent.com/TheDevNetwork/Aux/master/images/doctrine-logo.png" alt="Doctrine Collections & Doctrine Inflector" width="100px" />
</a>

> This class exposes the same API as Doctrine's ArrayCollection class, with extra functionality.

## Usage

Provides a wrapper around arrays that exposes most if not all native array functions.
Also implements the following interfaces:

**Native**

* `Countable`
* `IteratorAggregate`
* `ArrayAccess`

**Library**

* `Doctrine\Common\Collections\Collection`

**Example**

```php
<?php

namespace Foo;

use Typing\Type\Collection;
use Typing\Type\StringObject;

$typedCollection = new Collection(['foo', 'bar'], StringObject::class); // A collection of StringObjects
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

#### unshift

#### first

#### last

#### isAssociative

#### key

#### next

#### current

#### remove

#### removeElement

#### offsetExists

#### offsetGet

#### offsetSet

#### offsetUnset

#### containsKey

#### contains

#### exists

#### indexOf

#### get

#### getKeys

#### getValues

#### count

#### set

#### add

#### isEmpty

#### getIterator

#### map

#### filter

#### forAll

#### partition

#### clear

#### slice

#### matching

#### unique

#### merge

#### implode

#### toArray

#### getType

#### isTyped

#### isOfType

#### hasType

### Static

#### fromPrimitive

#### box
