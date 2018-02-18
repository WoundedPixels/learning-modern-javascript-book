# Chapter Constants and Variables at a Glance

So,  use const. It keeps everything simple and makes debugging easier.

```JavaScript
const name = 'fred';
const message = 'Hi ' + name + '!';
console.log('message', message);
```
[https://es6console.com/jdrq67hu/](https://es6console.com/jdrq67hu/)

You just can't change a value once it is assigned.

`name = 'ted'; // Nope!`

Sometimes you need to change values, but not as often as you might think. Make up your mind!

But if you do need to, just use let:

```JavaScript
let height = 100;`
height = 110; // Yup!
```

There are two common ways to store values in JavaScript - const and let. You can't change your mind with const. Current common practice is to favor const and use let only when the alternative makes your code unwieldy.

## Name Things Well

A little effort goes a long way and your future self will thank you! Also, the other fine professionals who read your code appreciate your efforts! 

But what makes a good name for a variable? You will have to develop your own style, but here are some starting points:
* Spell it out - abbreviations may save some keystrokes but they are often confusing
* Name things from the reader's perspective - choose a name that will make sense to the next hire, not you while you are immersed in the code or even the seasoned veteran in the next cube
* Be specific - maxAge is better than max unless the scope of the variable is just a few lines
* You usually don't need to include the type of a variable in the name - maxAgeNumber is a bit silly
* Unless it helps you - like distinguishing between helpText and helpDiv

Decent names also allow you to limit your comments to adding context or explaining assumptions and exceptions. Stick to your guns on this - line by line comments are inefficient and get dangerous as they age. If you want high quality and readable code then keep your files small and name things well! Comments should explain odd things, not illuminate overly terse lines.

### Consistency

Most languages have well defined conventions for naming everything. JavaScript is probably a little less standardized than most languages, but we agree on a few things. Use camelCase for variables and general purpose constants. Use all UPPERCASE for real world constants.

```JavaScript
const PI = 3.14;
const radius = 2;
const areaOfCircle = PI * radius * radius;
```

## Primitive Data Types

JavaScript has six fundamental data types. They are the lowest level most elemental values that you use to build everything else.

If you want to know the type of a variable, use the typeof operator as in typeof\(name\).

## Truth and Decisions

The name of the data type for holding all sorts of verdicts is boolean.

```JavaScript
const tall = (height > 72);
const big = (weight > 200);
const rich = (income > 500000);
const chargeExtra = ( (big && tall) || rich);

if (chargeExtra) {
  doSomethingGreedy();`
}
```

Read that as charge extra if people are both big and tall or rich. In any case tall, big, rich, and chargeExtra are booleans. 

Building complex conditionals from a series of simple conditionals allows the reader to get the big idea first and then fill in the details as needed. Consider the alternative:

```JavaScript
if ((weight > 200 && height > 72) || income > 500000) {
  doSomethingGreedy();
}
```

While this saves a lot of lines it gets confusing for real world logic. Also you will often need the same simple conditional later.

```JavaScript
if (big || tall) {
  provideBigSeat();
}
```

This really looks good compared to:
```JavaScript
if (weight > 20 || height > 72) {
  provideBigSeat();
}
```

Of course you would never fat finger a cut and paste like that... And you would totally see the mistake at a glance...

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

* [Null](https://developer.mozilla.org/en-US/docs/Glossary/Null)
* [Undefined](https://developer.mozilla.org/en-US/docs/Glossary/Undefined)
* [Number](https://developer.mozilla.org/en-US/docs/Glossary/Number)
* [String](https://developer.mozilla.org/en-US/docs/Glossary/String)
* [Symbol](https://developer.mozilla.org/en-US/docs/Glossary/Symbol)
  \(new in ECMAScript 6\)



