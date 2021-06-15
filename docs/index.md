# Types
[![Build Job][github-stable-build-shield]][github stable build]
[![Integration Job][github-int-build-shield]][github integration build]
[![Documentation][rtd-doc-shield]][rtd doc link]
[![License][github-license-shield]][packagist page]
[![Issues][github-issues-shield]][github issues page]
[![Downloads][pkgist-dls-shield]][packagist page]
[![Latest][pkgist-version-shield]][packagist page]

[![Quality Gate Status][sonar-gate-shield]][sonar page]
[![Maintainability Rating][sonar-maint-shield]][sonar page]
[![Reliability Rating][sonar-rel-shield]][sonar page]
[![Security Rating][sonar-sec-shield]][sonar page]
[![Bugs][sonar-bugs-shield]][sonar page]
[![Coverage][sonar-cov-shield]][sonar page]
[![Duplicated Lines (%)][sonar-cpd-shield]][sonar page]
[![Lines of Code][sonar-loc-shield]][sonar page]
[![Technical Debt][sonar-debt-shield]][sonar page]
[![Vulnerabilities][sonar-vul-shield]][sonar page]

<img align="right" src="https://raw.githubusercontent.com/TheDevNetwork/Aux/master/images/php-types.png"  alt="Typing/Types Logo" width="150px" />

Types is a library that provides a collection of useful primitive wrappers, similar to what other languages can do (
Java, etc). It fixes a few issues some internal functions have, and limits coercion around native PHP functions.

---

Below you will find information about the specific types, and the interfaces they expose.

| Class                                   | Type     | Description |
|-----------------------------------------|----------|-------------|
| [BooleanObject]                         | bool     | Base wrapper around primitive with some custom logical string keyword mappings.|
| [Collection]                            | array    | Analogous to Doctrine collections, and implements same interfaces (including Collection interface), but provides **
Typed Collection** functionality. |
| [FloatObject]                           | float    | Provides mathematics functionality, can use 3 different drivers. |
| [IntObject]                             | int      | Provides mathematics functionality, can use 3 different drivers.| 
| [StringObject]                          | string   | Extends Stringy using a multi-language inflector and 3rd party slugifier. |
| <span class="danger-text">[Enum]*</span>| enum     | Extends MyCLabs/Enum and provides a static alias for toArray, syntax sugar for using in attributes. |
| [DateTime]                              | datetime | Extends Carbon with a custom wrapper that can be automatically cast to an ISO 8601 date timestamp. |

!!! danger "*This class might be deprecated after PHP 8.1"
    PHP 8.1 is introducing native Enum structures and this class may no longer be needed.

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

### To Do

* Symfony bundle:
    * Configurable extensions for Math in service container

### What is boxing, and how does it work?

> Note: Boxing is just a feature in this library, and not something you **have** to use.

Ever since PHP 7.4 we've been able to have strict variable typing at the class level (properties), and method/function
level. However, even at the current version (8.0.x) we still cannot have it for variables outside a class, or locally
when declared within class methods. This [blog post] shows examples of how PHP's type system is weak, even
when `declare(strict_types=1);` is called.

There are 2 approaches to boxing. You can start with a primitive, and box it to a type, or start with a type and keep a
variable boxed into that type.

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

In an ideal world, we would do something similar to typescript, or python and the language would auto-box:

Error:

```php
$myString: StringObject = new StringObject();
$myString = new stdClass(); // TypeError
```

Auto:

```php
$myString: StringObject = new StringObject('noop');
$myString = 'fooBarBaz';
echo $myString->dasherize(); //foo-bar-baz
```

## License

This library is released under the MIT license. See the complete license in the [LICENSE](license.md) file.

## Contact

Use the buttons below for issues regarding the library.

<a href="https://github.com/phptyping/types/issues/new"><button class="btn btn-primary btn-lg" type="submit">Report
Issue</button></a> <a href="https://github.com/phptyping/types/issues"><button class="btn btn-primary btn-lg" type="submit">
Active Issues</button></a>

For other issues, reach out to vpassapera [at] linkedin [dot] com.

[PHP bcmath]: https://secure.php.net/manual/en5/book.bc.php
[PHP gmp]: https://secure.php.net/manual/en/book.gmp.php
[BooleanObject]: types/bool-object.md
[Collection]: ./types/collection.md
[FloatObject]: types/float-object.md
[IntObject]: types/int-object.md
[StringObject]: types/string-object.md
[Enum]: ./types/enum.md
[DateTime]: types/date-time.md
[blog post]: https://stitcher.io/blog/what-php-can-be
[rtd doc link]: https://php-types.readthedocs.io/en/latest/?badge=latest
[sonar page]: https://sonarcloud.io/dashboard?id=PhpTyping-types
[packagist page]: https://packagist.org/packages/typing/types
[github issues page]: https://github.com/PhpTyping/Types/issues
[github stable build]: https://github.com/PhpTyping/types/actions/workflows/build-stable.yaml
[github integration build]: https://github.com/PhpTyping/types/actions/workflows/build-integration.yaml
[github-issues-shield]: https://img.shields.io/github/issues/PhpTyping/Types.svg?style=flat-square
[github-license-shield]: https://img.shields.io/github/license/PhpTyping/types?style=flat-square
[github-stable-build-shield]: https://img.shields.io/endpoint?style=flat-square&url=https://gist.githubusercontent.com/vpassapera/027dcddb6a1dc1995a2a47e528aaf020/raw/build-stable.json
[github-int-build-shield]: https://img.shields.io/endpoint?style=flat-square&url=https://gist.githubusercontent.com/vpassapera/73b13bfc6a004696c00552deb44b9e40/raw/build-integration.json
[pkgist-dls-shield]: https://img.shields.io/packagist/dt/typing/types.svg?style=flat-square
[pkgist-version-shield]: https://img.shields.io/packagist/v/typing/types.svg?style=flat-square
[rtd-doc-shield]: https://readthedocs.org/projects/php-types/badge/?version=latest&style=flat-square
[sonar-bugs-shield]: https://sonarcloud.io/api/project_badges/measure?project=PhpTyping-types&metric=bugs&style=flat-square
[sonar-maint-shield]: https://sonarcloud.io/api/project_badges/measure?project=PhpTyping-types&metric=sqale_rating
[sonar-gate-shield]: https://sonarcloud.io/api/project_badges/measure?project=PhpTyping-types&metric=alert_status
[sonar-rel-shield]: https://sonarcloud.io/api/project_badges/measure?project=PhpTyping-types&metric=reliability_rating
[sonar-sec-shield]: https://sonarcloud.io/api/project_badges/measure?project=PhpTyping-types&metric=security_rating
[sonar-cov-shield]: https://sonarcloud.io/api/project_badges/measure?project=PhpTyping-types&metric=coverage
[sonar-cpd-shield]: https://sonarcloud.io/api/project_badges/measure?project=PhpTyping-types&metric=duplicated_lines_density
[sonar-loc-shield]: https://sonarcloud.io/api/project_badges/measure?project=PhpTyping-types&metric=ncloc
[sonar-debt-shield]: https://sonarcloud.io/api/project_badges/measure?project=PhpTyping-types&metric=sqale_index
[sonar-vul-shield]: https://sonarcloud.io/api/project_badges/measure?project=PhpTyping-types&metric=vulnerabilities
