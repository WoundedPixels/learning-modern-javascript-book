# Chapter Constants and Variables at a Glance

So,  use const. It keeps everything simple and makes debugging easier.

`const name = 'fred';`

`const message = 'Hi ' + name + '!';`

`console.log('message', message);`

You just can't change a value once it is assigned.

`name = 'ted'; // Nope!`

[https://es6console.com/jdrq67hu/](https://es6console.com/jdrq67hu/)

Sometimes you need let, but not often. Make up your mind!

`let height = 100;`

`height = 110; // Yup!`

There are two common ways to store values in JavaScript - const and let. You can't change your mind with const. Current common practice is to favor const and use let only when the alternative makes your code unwieldy.

## Name Things Well

A little effort goes a long way and your future self will thank you as will the other fine professionals who read your code! Decent names also allow you to comment for context or to explain assumptions and exceptions. Stick to your guns on this - line by line comments are inefficient and potentially dangerous. If you want high quality and readable code then keep it small and name things well!

### Consistency

Most languages have well defined conventions for naming everything. JavaScript is probably a little less standardized than most languages, but we agree on a few things. Use camelCase for variables and general purpose constants. Use all UPPERCASE for real world constants.

`const PI = 3.14;`

`const radius = 2;`

`const areaOfCircle = PI * radius * radius;`

## Primitive Data Types

JavaScript has six fundamental data types. They are the lowest level most elemental values that you use to build everything else.

If you want to know the type of a variable, use the typeof operator as in typeof\(name\).

## Truth and Truthyness

The name of the data type for holding all sorts of verdicts is boolean.

`const height = 60;`

`const tall = (height > 72);`

`const big = (weight > 200);`

`const rich = (income > 500000);`

`const chargeExtra = ( (big && tall) || rich);`

`if (chargeExtra) {`

`  doSomethingGreedy();`

`}`



For no clear reason, we charge more if people are big and tall or rich. Or both. 

Building complex conditionals from a series of simple conditionals keeps allows the reader to get the big idea first and then fill in the details as needed. Consider the alternative:

`if ((weight > 200 && height > 72) || income > 500000) {`

`doSomethingGreedy();`

`}` 

### Strings

JavaScript has really nice strings!

QQQ unicode, interpolation, multiline QQQ

### Known Unknowns

### Unknown Unknowns

### Symbols

Type Coercion

Six data types that are

[primitives](https://developer.mozilla.org/en-US/docs/Glossary/Primitive)

:

* [Boolean](https://developer.mozilla.org/en-US/docs/Glossary/Boolean)
* [Null](https://developer.mozilla.org/en-US/docs/Glossary/Null)
* [Undefined](https://developer.mozilla.org/en-US/docs/Glossary/Undefined)
* [Number](https://developer.mozilla.org/en-US/docs/Glossary/Number)
* [String](https://developer.mozilla.org/en-US/docs/Glossary/String)
* [Symbol](https://developer.mozilla.org/en-US/docs/Glossary/Symbol)
  \(new in ECMAScript 6\)



