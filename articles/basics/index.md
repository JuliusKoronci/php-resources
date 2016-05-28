---
title: "PHP basics"
read_time: "5 min"
updated: "february 21, 2015"
group: "articles"
permalink: "/tutorials/php-basics/index.html"
---

1. [PHP in a nutshell](#php-in-a-nutshell)
2. [Basic syntax](#basic-syntax)
    1. [Hello world](#hello-world)
    2. [Operators](#operators)
        * [Arithmetic operators](#arithmetic-operators)
        * [Comparison operators](#comparison-operators)
        * [Logical operators](#logical-operators)
        * [Assignment operators](#assignment-operators)
    3. [Declarations](#declarations)
    4. [Functions](#functions)
        * [Anonymous functions (closures)](#anonymous-functions-closures)
        * [Variadic functions](#variadic-functions)
    5. [Control structures](#control-structures)
        * [If](#if)
        * [Loops](#loops)
        * [Switch](#switch)
    6. [Arrays](#arrays)
        * [Operations on arrays](#operations on arrays)
    7. [Built in types](#built-in-types)
3. [Errors](#errors)
    1. [PHP Errors](#php-errors)
    2. [What is next?](#what-is-next)

This tutorial will show you basic PHP syntax and its features. If you're new to PHP read the most basic [PHP tutorial](http://php.net/manual/en/tutorial.php) to get started as quickly and painlessly as possible. For becoming modern PHP developer read and follow also [PHP: The Right Way](http://phptherightway.com). Seriously.


## PHP in a nutshell

* scripting language
* procedural and object oriented language
* dynamically (weakly) typed
* syntax similar to C, C++, C#, Java and Perl
* Imperative language
* PHP has closures

## Basic syntax

### Hello world

File `hello.php`:

~~~php
<?php

echo 'Hello, world.';
~~~
`$ php hello.php`

### Operators

#### Arithmetic operators

|Operator|Name|Result|
|--------|----|-----------|
|`-$a`|negation|Opposite of $a.|
|`$a + $b`|addition|Sum of $a and $b.|
|`$a - $b`|Subtraction|Difference of $a and $b.|
|`$a * $b`|Multiplication|Product of $a and $b.|
|`$a / $b`|division|Quotient of $a and $b.|
|`$a % $b`|modulus|Remainder of $a divided by $b.|
|`$a ** $b`|Exponentiation|Result of raising $a to the $b'th power.|

#### Comparison operators

|Operator|Name|Result|
|--------|----|-----------|
|`$a == $b`|Equal|TRUE if $a is equal to $b after type juggling.|
|`$a === $b`|Identical|TRUE if $a is equal to $b, and they are of the same type.|
|`$a != $b`|Not equal|TRUE if $a is not equal to $b after type juggling.|
|`$a <> $b`|Not equal|TRUE if $a is not equal to $b after type juggling.|
|`$a !== $b`|Not identical|TRUE if $a is not equal to $b, or they are not of the same type.|
|`$a < $b`|Less than|TRUE if $a is strictly less than $b.|
|`$a > $b`|Greater than|TRUE if $a is strictly greater than $b.|
|`$a <= $b`|Less than or equal to|TRUE if $a is less than or equal to $b.|
|`$a >= $b`|Greater than or equal to|TRUE if $a is greater than or equal to $b.|

#### Logical operators

|Operator|Name|Result|
|--------|----|------|
|`$a and $b`|And|TRUE if both $a and $b are TRUE.|
|`$a or $b`|Or|TRUE if either $a or $b is TRUE.|
|`$a xor $b`|Xor|TRUE if either $a or $b is TRUE, but not both.|
|`! $a`|Not|TRUE if $a is not TRUE.|
|`$a && $b`|And|TRUE if both $a and $b are TRUE.|
|`$a || $b`|Or|TRUE if either $a or $b is TRUE.|

#### Assignment operators

|Operator|Description|
|--------|-----------|
|`=`|Set a value to variable|
|`+=`|Addition of numeric value to variable|
|`.=`|Add string to variable|

### Declarations

* `$i = 1;` - assign value to variable
* `define('FOO', 'something');` - define a constant
*

### Functions

~~~php
// a simple function
function functionName() {}

// function with parameters
function functionName($param1, $param2) {}
~~~

#### Anonymous functions (closures)

~~~php
<?php
echo preg_replace_callback('~-([a-z])~', function ($match) {
    return strtoupper($match[1]);
}, 'hello-world');
// outputs helloWorld

// Anonymous function variable assignment example
$greet = function($name) {
    printf("Hello %s\r\n", $name);
};
$greet('World');

// inherit
$message = 'hello';

// Without "use" keyword
$example = function () {
    var_dump($message);
};
echo $example();

// Inherit $message
$example = function () use ($message) {
    var_dump($message);
};
echo $example();
~~~

#### Variadic functions

~~~php
<?php
function sum(...$nums)
{
    return array_sum($nums);
}
~~~

### Control structures

#### If

~~~php
if $x > 0 {
    return $x;
} else {
    return -$x;
}
~~~

#### Loops

~~~php
// for
for ($i = 1; $i<10; $i++) {}

// while
while ($i < 10) {}

// do while
$i = 0;
do {
    echo $i;
} while ($i > 0);


// foreach
foreach ($array as $key => $value) {}
~~~

#### Switch

~~~php
// switch statement
switch ($operatingSystem) {
    case 'darwin':
        echo 'Mac OS Hipster';
        break;
    case 'linux':
        echo 'Linux Geek';
        break;
    default:
        // Windows, BSD, ...
        echo 'Other';
}
~~~

### Arrays

~~~php
$array = [
    "foo" => "bar",
    "bar" => "foo",
];
~~~

#### Operations on arrays

|Operator|Name|Result|
|--------|----|------|
|`$a + $b`|Union|Union of $a and $b.|
|`$a == $b`|Equality|TRUE if $a and $b have the same key/value pairs.|
|`$a === $b`|Identity|TRUE if $a and $b have the same key/value pairs in the same order and of the same types.|
|`$a != $b`|Inequality|TRUE if $a is not equal to $b.|
|`$a <> $b`|Inequality|TRUE if $a is not equal to $b.|
|`$a !== $b`|Non-identity|TRUE if $a is not identical to $b.|

### Built-in types

|Type|
|----|
|boolean|
|integer|
|float|
|string|
|array|
|object|
|resource|
|NULL|

## Errors

### PHP errors

~~~php
<?php
// Turn off all error reporting
error_reporting(0);

// Report simple running errors
error_reporting(E_ERROR | E_WARNING | E_PARSE);

// Reporting E_NOTICE can be good too (to report uninitialized
// variables or catch variable name misspellings ...)
error_reporting(E_ERROR | E_WARNING | E_PARSE | E_NOTICE);

// Report all errors except E_NOTICE
error_reporting(E_ALL & ~E_NOTICE);

// Report all PHP errors (see changelog)
error_reporting(E_ALL);

// Report all PHP errors
error_reporting(-1);

// Same as error_reporting(E_ALL);
ini_set('error_reporting', E_ALL);

~~~

### Exceptions

~~~php
function inverse($x) {
    if (!$x) {
        throw new Exception('Division by zero.');
    }
    return 1/$x;
}

try {
    echo inverse(5) . "\n";
} catch (Exception $e) {
    echo 'Caught exception: ',  $e->getMessage(), "\n";
} finally {
    echo "This is always executed.\n";
}
~~~

## What is next?

Use [php.net](http://php.net). It has a great and detailed manual for a lot of your PHP adventures.
