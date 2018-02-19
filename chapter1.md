# Chapter - Shaping Data

Developers spend a lot of time working with different kinds of data. Somehow it never starts the way it needs to be and we get to combine, extrapolate and generally twist it into a useful form.

## Holding Data

Of course you need a way to hold data. Modern JavaScript takes a firm different stance on holding data - most data is not allowed to change. This takes two forms, constant assignment to immutable primitives and constant assignment to mutable complex things.

### Immutable Primitives
First, low level or primitive data is immutable, which is a fancy way of saying that it cannot be changed. You can create a new string from a string, perhaps by converting it to uppercase, but the original string lives on. Same for numbers.

### Constant Assignment
You indicate that you will not change the assignment of data to a name through the const keyword. In the following snippet, once the data 'fred' is assigned to the data named firstName it is fixed until the code finishes. 

```JavaScript
const firstName = 'fred';
const message = 'Hi ' + firstName + '!'; 
console.log('message', message);

const shouting = message.toUpperCase();
console.log('message', message);
console.log('shouting', shouting);
```
[https://es6console.com/jdtgv7kw/](https://es6console.com/jdtgv7kw/)

You just can't change a primitive once it is created and you can't reassign a const. So, primitive data that is held in a const is really, really going to stay put.

```JavaScript
message = shouting; // Nope!
```

### Non-Constant Assignment
Sometimes you need to change the value that a name refers to. To indicate that a piece of data can change, use the keyword let:

```JavaScript
let height = 100;`
height = 110; // Yup!
```

> The default way to hold data in JavaScript is const. It is generally worth the effort but it is also worth understanding why this best practice exists. Once you get the fundamentals, google 'javascript immutable const let var' and settle in for a bit. Down with Dogma!

### Mutable Complex Things
There is more to data in JavaScript than strings and numbers and other primitives. Specifically, there are arrays and objects. For now, let's just stay focused on mutability and assignment - a complex thing can be changed after it is created. But you can't change which complex thing a name refers to. So awkward to say, perhaps it is easier to see?

```JavaScript
const fred = {
  name: 'fred',
  height: 50,
};

console.log('fred', fred);
fred.height = 55;
console.log('fred', fred);

const sally = {
  name: 'sally',
  height: 54,
}
```
https://es6console.com/jdthokhd/

Fred can get taller, but thanks to the constant assignment he must continue to be the same object.

fred = sally; // Nope! 

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
In many cases you know what you are missing. By the time you are done processing user input you know which fields were not entered. Information that is deleted may leave a known unknown. Think of it as an explicit indication that we do not know something.

The right data type in this case is null as in:
```JavaScript
const firstName = 'fred';
const middleName = null;
```

### Unknown Unknowns
In other cases there is no explicit decision that a variable is not known. This may mean that a mistake has been made or that the processing just hasn't happened yet.

```JavaScript
const firstName = 'fred';
typeof(frstName) // undefined
```

### Symbols

For more information, including mention of the sixth primitive, Symbol, see:

[https://developer.mozilla.org/en-US/docs/Glossary/Primitive](https://developer.mozilla.org/en-US/docs/Glossary/Primitive)

### Type Coercion





