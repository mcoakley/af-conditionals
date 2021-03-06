# af-conditionals Library

## Status of Project

[![Build Status](https://github.com/acmeframework/af-conditionals/actions/workflows/build-test.yml/badge.svg)](https://github.com/acmeframework/af-conditionals/actions/workflows/build-test.yml) [![Coverage Status](https://coveralls.io/repos/github/acmeframework/af-conditionals/badge.svg?branch=main)](https://coveralls.io/github/acmeframework/af-conditionals?branch=main)

## Purpose

The `af-conditionals` library was created to provide a consistent interface from which to create dynamic comparisons, conditional expressions, logical expressions, and operations. Through the interface, expressions can be defined externally to the application code and dynamically executed.

## Standard Calling Conventions

All Comparisons, Conditionals, Logicals, and Operators expose the object class and a variable named after the class with the word _Instance_ appended, but starting with a lowercase letter. For example: `IsString` is exposed as is `isStringInstance`. The `isStringInstance` variable is declared with a `let` so you may subclass the object and then use your version of your class throughout your application easily. Additionally, we expose a function that implements the testing for the class, for example, `IsString` has a exposed function `isString` that calls `isStringInstance.test()`. _(This is described in the Release Notes for v0.2.0.)_

## Comparisons

The `Comparison` class provides a `compare` and `test` public methods.

The `compare` method takes two values and compares them returning:

- -1 (negative numeral one) when the first value is less than the second value
- 0 (zero) when the first value is equal to the second value
- +1 (positive numeral one) when the first value is greater than the second value

_When possible the `compare` method will compare the values using strict equals (`===`). When the values are not of the same type, `compare` will use coerced equality (`==`)._

The `test` uses the `compare` method to get the result and then compare that result to an expected result that you supply. `test` returns:

- `true` if the returned result and expected result are equal
- `false` otherwise

Supplied Comparisons are:

- `Equal` - determines if two values are equal
- `GreaterThan` - determines if the first value is greater than the second value
- `GreaterThanOrEqual` - determines if the first value is greater than or equal to the second value
- `LessThan` - determines if the first value is less than the second value
- `LessThanOrEqual` - determines if the first value is less than or equal to the second value

_Comparisons use shorthand calling function names instead of exposed functions of `equal`, `greaterThan`, etc... `eq`, `gt`, `gte`, `lt`, `lte` are exposed._

### `strict`

Both the `compare` and `test` methods take an optional parameter `strict` that defaults to `true`. When the comparison is between two string values the `strict` parameter is used to indicate if the comparison should be case-insensitive or not. When `strict` is `true` the comparison is made taking case into account (i.e. capital letters are greater than lowercase letters).

## Conditionals

This library defines a `Conditional` class that is then subclassed to create standard conditional checks.

Supplied Conditionals are:

- `IsArray` - determines if a value is an Array (and Array only)
- `IsEmpty` - determines if a value is empty
  - A string is empty if it is equal to ""
  - A number is empty if it is NaN
  - A boolean is empty if it is false
- `IsFalsey` - loosely tests if a value is false (coerced using !)
- `IsFunction` - determines if a value is a Function
- `IsNumber` - determines if a value is a number
- `IsObject` - determines if a value is an object. This excludes Array's and Function's
- `IsString` - determines if a value is a string
- `IsTruthy` - loosely tests if a value is true (coerced using !!)
- `IsUndefinedOrNull` - determines if a value is undefined or null
- `IsUsable` - inverts IsUndefinedOrNull to determine if a value is "usable"

The majority of the conditionals use `typeof` to determine if a value is of a particular type or not and use non-coerced equality to test the type.

## Logicals

Supplied Logicals are:

- `And` - performs a boolean AND on the supplied operands (can be more than a single test)
- `Or` - performs a boolean OR on the supplied operands (can be more than a single test)

## Operators

Supplied Operators are:

- `Not` - performs a boolean NOT on the supplied value (which will be cast into truthy or falsey)

## Support

To share your comments, provide suggestions, or raise issues, create an [issue](https://github.com/acmeframework/af-conditionals/issues).
