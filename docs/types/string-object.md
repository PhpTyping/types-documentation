# StringObject

* Primitive Type: `string`

## Credits

<a href="https://github.com/doctrine/inflector">
  <img src="https://raw.githubusercontent.com/TheDevNetwork/Aux/master/images/doctrine-logo.png" alt="Doctrine Collections & Doctrine Inflector" width="110px" />
</a>

> Doctrine/Inflector is used for inflection related methods

<a href="https://github.com/danielstjules/Stringy">
  <img src="https://raw.githubusercontent.com/TheDevNetwork/Aux/master/images/stringy.png" alt="Stringy" width="160px" />
</a>

> While Stringy is no longer maintained, the base class is pulled
> into our repo as an abstract class to maintain as a permanent fork.

<a href="https://github.com/cocur/slugify">
  <img src="https://raw.githubusercontent.com/TheDevNetwork/Aux/master/images/slug.png" alt="Slugify" style="max-height: 90px;" />
</a>

> cocur/slugify is used for Slugifying strings.

## Usage

Provides an interface for a string operations. Multibyte support.

**Example**

```php
use Typing\Type\StringObject;


$string = new StringObject('');
```

## Methods

### Instance

#### append

#### at

#### between

#### chars

#### collapseWhitespace

#### contains

#### containsAll

#### containsAny

#### count

#### countSubstr

#### dasherize

#### delimit

#### endsWith

#### endsWithAny

#### ensureLeft

#### ensureRight

#### first

#### getEncoding

#### getIterator

#### hasLowerCase

#### hasUpperCase

#### htmlDecode

#### htmlEncode

#### humanize

#### indexOf

#### indexOfLast

#### insert

#### isAlpha

#### isAlphanumeric

#### isBlank

#### isHexadecimal

#### isJson

#### isLowerCase

#### isSerialized

#### isBase64

#### isUpperCase

#### last

#### length

#### longestCommonPrefix

#### longestCommonSuffix

#### longestCommonSubstring

#### lowerCaseFirst

#### offsetExists

#### offsetGet

#### offsetSet

#### offsetUnset

#### pad

#### padBoth

#### padLeft

#### padRight

#### prepend

#### regexReplace

#### removeLeft

#### removeRight

#### repeat

#### replace

#### reverse

#### safeTruncate

#### shuffle

#### startsWith

#### startsWithAny

#### slice

#### split

#### lines

#### stripWhitespace

#### substr

#### surround

#### swapCase

#### tidy

#### titleize

#### toAscii

#### toLowerCase

#### toSpaces

#### toTabs

#### toTitleCase

#### toUpperCase

#### trim

#### trimLeft

#### trimRight

#### truncate

#### underscored

#### upperCaseFirst

#### __toString

#### getScalarValue

#### explode

#### isEmpty

#### slugify

#### normalize

#### urlize

#### classify

#### upperCamelize

#### tableize

#### capitilize

#### camelize

#### pluralize

#### singularize

#### strpos

#### strrpos

#### isSemVer

#### toDateTime

#### subStrUntil

#### subStrAfter

#### toArray

#### toCollection

#### toInt

#### toIntObject

#### toBool

#### toBoolObject

### Static

#### box

#### create

#### fromPrimitive
