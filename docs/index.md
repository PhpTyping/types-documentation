<img align="right" src="https://raw.githubusercontent.com/TheDevNetwork/Aux/master/images/gandalf.png"  alt="Typing/Types Logo"/>

# Types

[![Documentation Status](https://readthedocs.org/projects/types-documentation/badge/?version=latest&style=flat-square)](https://types-documentation.readthedocs.io/en/latest/?badge=latest)
[![GitHub issues][github issues]][issues page]
[![Total Downloads][downloads shield]][packagist page]
[![License][license shield]][packagist page]
[![Latest Stable Version][latest version shield]][packagist page]
[![Travis][travis build shield]][travis page]
[![Coverage Status][coveralls badge]][coveralls page]

Types is a library that provides a collection of useful primitive wrappers, similar to
what other languages can do (Java, etc). It fixes a few issues some internal functions have,
and limits coercion around native PHP functions.

---

Below you will find information about the specific types, and the interfaces
they expose.

| Class           | Type     | Description |
|-----------------|----------|-------------|
| [BooleanObject] | bool     | Base wrapper around primitive with some custom logical string keyword mappings.|
| [Collection]    | array    | Analogous to Doctrine collections, and implements same interfaces (including Collection interface), but provides **Typed Collection** functionality. |
| [FloatObject]   | float    | Provides mathematics functionality, can use 3 different drivers. |
| [IntObject]     | int      | Provides mathematics functionality, can use 3 different drivers.| 
| [StringObject]  | string   | Extends Stringy using a multi-language inflector and 3rd party slugifier. |
| [Enum]          | enum     | Extends MyCLabs/Enum and provides a static alias for toArray, syntax sugar for using in attributes. |
| [DateTime]      | datetime | Extends Carbon with a custom wrapper that can be automatically cast to an ISO 8601 date timestamp. |

## Installation

Using CLI:

```bash
composer require typing/types:*@stable
```

Or directly on the `composer.json` file:

```json
{
    "require": {
        "typing/types": "*@stable"
    }
}
```

See https://getcomposer.org/ for more information and documentation.

## Requirements

* `PHP >= 8.0`

### Optional

* [PHP bcmath]
* [PHP gmp]

## Features

* Rich interfaces exposing native PHP functions while fixing quirks, return values, etc.
* Multi-byte support
* Sane transmutation
* Explicit boxing of variable types, with very limited coercion.

### How does boxing work?

Ever since PHP 7.4 we've been able to have strict variable typing at the class level (properties). However, even
at the current version (8.0.x) we still cannot have it for variables outside a class, or locally when declared within
class methods.

There are 2 approaches to boxing. You can start with a primitive, and box it to a type, or start with a type
and keep a variable boxed into that type.

**Examples**:

Starting as a type...
```php
$myString = new StringObject('');
StringObject::box($myString);
$myString = 'my_new_value'; // This is still an instance of StringObject.
$myString->dasherize(); // my-new-value
$myString = new stdClass(); // TypeError.
```

Starting as a primitive...

```php
$myString = 'This is my string, there are many like it, but this one is mine.';
StringObject::box($myString);
assert($myString instanceof StringObject); // true
$myString->dasherize(); // this-is-my-string...
$myString = new stdClass(); // TypeError.
```

## License

This library is released under the MIT license. See the complete license in the [LICENSE](../LICENSE) file.

## Contact

Reach out to vpassapera [at] linkedin [dot] com.

[PHP bcmath]: https://secure.php.net/manual/en5/book.bc.php
[PHP gmp]: https://secure.php.net/manual/en/book.gmp.php
[BooleanObject]: types/bool-object.md
[Collection]: ./types/collection.md
[FloatObject]: types/float-object.md
[IntObject]: types/int-object.md
[StringObject]: types/string-object.md
[Enum]: ./types/enum.md
[DateTime]: types/date-time.md
[github issues]: https://img.shields.io/github/issues/PhpTyping/Types.svg?style=flat-square
[issues page]: https://github.com/PhpTyping/Types/issues
[downloads shield]: https://img.shields.io/packagist/dt/typing/types.svg?style=flat-square
[license shield]: https://img.shields.io/packagist/l/typing/types.svg?style=flat-square
[latest version shield]: https://img.shields.io/packagist/v/typing/types.svg?style=flat-square
[packagist page]: https://packagist.org/packages/typing/types
[travis build shield]: https://img.shields.io/travis/PhpTyping/Types.svg?style=flat-square
[travis page]: https://travis-ci.org/PhpTyping/Types
[coveralls badge]: https://img.shields.io/coveralls/PhpTyping/Types/develop.svg?style=flat-square
[coveralls page]: https://coveralls.io/github/PhpTyping/Types?branch=develop
