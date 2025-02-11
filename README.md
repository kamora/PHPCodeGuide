# PHP Style Guide

All rules and guidelines in this document apply to PHP files unless otherwise noted.

> The keywords "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](http://www.ietf.org/rfc/rfc2119.txt).


## Table of Contents

- [Encoding](#encoding)
- [Filename](#filenames)
- [Indentation](#indentation)
- [Line Endings](#line-endings)
- [Line Length](#line-length)
- [Opening Tag](#opening-tag)
- [Short Opening Tag](#short-opening-tag)
- [Closing Tag](#closing-tag)
- [Echo Tag](#echo-tag)
- [Namespace Declaration](#namespace-declaration)
- [Multiple Namespaces](#multiple-namespaces)
- [Imports](#imports)
- [Single-line Comments](#single-line-comments)
- [Multi-line Comments](#multi-line-comments)
- [PHPDoc](#phpdoc)
- [Keywords](#keywords)
- [Variables](#variables)
- [Constants](#constants)
- [Statements](#statements)
- [Operators](#operators)
- [Unary Operators](#unary-operators)
- [Function Name](#function-name)
- [Function Calls](#function-calls)
- [Function Arguments](#function-arguments)
- [Function Declaration](#function-declaration)
- [Function Return](#function-return)
- [Control Structures](#control-structures)
- [If, Elseif, Else](#if-elseif-else)
- [Switch, Case](#switch-case)
- [While, Do While](#while-do-while)
- [For, Foreach](#for-foreach)
- [Try, Catch](#try-catch)
- [Class File](#class-file)
- [Class Namespace](#class-namespace)
- [Class Name](#class-name)
- [Class Prefix](#class-prefix)
- [Class Definition](#class-definition)
- [`Extends` Keyword](#extends-keyword)  
- [`Implements` Keyword](#implements-keyword)  
- [`Use` Keyword](#use-keyword)  
- [Class Properties](#class-properties)
- [Class Methods](#class-methods)
- [Class Instance](#class-instance)


## Encoding
* MUST be set to UTF-8 without BOM

&#9650; [Table of Contents](#table-of-contents)


## Filenames
* MUST follow the [PSR-4](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md) convention 
	* e.g. `Controller.php` but not `controller.php`
* MUST NOT be separated by a hyphen or underscore
	* e.g. `AppConfig.php` but not `app-config.php` or `app_config.php` 

&#9650; [Table of Contents](#table-of-contents)


## Indentation
* MUST be accomplished using tabs
	* i.e. space characters are strictly **not allowed** for indentation

&#9650; [Table of Contents](#table-of-contents)


## Line Endings
* MUST be set to Unix (LF)

&#9650; [Table of Contents](#table-of-contents)


## Line Length
* MUST NOT be hard limited
* The soft limit MUST be 120 characters
	* i.e. automated style checkers SHOULD warn but MUST NOT error

&#9650; [Table of Contents](#table-of-contents)


## Opening Tag
* MUST be on its own line 
* MUST NOT be followed by a blank line. 

### &#10006; Incorrect

```php
<?php print_welcome_message();
```

&#8627; Incorrect because `<?php` is not on its own line.

```php
<?php

print_welcome_message();
```

&#8627; Incorrect because `<?php` is followed by a blank line.

### &#10004; Correct

```php
<?php
print_welcome_message();
```

&#9650; [Table of Contents](#table-of-contents)


## Short Opening Tag
* MUST NOT be used

### &#10006; Incorrect

```php
<?
print_welcome_message();
```

&#8627; Incorrect because `<?` was used instead of `<?php`.

### &#10004; Correct

```php
<?php
print_welcome_message();
```

&#9650; [Table of Contents](#table-of-contents)


## Closing Tag
* MUST NOT be used in PHP files

### &#10006; Incorrect

```php
<?php
print_welcome_message();
?>
```

&#8627; Incorrect because `?>` was used.

### &#10004; Correct

```php
<?php
print_welcome_message();
```

&#9650; [Table of Contents](#table-of-contents)

## Echo Tag
* SHOULD be used inside PHP/HTML files when possible

### ~ Acceptable

```php
<div>
	<p><?php echo get_welcome_message(); ?</p>
</div>
```

&#8627; Acceptable, but `<?=` should be used over `<?php echo` when possible.

### &#10004; Preferred

```php
<div>
	<p><?=get_welcome_message();?></p>
</div>
```

&#9650; [Table of Contents](#table-of-contents)


## Namespace Declaration
* MUST be the first statement 
* MUST be followed by a blank line
* MUST start with a capital letter 
* MUST be camelcased

### &#10006; Incorrect

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

### &#10004; Correct

```php
<?php
namespace SomeNamespace;

print_welcome_message();
```

### &#10006; Incorrect

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

### &#10004; Correct

```php
<?php
namespace SomeNamespace;

```

&#9650; [Table of Contents](#table-of-contents)


## Multiple Namespaces
* SHOULD be avoided if possible
* MUST use the curly brace syntax

### &#10006; Incorrect

```php
<?php
namespace SomeNamespace\Model;

namespace SomeNamespace\View;

```

&#8627; Incorrect because the curly brace syntax was not used.

### &#10004; Correct

```php
<?php
namespace SomeNamespace\Model {
	// model body
}

namespace SomeNamespace\View {
	// view body
}
```

&#9650; [Table of Contents](#table-of-contents)


## Imports
* MUST be followed by a blank line
* MUST import a single namespace per declaration
* SHOULD use leading backslashes

### &#10006; Incorrect

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

### ~ Acceptable

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

### &#10004; Preferred

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

&#9650; [Table of Contents](#table-of-contents)


## Single-line Comments
* MUST use two forward slashes
	* e.g. `// The comment`

### &#10006; Incorrect

```php
<?php
/* This is a comment */
```

&#8627; Incorrect because it uses `/*` and `*/` for a single-line comment.

### &#10004; Correct

```php
<?php
// This is a comment
```

&#9650; [Table of Contents](#table-of-contents)


## Multi-line Comments
* MUST use the block format
	* i.e. `/*` `↵` ` The comment` `↵` `*/`

### &#10006; Incorrect

```php
<?php
// This is a
// multi-line
// comment
 
```

&#8627; Incorrect because it uses `//` for a multi-line comment.

### &#10004; Correct

```php
<?php
/*
 This is a
 multi-line
 comment
*/

```

&#9650; [Table of Contents](#table-of-contents)


## PHPDoc
* MUST use the [PHPDoc](https://docs.phpdoc.org/3.0/guide/getting-started/what-is-a-docblock.html) block format.
	* i.e. `/**` `↵` `* The comment` `↵` `*/`

### &#10006; Incorrect

```php
<?php
/*
 This is a
 multi-line
 comment
*/
```

&#8627; Incorrect because doesn't use the PHPDoc block format.

### &#10004; Correct

```php
<?php
/**
 * This is a
 * PHPDoc comment 
 */
```

&#9650; [Table of Contents](#table-of-contents)


## Keywords
* MUST be all lowercased
	* e.g. `false`, `true`, `null`, etc.

### &#10006; Incorrect

```php
<?php
$isTrue = FALSE;
$isFalse = TRUE:
$value = NULL;
```

&#8627; Incorrect because `FALSE`, `TRUE` and `NULL` are not all lowercased.

### &#10004; Correct

```php
<?php
$isTrue = false;
$isFalse = true:
$value = null;
```

&#9650; [Table of Contents](#table-of-contents)


## Variables
* MUST be all camelcased 
* MUST NOT be separated by underscores
* Variables of object type MUST starts from a capital letter
* Variables of primitive types MUST starts from a lowercase letter
* Arrays MAY be tract both: as primitives or as objects

### &#10006; Incorrect

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

### &#10004; Correct

```php
<?php
$welcomeMessage = '';
$SomeObject = new SomeClass();
```

&#9650; [Table of Contents](#table-of-contents)


## Constants
* MUST be all uppercased 
* MUST be separated by underscores

### &#10006; Incorrect

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

### &#10004; Correct

```php
<?php
define('WELCOME_MESSAGE', '');
```

&#9650; [Table of Contents](#table-of-contents)


## Statements
* MUST be placed on their own line
* MUST end with a semicolon

### &#10006; Incorrect

```php
<?php
$isFalse = false; print_welcome_message();
```

&#8627; Incorrect because the statements are on the same line.

### &#10004; Correct

```php
<?php
$isFalse = false;
print_welcome_message();
```

&#9650; [Table of Contents](#table-of-contents)


## Operators
* MUST be surrounded by a space

### &#10006; Incorrect

```php
<?php
$total=3+14;
$string='Hello, World! ';
$string.='Today is a good day!';
echo 'Hello, World! Today is '.$date.'!';
```

&#8627; Incorrect because there is no space surrounding the `=`, `+`, `.` or `.=` sign.

### &#10004; Correct

```php
<?php
$total = 3 + 14;
$string = 'Hello, World! ';
$string .= 'Today is a good day!';
echo 'Hello, World! Today is ' . $date . '!';
```

&#9650; [Table of Contents](#table-of-contents)


## Unary Operators
* MUST be attached to the operand.

### &#10006; Incorrect

```php
<?php
$index ++;
-- $index;
```

&#8627; Incorrect because there is a space before `++` and after `--`.

### &#10004; Correct

```php
<?php
$index++;
--$index;
```

&#9650; [Table of Contents](#table-of-contents)


## Function Name
* MUST start from a lowercase letter
* MUST be all camelcased
* MUST NOT be separated by underscores

### &#10006; Incorrect

```php
<?php
get_WelcomeMessage();
GetWelcomeMessage();
GET_WELCOME_MESSAGE();
getwelcomemessage();
```

&#8627; Incorrect because the function names are not all properly camelcased or separated by underscores.

### &#10004; Correct

```php
<?php
getWelcomeMessage();
```

&#9650; [Table of Contents](#table-of-contents)


## Function Calls
* MUST NOT have a space between function name and open parenthesis

### &#10006; Incorrect

```php
<?php
printWelcomeMessage ();
```

&#8627; Incorrect because there is a space between `getWelcomeMessage` and `()`.

### &#10004; Correct

```php
<?php
printWelcomeMessage();
```

&#9650; [Table of Contents](#table-of-contents)


## Function Arguments
* MUST NOT have a space before the comma
* MUST have a space after the comma 
* SHOULD be type-hinted if possible
* MAY use line breaks for long arguments

### &#10006; Incorrect

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

### ~ Acceptable

```php
<?php
function addUsersToOffice($users, $Office) {
	// ...
}
```

&#8627; Acceptable, but `$users` and `$office` are missing their data types.

### &#10004; Preferred

```php
<?php
function addUsersToOffice(array $users, Office $Office): bool {
	// ...
}
```

&#9650; [Table of Contents](#table-of-contents)


## Function Declaration
* SHOULD be documented via [phpDOC](http://phpdoc.org/docs/latest/index.html) and SHOULD include but not be limited by:
	* short description if needed
	* argument data type and name
	* return data type, if applicable
	* throwable exceptions if any

### ~ Acceptable

```php
<?php
function someFunction(int $id, int $width, int $height): Photo {
	// ...
}
```

&#8627; Acceptable but the function is not documented.

### &#10004; Preferred

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

&#9650; [Table of Contents](#table-of-contents)


## Function Return
* MUST be type-hinted if applicable

### &#10006; Incorrect

```php
<?php
function getValue() {
	// ...
}
```

&#8627; Incorrect because the return type is not hinted.

### &#10004; Correct

```php
<?php
function getValue(): string {
	// ...
}
```

&#9650; [Table of Contents](#table-of-contents)


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

&#9650; [Table of Contents](#table-of-contents)


## If, Elseif, Else
* MUST follow the [control structures standards](#control-structures)
* `elseif` MUST be used instead of `else if`
* `elseif` or `else` MUST be between `}` and `{` on one line

### &#10006; Incorrect

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

### &#10004; Correct

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

&#9650; [Table of Contents](#table-of-contents)


## Switch, Case
* MUST follow the [control structures standards](#control-structures)
* Case statement MUST be indented once
	* i.e. `⇥` `case 1:`
* Case body MUST be indented twice
	* i.e. `⇥` `⇥` `func();`
* Break keyword MUST be indented twice
	* i.e. `⇥` `⇥` `break;`

### &#10006; Incorrect

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

### &#10004; Correct

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

&#9650; [Table of Contents](#table-of-contents)


## While, Do While
* MUST follow the [control structures standards](#control-structures)

### &#10004; Correct

```php
<?php
while ($expr) {
	// ...
}

do {
	// ...
} while ($expr);
```

&#9650; [Table of Contents](#table-of-contents)


## For, Foreach
* MUST follow the [control structures standards](#control-structures)

### &#10004; Correct

```php
<?php
for ($i = 0; $i < 10; $i++) {
	// ...
}

foreach ($iterable as $key => $value) {
	// ...
}
```

&#9650; [Table of Contents](#table-of-contents)


## Try, Catch
* MUST follow the [control structures standards](#control-structures)
* `catch` MUST be between `}` and `{` on one line

### &#10006; Incorrect

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

### &#10004; Correct

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

&#9650; [Table of Contents](#table-of-contents)


## Class File
*  MUST only contain one definition

### &#10006; Incorrect

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

### &#10004; Correct
```php
<?php
namespace Core\Models;

class User {
	// ...
}
```

&#9650; [Table of Contents](#table-of-contents)


## Class Namespace
* MUST be defined

### &#10006; Incorrect

```php
<?php
class User {
	// ...
}
```

&#8627; Incorrect because there is no namespace defined.

### &#10004; Correct

```php
<?php
namespace Core\Models;

class User {
	// ...
}
```

&#9650; [Table of Contents](#table-of-contents)


## Class Name
* MUST start with a capital letter 
* MUST be camelcased

### &#10006; Incorrect

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

### &#10004; Correct

```php
<?php
namespace Core\Models;

class OfficeProgram {
	// ...
}
```

&#9650; [Table of Contents](#table-of-contents)


## Class Prefix
The following prefix notation SHOULD be used:

* `A` for abstract classes
	* e.g. `AController`, `APrototype`, etc
* `I` for interfaces
	* e.g. `ICountable`, `IBehavior`, etc
* `T` for traits
	* e.g. `TString`, `TNotation`, etc
* `E` for exceptions
	* e.g. `EInbvalidArgument`, `EUndefinedVariable`, etc

### &#10004; Correct

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

&#9650; [Table of Contents](#table-of-contents)


## Class Definition
* The opening curly brace MUST be placed on the same line
	* i.e. `class User` `·` `{` `↵` `...` `↵` `}`

### &#10006; Incorrect

```php
<?php
namespace Core\Models;

class User 
{
	// ...
}
```

&#8627; Incorrect because `{` is not on the same line.

### &#10004; Correct

```php
<?php
namespace Core\Models;

class User {
	// ...
}
```

&#9650; [Table of Contents](#table-of-contents)


## `Extends` Keyword
* MUST be placed on the same line

### &#10006; Incorrect

```php
<?php
namespace Core\Models;

class User 
	extends APrototype {
	// ...
}
```

&#8627; Incorrect because the `extends` keyword is not on the same line.

### &#10004; Correct

```php
<?php
namespace Core\Models;

class User extends APrototype {
	// ...
}
```

&#9650; [Table of Contents](#table-of-contents)



## `Implements` keyword
* SHOULD be moved to the next line

### ~ Acceptable

```php
<?php
namespace Core\Models;

class User extends APrototype implements Countable {
	// ...
}
```

&#8627; Incorrect because the `implements` keyword is not on the new line.

### &#10004; Preferred

```php
<?php
namespace Core\Models;

class User extends APrototype 
	implements Countable {
	// ...
}
```

&#9650; [Table of Contents](#table-of-contents)


## `Use` keyword
* MUST include a single trait per line 

### &#10006; Incorrect

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

### &#10004; Correct

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

&#9650; [Table of Contents](#table-of-contents)


## Class Properties
* MUST follow the [variable standards](#variables)
* MUST specify visibility
* MUST NOT be prefixed with an underscore
* SHOULD be type-hinted if possible

### &#10006; Incorrect

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

### ~ Acceptable

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

### &#10004; Preferred

```php
<?php
namespace Core\Models;

class User {
	public int $var1;
	protected string $var2;
	private bool $var3;
}
```

&#9650; [Table of Contents](#table-of-contents)


## Class Methods
* MUST follow the [function standards](#function-name)
* MUST specify visibility
* MUST NOT be prefixed with an underscore

### &#10006; Incorrect

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

### &#10004; Correct

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

&#9650; [Table of Contents](#table-of-contents)


## Class Instance
* MUST start with a capital letter
* MUST be camelcased
* MUST include parenthesis

### &#10006; Incorrect

```php
<?php
$office_program = new OfficeProgram;
```

&#8627; Incorrect because a lack of parenthesis.

### &#10004; Correct

```php
<?php
$office_program = new OfficeProgram();
```

&#9650; [Table of Contents](#table-of-contents)

