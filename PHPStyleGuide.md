# PHP Style Guide

All rules and guidelines in this document apply to PHP files unless otherwise noted. References to PHP/HTML files can be interpreted as files that primarily contain HTML, but use PHP for templating purposes.

> The keywords "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED",  "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC 2119](http://www.ietf.org/rfc/rfc2119.txt).

<!-- ---------------------------------------------------------------------- -->

## Icons Legend
The icons are used to designate the character sequences around this document simply and unambiguously.

1. `·` means `Space`
2. `⇥` means `Tab`
3. `↵` means `Enter`

<!-- ---------------------------------------------------------------------- -->

## Table of Contents

1. [**Files**](#1-files)
	1. [File Format](#file-format)
	2. [Filename](#filename)
2. [**Tags**](#2-php-tags)
	1. [Open Tag](#1-open-tag)
	2. [Close Tag](#2-close-tag)
	3. [Short Open Tag](#3-short-open-tag)
	4. [Short Echo Tag](#4-short-echo-tag)
3. [**Namespaces**](#3-namespaces)
	1. [Namespace Declaration](#1-namespace-declaration)
	2. [Namespace Definition](#2-namespace-definition)
	3. [Multiple Namespaces](#3-multiple-namespaces)
4. [**Comments**](#4-comments)
	1. [Single-line Comments](#1-single-line-comments)
	2. [Multi-line Comments](#2-multi-line-comments)
	3. [PHPDoc Comments](#3-phpdoc-comments)
5. [**Formatting**](#5-formatting)
	1. [Line Length](#1-line-length)
	2. [Line Indentation](#2-line-indentation)
	3. [Keywords](#3-keywords)
	4. [Variables](#4-variables)
	5. [Constants](#5-constants)
	6. [Statements](#6-statements)
	7. [Operators](#7-operators)
	8. [Unary Operators](#8-unary-operators)
	9. [Concatenation Period](#9-concatenation-period)
6. [**Functions**](#6-functions)
	1. [Function Name](#1-function-name)
	3. [Function Call](#2-function-call)
	3. [Function Arguments](#3-function-arguments)
	4. [Function Declaration](#4-function-declaration)
	5. [Function Return](#5-function-return)
7. [**Control Structures**](#7-control-structures)
	1. [If, Elseif, Else](#1-if-elseif-else)
	2. [Switch, Case](#2-switch-case)
	3. [While, Do While](#3-while-do-while)
	4. [For, Foreach](#4-for-foreach)
	5. [Try, Catch](#5-try-catch)
8. [**Classes**](#8-classes)
	1. [Class File](#1-class-file)
	2. [Class Namespace](#2-class-namespace)
	3. [Class Name](#3-class-name)
	4. [Class Definition](#4-class-definition)
	5. [Extends Keyword](#5-extends-keyword)  
	5. [Implements Keyword](#6-implements-keyword)  
	6. [Class Properties](#7-class-properties)
	7. [Class Methods](#8-class-methods)
	8. [Class Instance](#9-class-instance)

<!-- ---------------------------------------------------------------------- -->

## 1. Files

This section describes the format and naming convention of PHP files.

#### File Format

1. **Characters encoding** MUST be set to UTF-8 without BOM
2. **Line endings** MUST be set to Unix (LF)

#### Filename

1. **Names** MUST follow the [PSR-4](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md) convention 
	* e.g. `Controller.php` but not `controller.php`
2. **Words** MUST NOT be separated with a hyphen or underscore
	* e.g. `AppConfig.php` but not `app-config.php` or `app_config.php` 

&#9650; [Table of Contents](#table-of-contents)

<!-- ---------------------------------------------------------------------- -->

## 2. PHP Tags

This section describes the use of PHP tags in PHP and PHP/HTML files.

1. [**Open tag**](#1-open-tag) MUST be on its own line and MUST NOT be followed by a blank line
	* i.e. `<?php` `↵` `...` but not `<?php` `↵` `↵` `...`
2. [**Close tag**](#2-close-tag) MUST NOT be used in PHP files
	* i.e. `?>` is prohibited in PHP files
3. [**Short open tag**](#3-short-open-tag) MUST NOT be used
	* i.e. `<?php` MUST be always used over `<?` 
4. [**Short echo tag**](#4-short-echo-tag) MAY be used inside PHP/HTML files
	* i.e. `<?=` SHOULD be used over `<?php echo` inside PHP/HTML files when possible

&#9650; [Table of Contents](#table-of-contents)

<!-- ------------------------------ -->

### 1. Open Tag

Open tag MUST be on its own line and MUST NOT be followed by a blank line.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php print_welcome_message();
</pre>

&#8627; Incorrect because `<?php` is not on its own line.

<pre lang=php>
&lt;?php

print_welcome_message();
</pre>

&#8627; Incorrect because `<?php` is followed by a blank line.

#### &#10004; Correct

<pre lang=php>
&lt;?php
print_welcome_message();

</pre>

&#9650; [PHP Tags](#2-php-tags)

<!-- ------------------------------ -->

### 2. Close Tag

Close tag MUST NOT be used in PHP files.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
print_welcome_message();

?&gt;
</pre>

&#8627; Incorrect because `?>` was used.

#### &#10004; Correct

<pre lang=php>
&lt;?php
print_welcome_message();
</pre>

&#9650; [PHP Tags](#2-php-tags)

<!-- ------------------------------ -->

### 3. Short Open Tag

Short open tag MUST NOT be used.

#### &#10006; Incorrect

<pre lang=php>
&lt;?
print_welcome_message();
</pre>

&#8627; Incorrect because `<?` was used instead of `<?php`.

#### &#10004; Correct

<pre lang=php>
&lt;?php
print_welcome_message();
</pre>

&#9650; [PHP Tags](#2-php-tags)

<!-- ------------------------------ -->

### 4. Short Echo Tag

Short echo tag MAY be used inside PHP/HTML files and SHOULD be used over `<?php echo` inside PHP/HTML files when possible.

#### ~ Acceptable

<pre lang=html>
&lt;div&gt;
	&lt;p&gt;&lt;?php echo get_welcome_message(); ?&gt;&lt;/p&gt;
&lt;/div&gt;
</pre>

&#8627; Acceptable, but `<?=` should be used over `<?php echo` when possible.

#### &#10004; Preferred

<pre lang=html>
&lt;div&gt;
	&lt;p&gt;&lt;?=get_welcome_message();?&gt;&lt;/p&gt;
&lt;/div&gt;
</pre>

&#9650; [PHP Tags](#2-php-tags)

<!-- ---------------------------------------------------------------------- -->

## 3. Namespaces

This section describes how to use one or more namespaces and their naming convention.

1. [**Namespace declaration**](#1-namespace-declaration) MUST be the first statement and MUST be followed by a blank line
	* e.g. `<?php` `↵` `namespace MyCompany;` `↵` `↵` `...`
2. [**Namespace definition**](#2-namespace-definition) MUST start with a capital letter and MUST be camelcased
	* e.g. `namespace MyCompany;`
3. [**Multiple namespaces**](#3-multiple-namespaces) MUST use the curly brace syntax
	* e.g. `namespace MyCompany { ... }`

&#9650; [Table of Contents](#table-of-contents)

<!-- ------------------------------ -->

### 1. Namespace Declaration

Namespace declaration MUST be the first statement and MUST be followed by a blank line.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
print_welcome_message();

namespace MyCompany;

</pre>

&#8627; Incorrect because `namespace MyCompany;` is not the first statement.

<pre lang=php>
&lt;?php
namespace MyCompany;
print_welcome_message();

</pre>

&#8627; Incorrect because `namespace MyCompany;` is not followed by a blank line.

#### &#10004; Correct

<pre lang=php>
&lt;?php
namespace MyCompany;

print_welcome_message();
</pre>

&#9650; [Namespaces](#3-namespaces)

<!-- ------------------------------ -->

### 2. Namespace Definition

Namespace name MUST start with a capital letter and MUST be camelcased.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
namespace myCompany;
 
</pre>

&#8627; Incorrect because `myCompany` does not start with a capital letter.

<pre lang=php>
&lt;?php
namespace MyCOMPANY;

</pre>

&#8627; Incorrect because `MyCOMPANY` is not camelcased.

#### &#10004; Correct

<pre lang=php>
&lt;?php
namespace MyCompany;

</pre>

&#9650; [Namespaces](#3-namespaces)

<!-- ------------------------------ -->

### 3. Multiple Namespaces

Multiple namespaces MUST use the curly brace syntax.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
namespace MyCompany\Model;

namespace MyCompany\View;

</pre>

&#8627; Incorrect because there are two namespaces, but the curly brace syntax was not used.

#### &#10004; Correct

<pre lang=php>
&lt;?php
namespace MyCompany\Model {
	// model body
}

namespace MyCompany\View {
	// view body
}

</pre>

&#9650; [Namespaces](#3-namespaces)

<!-- ------------------------------ -->

## 4. Comments

This section describes how comments should be formatted and used.

1. **[Single-line comments](#1-single-line-comments)** MUST use two forward slashes
	* e.g. `// My comment`
2. **[Multi-line comments](#2-multi-line-comments)** MUST use the block format
	* i.e. `/*` `↵` ` My comment` `↵` `*/`
3. **[PHPDoc comments](#3-phpdoc-comments)** MUST use the block format and follow the [PHPDoc](https://docs.phpdoc.org/3.0/guide/getting-started/what-is-a-docblock.html) syntax requirements.
	* i.e. `/**` `↵` `* My comment` `↵` `*/`

&#9650; [Table of Contents](#table-of-contents)

<!-- ------------------------------ -->

### 1. Single-line Comments

Single-line comments MUST use two forward slashes.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
/* This is a comment */

</pre>

&#8627; Incorrect because it uses `/*` and `*/` for a single-line comment.

#### &#10004; Correct

<pre lang=php>
&lt;?php
// This is a comment

</pre>

&#9650; [Comments](#4-comments)

<!-- ------------------------------ -->

### 2. Multi-line Comments

Multi-line comments MUST use the block format.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
// This is a
// multi-line
// comment
 
</pre>

&#8627; Incorrect because it uses `//` for a multi-line comment.

#### &#10004; Correct

<pre lang=php>
&lt;?php
/*
 This is a
 multi-line
 comment
*/

</pre>

&#9650; [Comments](#4-comments)

<!-- ------------------------------ -->


### 3. PHPDoc Comments

Multi-line comments MUST use the block format and follow the [PHPDoc](https://docs.phpdoc.org/3.0/guide/getting-started/what-is-a-docblock.html) syntax requirements.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
/*
 This is a
 multi-line
 comment
*/
 
</pre>

&#8627; Incorrect because it uses `/*` for a PHPDoc comment.

#### &#10004; Correct

<pre lang=php>
&lt;?php
/**
 * This is a
 * PHPDoc comment 
 */

</pre>

&#9650; [Comments](#4-comments)

<!-- ------------------------------ -->

## 5. Formatting

This section outline various, general formatting rules related to whitespace and text.

1. [**Line length**](#1-line-length) MUST NOT be hard limited
2. [**Line indentation**](#2-line-indentation) MUST be accomplished using tabs
	* i.e. `function func() {` `↵` `⇥` `...` `↵` `}`
3. [**Keywords**](#3-keywords) MUST be all lowercase
	* e.g. `false`, `true`, `null`, etc.
4. [**Variables**](#4-variables) MUST be all camelcased and MUST NOT be separated by an underscore.
	* e.g. `$shortWelcomeMessage` instead of `$short_welcome_message`
9. [**Constants**](#5-constants) MUST be all uppercase and words MUST be separated by an underscore
	* e.g. `WELCOME_MESSAGE`
10. [**Statements**](#6-statements) MUST be placed on their own line and MUST end with a semicolon
	* e.g. `welcome_message();`
11. [**Operators**](#7-operators) MUST be surrounded by a space
	* e.g. `$total = 15 + 7;`, `$var .= '';`
12. [**Unary operators**](#8-unary-operators) MUST be attached to their variable or integer
	* e.g. `$index++`, `--$index`
13. [**Concatenation period**](#9-concatenation-period) MUST be surrounded by a space
	* e.g. `echo 'Read:' . $welcome_message;`

&#9650; [Table of Contents](#table-of-contents)

<!-- ------------------------------ -->

### 1. Line Length

The soft limit on line length MUST be 120 characters; automated style checkers MAY warn but MUST NOT error at the soft limit.

&#9650; [Formatting](#5-formatting)

### 2. Line Indentation

The line indentation MUST be accomplished by using `TAB` characters only.

&#9650; [Formatting](#5-formatting)

<!-- ------------------------------ -->

### 3. Keywords

Keywords MUST be all lowercase.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
$is_true = FALSE;
$is_false = TRUE:
$movie_quote = NULL;

</pre>

&#8627; Incorrect because `FALSE`, `TRUE` and `NULL` are not all lowercase.

#### &#10004; Correct

<pre lang=php>
&lt;?php
$is_true = false;
$is_false = true:
$movie_quote = null;
 
</pre>

&#9650; [Formatting](#5-formatting)

<!-- ------------------------------ -->

### 4. Variables

Variables MUST be all camelcased and MUST NOT be separated by an underscore. 
The first letter case MUST slightly determine the variable type:

1. Variables of object type MUST starts from an uppercase letter
2. Variables of primitive types MUST starts from a lowercase letter
3. Arrays MAY be tract as primitives or as objects in accordance to the situation


#### &#10006; Incorrect

<pre lang=php>
&lt;?php
$welcome_message = '';
$WelcomeMESSAGE = '';
</pre>

&#8627; Incorrect because variables are not camelcased properly.

<pre lang=php>
&lt;?php
$WelcomeMessage = '';
</pre>

&#8627; Incorrect because the variable contains a primitive type but starts from an uppercase letter.

<pre lang=php>
&lt;?php
$someObject = new SomeClass();
</pre>

&#8627; Incorrect because the variable contains an object but doesn't start from an uppercase letter.

#### &#10004; Correct

<pre lang=php>
&lt;?php
$welcomeMessage = '';
$SomeObject = new SomeClass();
</pre>

&#9650; [Formatting](#5-formatting)

<!-- ------------------------------ -->

### 5. Constants

Constants MUST be all uppercase and words MUST be separated by an underscore.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
define('welcome_Message', '');
define('Welcome_Message', '');
define('welcome_message', '');

</pre>

&#8627; Incorrect because the constants are not all uppercase.

<pre lang=php>
&lt;?php
define('WELCOMEMESSAGE', '');
 
</pre>

&#8627; Incorrect because `WELCOME` and `MESSAGE` are not separated with an underscore.

#### &#10004; Correct

<pre lang=php>
&lt;?php
define('WELCOME_MESSAGE', '');

</pre>

&#9650; [Formatting](#5-formatting)

<!-- ------------------------------ -->

### 6. Statements

Statements MUST be placed on their own line and MUST end with a semicolon.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
$quotes_exist = false; print_welcome_message();

</pre>

&#8627; Incorrect because the statements are on the same line.

#### &#10004; Correct

<pre lang=php>
&lt;?php
$quotes_exist = false;
print_welcome_message();

</pre>

&#9650; [Formatting](#5-formatting)

<!-- ------------------------------ -->

### 7. Operators

Operators MUST be surrounded a space.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
$total=3+14;
$string='Hello, World! ';
$string.='Today is a good day!';

</pre>

&#8627; Incorrect because there is no space surrounding the `=`, `+` or `.=` sign.

#### &#10004; Correct

<pre lang=php>
&lt;?php

$total = 3 + 14;
$string = 'Hello, World! ';
$string .= 'Today is a good day!';

</pre>

&#9650; [Formatting](#5-formatting)

<!-- ------------------------------ -->

### 8. Unary Operators

Unary operators MUST be attached to their operand.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
$index ++;
-- $index;
</pre>

&#8627; Incorrect because there is a space before `++` and after `--`.

#### &#10004; Correct

<pre lang=php>
&lt;?php
$index++;
--$index;
</pre>

&#9650; [Formatting](#5-formatting)

<!-- ------------------------------ -->

### 9. Concatenation Period

Concatenation period MUST be surrounded by a space.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
echo 'Hello, World! Today is '.$date.'!';
</pre>

&#8627; Incorrect because there is no space surrounding `.`.

#### &#10004; Correct

<pre lang=php>
&lt;?php
echo 'Hello, World! Today is ' . $date . '!';
</pre>

&#9650; [Formatting](#5-formatting)

<!-- ------------------------------ -->

## 6. Functions

This section describes the format for function names, calls, arguments and declarations.

1. [**Function name**](#1-function-name) MUST start from a lowercase letter, MUST be all camelcased, and MUST NOT be separated by an underscore.
	* e.g. `function welcomeMessage() {`
2. [**Function call**](#2-function-call) MUST NOT have a space between function name and open parenthesis
	* e.g. `func();`
3. [**Function arguments**](#3-function-arguments)
	* MUST NOT have a space before the comma
	* MUST have a space after the comma 
	* SHOULD be type-hinted if possible
	* MAY use line breaks for long arguments
	* e.g. `func($arg1, $arg2 = 'asc', $arg3 = 100);`
4. [**Function declaration**](#4-function-declaration) MUST be documented using [phpDocumentor](http://phpdoc.org/docs/latest/index.html) tag style and SHOULD include
	* Short description
	* Optional long description, if needed
	* @access: `private` or `protected` (assumed `public`)
	* @author: Author name
	* @global: Global variables function uses, if applicable
	* @param: Parameters with data type, variable name, and description
	* @return: Return data type, if applicable
5. [**Function return**](#5-function-return)
	* MUST occur as early as possible 
	* MUST be initialized prior at top
	* MUST be preceded by blank line, except inside control statement
	* i.e. `if (!$expr) { return false; }`

&#9650; [Table of Contents](#table-of-contents)

<!-- ------------------------------ -->

### 1. Function Name

Function name MUST be all lowercase and words MUST be separated by an underscore.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
get_WelcomeMessage();
GetWelcomeMessage();
GET_WELCOME_MESSAGE();
getwelcomemessage();
</pre>

&#8627; Incorrect because the function names are not all properly camelcased.

#### &#10004; Correct

<pre lang=php>
&lt;?php
getWelcomeMessage();
</pre>

&#9650; [Functions](#6-functions)

<!-- ------------------------------ -->

### 2. Function Call

Function call MUST NOT have a space between function name and open parenthesis.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
printWelcomeMessage ();
</pre>

&#8627; Incorrect because there is a space between `getWelcomeMessage` and `()`.

#### &#10004; Correct

<pre lang=php>
&lt;?php
printWelcomeMessage();
</pre>

&#9650; [Functions](#6-functions)

<!-- ------------------------------ -->

### 3. Function Arguments

Function arguments:

* MUST NOT have a space before the comma
* MUST have a space after the comma
* SHOULD be type-hinted if possible
* MAY use line breaks for long arguments

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
someFunction($arg1 , $arg2 , $arg3) {
	// ...
}
</pre>

&#8627; Incorrect because there is a space before `,`.

<pre lang=php>
&lt;?php
someFunction($arg1,$arg2,$arg3) {
	// ...
}
</pre>

&#8627; Incorrect because there is no space after `,`.

#### ~ Acceptable

<pre lang=php>
&lt;?php
function addUsersToOffice($users, $Office) {
	// ...
}
</pre>

&#8627; Acceptable, but `$users` and `$office` are missing their data types.

#### &#10004; Preferred

<pre lang=php>
&lt;?php
function getObjects(string $type, string $order = 'asc', int $limit = 100): SomeObjectType {
	// ...
}

function addUsersToOffice(array $users, Office $Office): bool {
	// ...
}
</pre>

&#9650; [Functions](#6-functions)

<!-- ------------------------------ -->

### 4. Function Declaration

Function declaration MUST be documented via [phpDOC](http://phpdoc.org/docs/latest/index.html) and SHOULD include but not be limited by:

* short description if needed
* `@param` - argument data type and name
* `@return` - return data type, if applicable
* `@throws` - throwable exceptions if any

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
function someFunction(int $id, int $width, int $height): Photo {
	// ...
}
</pre>

&#8627; Incorrect because the function is not documented.

#### &#10004; Correct

<pre lang=php>
&lt;?php
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
</pre>

&#9650; [Functions](#6-functions)

<!-- ------------------------------ -->

### 5. Function Return

Function return:

* SHOULD be type-hinted if applicable

#### ~ Acceptable

<pre lang=php>
&lt;?php
function getValue() {
	// ...
}
</pre>

&#8627; Acceptable, but the return type is not hinted.

#### &#10004; Preferred

<pre lang=php>
&lt;?php
function getValue(): string {
	// ...
}
</pre>

&#9650; [Functions](#6-functions)

<!-- ---------------------------------------------------------------------- -->

## 7. Control Structures
This section defines the layout and usage of control structures. Note that this section is separated into rules that are applicable to all structures, followed by specific rules for individual structures.

* **Keyword** MUST be followed by a space
	* e.g. `if (`, `switch (`, `do {`, `for (`
* **Opening parenthesis** MUST NOT be followed by a space
	* e.g. `($expr`, `($i`
* **Closing parenthesis** MUST NOT be preceded by a space
	* e.g. `$expr)`, `$i++)`, `$value)`
* **Opening brace** MUST be preceded by a space and MUST be followed by a new line
	* e.g. `$expr) {`, `$i++) {`
* **Structure body** MUST be indented once and MUST be enclosed with curly braces (no shorthand)
	* e.g. `if ($expr) {` `↵` `⇥` `...` `↵` `}`
* **Closing brace** MUST start on the next line
	* i.e. `...` `↵` `}`

In addition to the rules above, some control structures have additional requirements:

1. [**If, Elseif, Else**](#1-if-elseif-else)
	* `elseif` MUST be used instead of `else if`
	* `elseif` and `else` MUST be between `}` and `{` on one line
2. [**Switch, Case**](#2-switch-case)
	* Case statement MUST be indented once
		* i.e. `⇥` `case 1:`
	* Case body MUST be indented twice
		* i.e. `⇥` `⇥` `func();`
	* Break keyword MUST be indented twice
		* i.e. `⇥` `⇥` `break;`
3. [**While, Do While**](#3-while-do-while)
4. [**For, Foreach**](#4-for-foreach)
5. [**Try, Catch**](#5-try-catch)
	* `catch` MUST be between `}` and `{` on one line

&#9650; [Table of Contents](#table-of-contents)

<!-- ------------------------------ -->

### 1. If, Elseif, Else
* `elseif` MUST be used instead of `else if`
* `elseif` and `else` MUST be between `}` and `{` on one line

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
if ($expr1) {
	// if body
} else if ($expr2) {
	// elseif body
} else {
	// else body
}
</pre>

&#8627; Incorrect because `else if` was used instead of `elseif`.

<pre lang=php>
&lt;?php
if ($expr1) {
	// if body
}
elseif ($expr2) {
	// elseif body
}
else {
	// else body
}
</pre>

&#8627; Incorrect because `elseif` and `else` are not between `}` and `{` on one line.

<pre lang=php>
&lt;?php
if($expr)
	$result = 100;
</pre>

&#8627; Incorrect because structure body is not wrapped in curly braces.

#### &#10004; Correct

<pre lang=php>
&lt;?php
if ($expr1) {
	// if body
} elseif ($expr2) {
	// elseif body
} else {
	// else body
}
</pre>

&#9650; [Control Structures](#7-control-structures)

<!-- ------------------------------ -->

### 2. Switch, Case
* Case statement MUST be indented once
* Case body MUST be indented twice
* Break keyword MUST be indented twice
* Case logic MUST be separated by one blank line

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
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
</pre>

&#8627; Incorrect because `case 0` thru `default` are not indented once.

<pre lang=php>
&lt;?php
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
</pre>

&#8627; Incorrect because `echo`, `break` and `return` are not indented twice.

#### &#10004; Correct

<pre lang=php>
&lt;?php
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
</pre>

&#9650; [Control Structures](#7-control-structures)

<!-- ------------------------------ -->

### 3. While, Do While

#### &#10004; Correct

<pre lang=php>
&lt;?php
while ($expr) {
	// ...
}

do {
	// ...
} while ($expr);
</pre>

&#9650; [Control Structures](#7-control-structures)

<!-- ------------------------------ -->

### 4. For, Foreach

#### &#10004; Correct

<pre lang=php>
&lt;?php
for ($i = 0; $i &lt; 10; $i++) {
	// ...
}

foreach ($iterable as $key => $value) {
	// ...
}
</pre>

&#9650; [Control Structures](#7-control-structures)

<!-- ------------------------------ -->

### 5. Try, Catch

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
try {
	// ...
}
catch (FirstExceptionType $Exception) {
	// ...
}
catch (OtherExceptionType $Exception) {
	// ...
}
</pre>

&#8627; Incorrect because `catch` is not between `}` and `{` on one line.

#### &#10004; Correct

<pre lang=php>
&lt;?php
try {
	// ...
} catch (FirstExceptionType $Exception) {
	// ...
} catch (OtherExceptionType $Exception) {
	// ...
}
</pre>

&#9650; [Control Structures](#7-control-structures)

<!-- ---------------------------------------------------------------------- -->

## 8. Classes

This section describes class files, names, definitions, properties, methods and instantiation.

1. [**Class file**](#1-class-file) MUST only contain one definition
2. [**Class namespace**](#2-class-namespace) MUST be defined
3. [**Class name**](#3-class-name) MUST start with a capital letter and MUST be camelcased
	* e.g. `MyCompany`
4. [**Class definition**](#4-class-definition) MUST place curly braces on the same line after a space
	* i.e. `class User` `·` `{` `↵` `...` `↵` `}`
5. [**Extends keyword**](#5-extends-keyword)
	* MUST be placed on the same line.
6. [**Implements keyword**](#6-implements-keyword)
	* SHOULD be moved to the next line.
7. [**Class properties**](#7-class-properties)
	* MUST follow [variable standards](#4-variables)
	* MUST specify visibility
	* MUST NOT be prefixed with an underscore
	* SHOULD be type-hinted if possible
	* e.g. `protected int $var3;`
8. [**Class methods**](#8-class-methods)
	* MUST follow [function standards](#6-functions)
	* MUST specify visibility
	* MUST NOT be prefixed with an underscore if private or protected
	* e.g. `protected func3()`
9. [**Class instance**](#9-class-instance)
	* MUST start with capital letter
	* MUST be camelcase
	* MUST include parenthesis
	* e.g. `$user = new User();`, `$OfficeProgram = new OfficeProgram();`

&#9650; [Table of Contents](#table-of-contents)

<!-- ------------------------------ -->

### 1. Class File

Class file MUST only contain one definition.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
namespace Core\Model;

class User {
	// ...
}

class Office {
	// ...
}
</pre>

&#8627; Incorrect because `User` and `Office` are defined in one file.

#### &#10004; Correct
<pre lang=php>
&lt;?php
namespace Core\Model;

class User {
	// ...
}
</pre>

&#9650; [Classes](#8-classes)

<!-- ------------------------------ -->

### 2. Class Namespace

Class namespace MUST be defined.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
class User {
	// ...
}
</pre>

&#8627; Incorrect because there is no namespace defined.

#### &#10004; Correct

<pre lang=php>
&lt;?php
namespace Core\Models;

class User {
	// ...
}
</pre>

&#9650; [Classes](#8-classes)

<!-- ------------------------------ -->

### 3. Class Name

Class name MUST start with a capital letter and MUST be camelcased.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
namespace Core\Model;
class officeProgram {
	// ...
}
</pre>

&#8627; Incorrect because `officeProgram` does not start with a capital letter.

<pre lang=php>
&lt;?php
namespace Core\Model;

class Officeprogram {
	// ...
}
</pre>

&#8627; Incorrect because `Officeprogram` is not camelcased.

#### &#10004; Correct

<pre lang=php>
&lt;?php
namespace Core\Model;

class OfficeProgram {
	// ...
}
</pre>

&#9650; [Classes](#8-classes)

<!-- ------------------------------ -->

### 4. Class Definition

The opening curly brace MUST be placed on the same line.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
namespace Core\Model;

class User 
{
	// ...
}
</pre>

&#8627; Incorrect because `{` is not on the same line.

#### &#10004; Correct

<pre lang=php>
&lt;?php
namespace Core\Model;

class User {
	// ...
}
</pre>

&#9650; [Classes](#8-classes)

<!-- ------------------------------ -->

### 5. Extends Keyword

The `extends` keyword MUST be placed on the same line.

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
namespace Core\Model;

class User 
	extends APrototype {
	// ...
}
</pre>

&#8627; Incorrect because the `extends` keyword is not on the same line.

#### &#10004; Correct

<pre lang=php>
&lt;?php
namespace Core\Model;

class User extends APrototype {
	// ...
}
</pre>

&#9650; [Classes](#8-classes)

<!-- ------------------------------ -->


### 6. Implements keyword

The `implements` keyword SHOULD be moved to the next line.

#### ~ Acceptable

<pre lang=php>
&lt;?php
namespace Core\Model;

class User extends APrototype implements Countable {
	// ...
}
</pre>

&#8627; Incorrect because the `implements` keyword is not on the new line.

#### &#10004; Preferred

<pre lang=php>
&lt;?php
namespace Core\Model;

class User extends APrototype 
	implements Countable {
	// ...
}
</pre>

&#9650; [Classes](#8-classes)

<!-- ------------------------------ -->

### 7. Class Properties

Class properties:

* MUST follow [variable standards](#4-variables)
* MUST specify visibility
* MUST NOT be prefixed with an underscore
* SHOULD be type-hinted if possible

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
namespace Core\Model;

class User {
	// Public
	$var1;

	// Protected
	$var2;

	// Private
	$var3;
}
</pre>

&#8627; Incorrect because visibility is not specified.

<pre lang=php>
&lt;?php
namespace Core\Model;

class User {
	public $var1;
	protected $_var2;
	private $_var3;
}
</pre>

&#8627; Incorrect because some properties are prefixed by the underscore.

#### ~ Acceptable

<pre lang=php>
&lt;?php
namespace Core\Model;

class User {
	public $var1;
	protected $var2;
	private $var3;
}
</pre>

&#8627; Acceptable, but the properties are not type-hinted.

#### &#10004; Preferred

<pre lang=php>
&lt;?php
namespace Core\Model;

class User {
	public int $var1;
	protected string $var2;
	private bool $var3;
}
</pre>

&#9650; [Classes](#8-classes)

<!-- ------------------------------ -->

### 8. Class Methods

Class methods:

* MUST follow [function standards](#6-functions)
* MUST specify visibility
* MUST NOT be prefixed with an underscore

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
namespace Core\Model;

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
</pre>

&#8627; Incorrect because visibility is not specified.

<pre lang=php>
&lt;?php
namespace Core\Model;

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
</pre>

&#8627; Incorrect because some methods are prefixed by the underscore.

#### &#10004; Correct

<pre lang=php>
&lt;?php
namespace Core\Model;

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
</pre>

&#9650; [Classes](#8-classes)

<!-- ------------------------------ -->

### 9. Class Instance

Class instance:

* MUST follow [variable standards](#4-variables)
* MUST include parenthesis

#### &#10006; Incorrect

<pre lang=php>
&lt;?php
$office_program = new OfficeProgram;
</pre>

&#8627; Incorrect because a lack of parenthesis.

#### &#10004; Correct

<pre lang=php>
&lt;?php
$office_program = new OfficeProgram();
</pre>

&#9650; [Classes](#8-classes)

<!-- ---------------------------------------------------------------------- -->
