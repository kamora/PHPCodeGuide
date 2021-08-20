# PHP Style Guide

All rules and guidelines in this document apply to PHP files unless otherwise noted. References to PHP/HTML files can be interpreted as files that primarily contain HTML, but use PHP for templating purposes.

> The keywords "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](http://www.ietf.org/rfc/rfc2119.txt).


## Table of Contents

- [**Files**](#files)
	- [Encoding](#encoding)
	- [Line Ends](#line-ends)
	- [File Format](#filename)
- [**Tags**](#php-tags)
	- [Open Tag](#open-tag)
	- [Close Tag](#close-tag)
	- [Short Open Tag](#short-open-tag)
	- [Short Echo Tag](#short-echo-tag)
- [**Namespaces**](#3-namespaces)
	- [Declaration](#1-namespace-declaration)
	- [Definition](#2-namespace-definition)
	- [Multiple Namespaces](#3-multiple-namespaces)
	- [List of imports](#4-list-of-imports)
- [**Comments**](#4-comments)
	- [Single-line Comments](#1-single-line-comments)
	- [Multi-line Comments](#2-multi-line-comments)
	- [PHPDoc Comments](#3-phpdoc-comments)
- [**Formatting**](#5-formatting)
	- [Line Length](#1-line-length)
	- [Indentation](#2-line-indentation)
	- [Keywords](#3-keywords)
	- [Variables](#4-variables)
	- [Constants](#5-constants)
	- [Statements](#6-statements)
	- [Operators](#7-operators)
	- [Unary Operators](#8-unary-operators)
- [**Functions**](#6-functions)
	- [Function Name](#1-function-name)
	- [Function Call](#2-function-call)
	- [Function Arguments](#3-function-arguments)
	- [Function Declaration](#4-function-declaration)
	- [Function Return](#5-function-return)
- [**Control Structures**](#7-control-structures)
	- [If, Elseif, Else](#1-if-elseif-else)
	- [Switch, Case](#2-switch-case)
	- [While, Do While](#3-while-do-while)
	- [For, Foreach](#4-for-foreach)
	- [Try, Catch](#5-try-catch)
- [**Classes**](#8-classes)
	- [Class File](#1-class-file)
	- [Class Namespace](#2-class-namespace)
	- [Class Name](#3-class-name)
	- [Class Prefix](#4-class-prefix)
	- [Class Definition](#5-class-definition)
	- [Extends Keyword](#6-extends-keyword)  
	- [Implements Keyword](#7-implements-keyword)  
	- [Use Keyword](#8-use-keyword)  
	- [Class Properties](#9-class-properties)
	- [Class Methods](#10-class-methods)
	- [Class Instance](#11-class-instance)


## Files
This section describes the format of PHP files.

1. [**Encoding**](#encoding)
2. [**Line Ends**](#line-ends)
3. [**Filename**](#filename)

&#9650; [Table of Contents](#table-of-contents)


### Encoding

* MUST be set to UTF-8 without BOM

&#9650; [Files](#files)


### Line Ends

* MUST be set to Unix (LF)

&#9650; [Files](#files)


### Filename
* MUST follow the [PSR-4](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md) convention 
	* e.g. `Controller.php` but not `controller.php`
* MUST NOT be separated by a hyphen or underscore
	* e.g. `AppConfig.php` but not `app-config.php` or `app_config.php` 

&#9650; [Files](#files)


## PHP Tags

This section describes the use of PHP tags in PHP and PHP/HTML files.

1. [**Open tag**](#open-tag) 
2. [**Close tag**](#close-tag) 
3. [**Short open tag**](#short-open-tag) 
4. [**Short echo tag**](#short-echo-tag) 

&#9650; [Table of Contents](#table-of-contents)


### Open Tag

* MUST be on its own line 
* MUST NOT be followed by a blank line. 

#### &#10006; Incorrect

```php
<?php print_welcome_message();
```

&#8627; Incorrect because `<?php` is not on its own line.

```php
<?php

print_welcome_message();
```

&#8627; Incorrect because `<?php` is followed by a blank line.

#### &#10004; Correct

```php
<?php
print_welcome_message();
```

&#9650; [PHP Tags](#php-tags)


### Close Tag

* MUST NOT be used in PHP files

#### &#10006; Incorrect

```php
<?php
print_welcome_message();
?>
```

&#8627; Incorrect because `?>` was used.

#### &#10004; Correct

```php
<?php
print_welcome_message();
```

&#9650; [PHP Tags](#php-tags)


### Short Open Tag

* MUST NOT be used

#### &#10006; Incorrect

```php
<?
print_welcome_message();
```

&#8627; Incorrect because `<?` was used instead of `<?php`.

#### &#10004; Correct

```php
<?php
print_welcome_message();
```

&#9650; [PHP Tags](#2-php-tags)


### Short Echo Tag

* SHOULD be used inside PHP/HTML files when possible

#### ~ Acceptable

```php
<div>
	<p><?php echo get_welcome_message(); ?</p>
</div>
```

&#8627; Acceptable, but `<?=` should be used over `<?php echo` when possible.

#### &#10004; Preferred

```php
<div>
	<p><?=get_welcome_message();?></p>
</div>
```

&#9650; [PHP Tags](#2-php-tags)


 ## Namespaces

This section describes how to use one or more namespaces and their naming convention.

1. [**Namespace declaration**](#1-namespace-declaration) 
2. [**Namespace definition**](#2-namespace-definition) 
3. [**Multiple namespaces**](#3-multiple-namespaces) 
4. [**List of imports**](#4-list-of-imports)

&#9650; [Table of Contents](#table-of-contents)


### Namespace Declaration

* MUST be the first statement 
* MUST be followed by a blank line

#### &#10006; Incorrect

```php
<?php
print_welcome_message();

namespace SomeNamespace;
```

&#8627; Incorrect because `namespace SomeNamespace` is not the first statement.

```php
<?php
namespace SomeNamespace;
print_welcome_message();
```

&#8627; Incorrect because `namespace SomeNamespace` is not followed by a blank line.

#### &#10004; Correct

```php
<?php
namespace SomeNamespace;

print_welcome_message();
```

&#9650; [Namespaces](#3-namespaces)


### Namespace Definition

* MUST start with a capital letter 
* MUST be camelcased

#### &#10006; Incorrect

```php
<?php
namespace SomeNamespace;

```

&#8627; Incorrect because `SomeNamespace` does not start with a capital letter.

```php
<?php
namespace SomeNAMESPACE;

```

&#8627; Incorrect because `SomeNAMESPACE` is not camelcased.

#### &#10004; Correct

```php
<?php
namespace SomeNamespace;

```

&#9650; [Namespaces](#3-namespaces)


### Multiple Namespaces

* MUST use the curly brace syntax

#### &#10006; Incorrect

```php
<?php
namespace SomeNamespace\Model;

namespace SomeNamespace\View;

```

&#8627; Incorrect because the curly brace syntax was not used.

#### &#10004; Correct

```php
<?php
namespace SomeNamespace\Model {
	// model body
}

namespace SomeNamespace\View {
	// view body
}
```

&#9650; [Namespaces](#3-namespaces)


### List of Imports

* MUST be followed by a blank line
* MUST import a single namespace per declaration
* SHOULD use leading backslashes

#### &#10006; Incorrect

```php
<?php
namespace Core\Models;

use  Core\Facades\Log;
use  Core\Facades\View;
use  Core\Facades\Input;
class Model {
	// ...
}
```

&#8627; Incorrect because not followed by a blank line.

```php
<?php
namespace Core\Models;

use  \Core\Facades\Log, \Core\Facades\View, \Core\Facades\Input;

class Model {
	// ...
}
```

&#8627; Incorrect because the multiple namespaces are imported per declaration.

#### ~ Acceptable

```php
<?php
namespace Core\Models;

use  Core\Facades\Log;
use  Core\Facades\View;
use  Core\Facades\Input;

class Model {
	// ...
}
```

&#8627; Acceptable, but no leading backslashes are using.

#### &#10004; Preferred

```php
<?php
namespace Core\Models;

use  \Core\Facades\Log;
use  \Core\Facades\View;
use  \Core\Facades\Input;

class Model {
	// ...
}
```

&#9650; [Namespaces](#3-namespaces)


 ## Comments

This section describes how comments should be formatted and used.

1. **[Single-line comments](#1-single-line-comments)**
2. **[Multi-line comments](#2-multi-line-comments)**
3. **[PHPDoc comments](#3-phpdoc-comments)** 

&#9650; [Table of Contents](#table-of-contents)


### Single-line Comments

* MUST use two forward slashes
	* e.g. `// The comment`

#### &#10006; Incorrect

```php
<?php
/* This is a comment */
```

&#8627; Incorrect because it uses `/*` and `*/` for a single-line comment.

#### &#10004; Correct

```php
<?php
// This is a comment
```

&#9650; [Comments](#4-comments)


### Multi-line Comments

* MUST use the block format
	* i.e. `/*` `↵` ` The comment` `↵` `*/`

#### &#10006; Incorrect

```php
<?php
// This is a
// multi-line
// comment
 
```

&#8627; Incorrect because it uses `//` for a multi-line comment.

#### &#10004; Correct

```php
<?php
/*
 This is a
 multi-line
 comment
*/

```

&#9650; [Comments](#4-comments)


### PHPDoc Comments
* MUST use the [PHPDoc](https://docs.phpdoc.org/3.0/guide/getting-started/what-is-a-docblock.html) block format.
	* i.e. `/**` `↵` `* The comment` `↵` `*/`

#### &#10006; Incorrect

```php
<?php
/*
 This is a
 multi-line
 comment
*/
```

&#8627; Incorrect because doesn't use the PHPDoc block format.

#### &#10004; Correct

```php
<?php
/**
 * This is a
 * PHPDoc comment 
 */
```

&#9650; [Comments](#4-comments)


 ## Formatting

This section outline various, general formatting rules related to whitespace and text.

1. [**Line length**](#1-line-length)
2. [**Line indentation**](#2-line-indentation) 
3. [**Keywords**](#3-keywords) 
4. [**Variables**](#4-variables) 
9. [**Constants**](#5-constants) 
10. [**Statements**](#6-statements) 
11. [**Operators**](#7-operators) 
12. [**Unary operators**](#8-unary-operators) 

&#9650; [Table of Contents](#table-of-contents)


### Line Length

* MUST NOT be hard limited
* The soft limit MUST be 120 characters
	* i.e. automated style checkers SHOULD warn but MUST NOT error

&#9650; [Formatting](#5-formatting)

### Line Indentation
* MUST be accomplished using tabs
	* i.e. space characters are strictly not allowed for indentation

&#9650; [Formatting](#5-formatting)


### Keywords

* MUST be all lowercased
	* e.g. `false`, `true`, `null`, etc.

#### &#10006; Incorrect

```php
<?php
$isTrue = FALSE;
$isFalse = TRUE:
$value = NULL;
```

&#8627; Incorrect because `FALSE`, `TRUE` and `NULL` are not all lowercased.

#### &#10004; Correct

```php
<?php
$isTrue = false;
$isFalse = true:
$value = null;
```

&#9650; [Formatting](#5-formatting)


### Variables

* MUST be all camelcased 
* MUST NOT be separated by underscores
* Variables of object type MUST starts from a capital letter
* Variables of primitive types MUST starts from a lowercase letter
* Arrays MAY be tract both: as primitives or as objects

#### &#10006; Incorrect

```php
<?php
$welcome_message = '';
$WelcomeMESSAGE = '';
```

&#8627; Incorrect because variables are not camelcased properly.

```php
<?php
$WelcomeMessage = '';
```

&#8627; Incorrect because the variable contains a primitive type but starts from an uppercase letter.

```php
<?php
$someObject = new SomeClass();
```

&#8627; Incorrect because the variable contains an object but doesn't start from an uppercase letter.

#### &#10004; Correct

```php
<?php
$welcomeMessage = '';
$SomeObject = new SomeClass();
```

&#9650; [Formatting](#5-formatting)


### Constants

* MUST be all uppercased 
* MUST be separated by underscores

#### &#10006; Incorrect

```php
<?php
define('welcome_Message', '');
define('Welcome_Message', '');
define('welcome_message', '');
```

&#8627; Incorrect because the constants are not all uppercase.

```php
<?php
define('WELCOMEMESSAGE', '');
```

&#8627; Incorrect because `WELCOME` and `MESSAGE` are not separated by an underscore.

#### &#10004; Correct

```php
<?php
define('WELCOME_MESSAGE', '');
```

&#9650; [Formatting](#5-formatting)


### Statements

* MUST be placed on their own line
* MUST end with a semicolon

#### &#10006; Incorrect

```php
<?php
$isFalse = false; print_welcome_message();
```

&#8627; Incorrect because the statements are on the same line.

#### &#10004; Correct

```php
<?php
$isFalse = false;
print_welcome_message();
```

&#9650; [Formatting](#5-formatting)


### Operators

* MUST be surrounded by a space

#### &#10006; Incorrect

```php
<?php
$total=3+14;
$string='Hello, World! ';
$string.='Today is a good day!';
echo 'Hello, World! Today is '.$date.'!';
```

&#8627; Incorrect because there is no space surrounding the `=`, `+`, `.` or `.=` sign.

#### &#10004; Correct

```php
<?php
$total = 3 + 14;
$string = 'Hello, World! ';
$string .= 'Today is a good day!';
echo 'Hello, World! Today is ' . $date . '!';
```

&#9650; [Formatting](#5-formatting)


### Unary Operators

* MUST be attached to the operand.

#### &#10006; Incorrect

```php
<?php
$index ++;
-- $index;
```

&#8627; Incorrect because there is a space before `++` and after `--`.

#### &#10004; Correct

```php
<?php
$index++;
--$index;
```

&#9650; [Formatting](#5-formatting)


 ## Functions

This section describes the format for function names, calls, arguments and declarations.

1. [**Function name**](#1-function-name) 
2. [**Function call**](#2-function-call)
3. [**Function arguments**](#3-function-arguments)
4. [**Function declaration**](#4-function-declaration) 
5. [**Function return**](#5-function-return)

&#9650; [Table of Contents](#table-of-contents)


### Function Name

* MUST start from a lowercase letter
* MUST be all camelcased
* MUST NOT be separated by underscores

#### &#10006; Incorrect

```php
<?php
get_WelcomeMessage();
GetWelcomeMessage();
GET_WELCOME_MESSAGE();
getwelcomemessage();
```

&#8627; Incorrect because the function names are not all properly camelcased or separated by underscores.

#### &#10004; Correct

```php
<?php
getWelcomeMessage();
```

&#9650; [Functions](#6-functions)


### Function Call

* MUST NOT have a space between function name and open parenthesis

#### &#10006; Incorrect

```php
<?php
printWelcomeMessage ();
```

&#8627; Incorrect because there is a space between `getWelcomeMessage` and `()`.

#### &#10004; Correct

```php
<?php
printWelcomeMessage();
```

&#9650; [Functions](#6-functions)


### Function Arguments

* MUST NOT have a space before the comma
* MUST have a space after the comma 
* SHOULD be type-hinted if possible
* MAY use line breaks for long arguments

#### &#10006; Incorrect

```php
<?php
someFunction($arg1 , $arg2 , $arg3) {
	// ...
}
```

&#8627; Incorrect because there is a space before `,`.

```php
<?php
someFunction($arg1,$arg2,$arg3) {
	// ...
}
```

&#8627; Incorrect because there is no space after `,`.

#### ~ Acceptable

```php
<?php
function addUsersToOffice($users, $Office) {
	// ...
}
```

&#8627; Acceptable, but `$users` and `$office` are missing their data types.

#### &#10004; Preferred

```php
<?php
function addUsersToOffice(array $users, Office $Office): bool {
	// ...
}
```

&#9650; [Functions](#6-functions)


### Function Declaration

* SHOULD be documented via [phpDOC](http://phpdoc.org/docs/latest/index.html) and SHOULD include but not be limited by:
	* short description if needed
	* argument data type and name
	* return data type, if applicable
	* throwable exceptions if any

#### ~ Acceptable

```php
<?php
function someFunction(int $id, int $width, int $height): Photo {
	// ...
}
```

&#8627; Acceptable but the function is not documented.

#### &#10004; Preferred

```php
<?php
/**
 * Get profile photo of a customer
 *
 * @param int $id 
 * @param int $width 
 * @param int $height
 * @return string
 *
 * @throws AccessDeniedException
 */
function someFunction(int $id, int $width, int $height): string {
	// ...
}
```

&#9650; [Functions](#6-functions)


### Function Return

* MUST be type-hinted if applicable

#### &#10006; Incorrect

```php
<?php
function getValue() {
	// ...
}
```

&#8627; Incorrect because the return type is not hinted.

#### &#10004; Correct

```php
<?php
function getValue(): string {
	// ...
}
```

&#9650; [Functions](#6-functions)


 ## Control Structures
This section defines the layout and usage of control structures. Note that this section is separated into rules that are applicable to all structures, followed by specific rules for individual structures.

* **Keyword** MUST be followed by a space
	* e.g. `if (`, `switch (`, `do {`, `for (`
* **Opening parenthesis** MUST NOT be followed by a space
	* e.g. `($expr`, `($i`
* **Closing parenthesis** MUST NOT be preceded by a space
	* e.g. `$expr)`, `$i++)`, `$value)`
* **Opening brace** MUST be placed on the same line, preceded by a space and followed by a new line
	* e.g. `$expr) { ` `↵`, `$i++) {` `↵`, 
* **Structure body** MUST be indented once and MUST be enclosed with curly braces
	* e.g. `if ($expr) {` `↵` `⇥` `...` `↵` `}`
* **Closing brace** MUST start on the next line
	* i.e. `...` `↵` `}`

In addition to the rules above, some control structures have additional requirements:

1. [**If, Elseif, Else**](#1-if-elseif-else)
2. [**Switch, Case**](#2-switch-case)
3. [**While, Do While**](#3-while-do-while)
4. [**For, Foreach**](#4-for-foreach)
5. [**Try, Catch**](#5-try-catch)

&#9650; [Table of Contents](#table-of-contents)


### If, Elseif, Else
* `elseif` MUST be used instead of `else if`
* `elseif` or `else` MUST be between `}` and `{` on one line

#### &#10006; Incorrect

```php
<?php
if ($expr1) {
	// if body
} else if ($expr2) {
	// elseif body
} else {
	// else body
}
```

&#8627; Incorrect because `else if` was used instead of `elseif`.

```php
<?php
if ($expr1) {
	// if body
}
elseif ($expr2) {
	// elseif body
}
else {
	// else body
}
```

&#8627; Incorrect because `elseif` or `else` are not between `}` and `{` on one line.

```php
<?php
if($expr)
	$result = 100;
```

&#8627; Incorrect because structure body is not wrapped in curly braces.

#### &#10004; Correct

```php
<?php
if ($expr1) {
	// if body
} elseif ($expr2) {
	// elseif body
} else {
	// else body
}
```

&#9650; [Control Structures](#7-control-structures)


### Switch, Case

* Case statement MUST be indented once
	* i.e. `⇥` `case 1:`
* Case body MUST be indented twice
	* i.e. `⇥` `⇥` `func();`
* Break keyword MUST be indented twice
	* i.e. `⇥` `⇥` `break;`

#### &#10006; Incorrect

```php
<?php
switch ($expr) {
case 0:
	echo 'First case, with a break';
	break;

case 1:
	echo 'Second case, which falls through';
	// no break
case 2:
case 3:
case 4:
	echo 'Third case, return instead of break';
	return;

default:
	echo 'Default case';
	break;
}
```

&#8627; Incorrect because statements are not indented once.

```php
<?php
switch ($expr) {
	case 0:
	echo 'First case, with a break';
	break;

	case 1:
	echo 'Second case, which falls through';
	// no break
	case 2:
	case 3:
	case 4:
	echo 'Third case, return instead of break';
	return;

	default:
	echo 'Default case';
	break;
}
```

&#8627; Incorrect because body is not indented twice.

#### &#10004; Correct

```php
<?php
switch ($expr) {
	case 0:
		echo 'First case, with a break';
		break;

	case 1:
		echo 'Second case, which falls through';
		// no break
	case 2:
	case 3:
	case 4:
		echo 'Third case, return instead of break';
		return;

	default:
		echo 'Default case';
		break;
}
```

&#9650; [Control Structures](#7-control-structures)


### While, Do While

#### &#10004; Correct

```php
<?php
while ($expr) {
	// ...
}

do {
	// ...
} while ($expr);
```

&#9650; [Control Structures](#7-control-structures)


### For, Foreach

#### &#10004; Correct

```php
<?php
for ($i = 0; $i < 10; $i++) {
	// ...
}

foreach ($iterable as $key => $value) {
	// ...
}
```

&#9650; [Control Structures](#7-control-structures)


### Try, Catch

* `catch` MUST be between `}` and `{` on one line

#### &#10006; Incorrect

```php
<?php
try {
	// ...
}
catch (FirstExceptionType $Exception) {
	// ...
}
catch (OtherExceptionType $Exception) {
	// ...
}
```

&#8627; Incorrect because `catch` is not between `}` and `{` on one line.

#### &#10004; Correct

```php
<?php
try {
	// ...
} catch (FirstExceptionType $Exception) {
	// ...
} catch (OtherExceptionType $Exception) {
	// ...
}
```

&#9650; [Control Structures](#7-control-structures)


 ## Classes

This section describes class files, names, definitions, properties, methods and instantiation.

1. [**Class file**](#1-class-file)
2. [**Class namespace**](#2-class-namespace) 
3. [**Class name**](#3-class-name) 
4. [**Class prefix**](#4-class-prefix)
5. [**Class definition**](#5-class-definition) 
6. [**Extends keyword**](#6-extends-keyword)
7. [**Implements keyword**](#7-implements-keyword)
8. [**Use keyword**](#8-use-keyword)
9. [**Class properties**](#9-class-properties)
10. [**Class methods**](#10-class-methods)
11. [**Class instance**](#11-class-instance)

&#9650; [Table of Contents](#table-of-contents)


### Class File

*  MUST only contain one definition

#### &#10006; Incorrect

```php
<?php
namespace Core\Models;

class User {
	// ...
}

class Office {
	// ...
}
```

&#8627; Incorrect because two classes are defined in one file.

#### &#10004; Correct
```php
<?php
namespace Core\Models;

class User {
	// ...
}
```

&#9650; [Classes](#8-classes)


### Class Namespace

* MUST be defined

#### &#10006; Incorrect

```php
<?php
class User {
	// ...
}
```

&#8627; Incorrect because there is no namespace defined.

#### &#10004; Correct

```php
<?php
namespace Core\Models;

class User {
	// ...
}
```

&#9650; [Classes](#8-classes)


### Class Name

* MUST start with a capital letter 
* MUST be camelcased

#### &#10006; Incorrect

```php
<?php
namespace Core\Models;
class officeProgram {
	// ...
}
```

&#8627; Incorrect because the class name doesn't start with a capital letter.

```php
<?php
namespace Core\Models;

class Officeprogram {
	// ...
}
```

&#8627; Incorrect because the class name is not camelcased.

#### &#10004; Correct

```php
<?php
namespace Core\Models;

class OfficeProgram {
	// ...
}
```

&#9650; [Classes](#8-classes)


### Class Prefix

The following prefix notation SHOULD be used:

* `A` for abstract classes
	* e.g. `AController`, `APrototype`, etc
* `I` for interfaces
	* e.g. `ICountable`, `IBehavior`, etc
* `T` for traits
	* e.g. `TString`, `TNotation`, etc
* `E` for exceptions
	* e.g. `EInbvalidArgument`, `EUndefinedVariable`, etc

#### &#10004; Correct

```php
<?php
namespace Core\Models\Abstractions;

abstract class AModel {
	// ...
}
```

```php
<?php
namespace Core\Interfaces;

interface ICountable {
	// ...
}
```

&#9650; [Classes](#8-classes)


### Class Definition

* The opening curly brace MUST be placed on the same line
	* i.e. `class User` `·` `{` `↵` `...` `↵` `}`

#### &#10006; Incorrect

```php
<?php
namespace Core\Models;

class User 
{
	// ...
}
```

&#8627; Incorrect because `{` is not on the same line.

#### &#10004; Correct

```php
<?php
namespace Core\Models;

class User {
	// ...
}
```

&#9650; [Classes](#8-classes)


### `Extends` Keyword

* MUST be placed on the same line

#### &#10006; Incorrect

```php
<?php
namespace Core\Models;

class User 
	extends APrototype {
	// ...
}
```

&#8627; Incorrect because the `extends` keyword is not on the same line.

#### &#10004; Correct

```php
<?php
namespace Core\Models;

class User extends APrototype {
	// ...
}
```

&#9650; [Classes](#8-classes)



### `Implements` keyword

* SHOULD be moved to the next line

#### ~ Acceptable

```php
<?php
namespace Core\Models;

class User extends APrototype implements Countable {
	// ...
}
```

&#8627; Incorrect because the `implements` keyword is not on the new line.

#### &#10004; Preferred

```php
<?php
namespace Core\Models;

class User extends APrototype 
	implements Countable {
	// ...
}
```

&#9650; [Classes](#8-classes)


### `Use` keyword

* MUST include a single trait per line 

#### &#10006; Incorrect

```php
<?php
namespace Core\Models;

use \Core\Traits\TNumeric;
use \Core\Traits\TCountable;

class User extends APrototype 
	implements Countable {

	use TCountable, TNumeric; 
	// ...
}
```

&#8627; Incorrect because two traits are included per line.

#### &#10004; Correct

```php
<?php
namespace Core\Models;

use \Core\Traits\TNumeric;
use \Core\Traits\TCountable;

class User extends APrototype 
	implements Countable {

	use TCountable;
	use TNumeric; 
	// ...
}
```

&#9650; [Classes](#8-classes)


### Class Properties

* MUST follow [variable standards](#4-variables)
* MUST specify visibility
* MUST NOT be prefixed with an underscore
* SHOULD be type-hinted if possible

#### &#10006; Incorrect

```php
<?php
namespace Core\Models;

class User {
	// Public
	$var1;

	// Protected
	$var2;

	// Private
	$var3;
}
```

&#8627; Incorrect because visibility is not specified.

```php
<?php
namespace Core\Models;

class User {
	public $var1;
	protected $_var2;
	private $_var3;
}
```

&#8627; Incorrect because some properties are prefixed by the underscore.

#### ~ Acceptable

```php
<?php
namespace Core\Models;

class User {
	public $var1;
	protected $var2;
	private $var3;
}
```

&#8627; Acceptable, but the properties are not type-hinted.

#### &#10004; Preferred

```php
<?php
namespace Core\Models;

class User {
	public int $var1;
	protected string $var2;
	private bool $var3;
}
```

&#9650; [Classes](#8-classes)


### Class Methods

* MUST follow [function standards](#6-functions)
* MUST specify visibility
* MUST NOT be prefixed with an underscore

#### &#10006; Incorrect

```php
<?php
namespace Core\Models;

class User {
	// ...

	// Public
	function getVar1(): int {
		return $this->var1;
	}

	// Protected
	function getVar2(): string {
		return $this->var2;
	}

	// Private
	function getVar3(): bool {
		return $this->var3;
	}
}
```

&#8627; Incorrect because visibility is not specified.

```php
<?php
namespace Core\Models;

class User {
	// ...

	public function getVar1(): int {
		return $this->var1;
	}

	protected function _getVar2(): string {
		return $this->var2;
	}

	private function _getVar3(): bool {
		return $this->var3;
	}
}
```

&#8627; Incorrect because some methods are prefixed by the underscore.

#### &#10004; Correct

```php
<?php
namespace Core\Models;

class User {
	// ...

	public function getVar1(): int {
		return $this->var1;
	}

	protected function getVar2(): string {
		return $this->var2;
	}

	private function getVar3(): bool {
		return $this->var3;
	}
}
```

&#9650; [Classes](#8-classes)


### Class Instance

* MUST start with a capital letter
* MUST be camelcased
* MUST include parenthesis

#### &#10006; Incorrect

```php
<?php
$office_program = new OfficeProgram;
```

&#8627; Incorrect because a lack of parenthesis.

#### &#10004; Correct

```php
<?php
$office_program = new OfficeProgram();
```

&#9650; [Classes](#8-classes)

