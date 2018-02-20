# Chapter - Shaping Data

Developers spend a lot of time working with different kinds of data. Somehow it never starts the way it needs to be and we get to combine, extrapolate and generally twist it into a useful form.

Much of a developers life is spend building more and more complicated data from primitive chunks. The next few sections cover how data can be assigned and combined.

## Holding Data (Short Version)
Data is assigned using the const keyword:
```JavaScript
const firstName = 'fred';
const message = 'Hi ' + firstName + '!'; 
```

In this case, two strings are created and message holds 'Hi fred!'.

There is a longer section on this topic at the end of the chapter.

## Name Things Well
As you shape data you may need to keep track of a lot of pieces. A little effort on naming goes a long way and your future self will thank you! Also, the other fine professionals who read your code appreciate your efforts! 

But what makes a good name? You will have to develop your own style, but here are some starting points:
* Spell it out - abbreviations may save some keystrokes but they are often confusing
* Name things from the reader's perspective - choose a name that will make sense to the next hire, not you while you are immersed in the code or even the seasoned veteran in the next cube
* Be specific - maxAge is better than max unless the context is just a few lines long
* Avoid single character names - making the next person search for 'i' and 'j' is only funny if they aren't you
* You usually don't need to include the type of a variable in the name - maxAgeNumber is a bit silly
* Unless it really helps you - like distinguishing between helpText and helpDiv  

Decent names also allow you to limit your comments to adding context or explaining assumptions and exceptions. Stick to your guns on this - line by line comments are inefficient and get dangerous as they age. If you want high quality and readable code then keep your functions and files small and name things well! Comments should explain odd things, not illuminate overly terse lines.

### Consistency

Most languages have well defined conventions for naming everything. JavaScript is probably a little less standardized than most languages, but we agree on a few things. Use camelCase for most data assignments. Use all UPPERCASE for real world constants.

```JavaScript
const PI = 3.14;
const radius = 2;
const areaOfCircle = PI * radius * radius;
```
## Primitive Data Types

JavaScript has six fundamental data types. They are the most elemental values that you use to build everything else.

If you want to know the type of a variable, use the typeof operator as in typeof\(name\).

### Truth and Consequences

The name of the data type for holding all sorts of verdicts is boolean.

```JavaScript
const tall = (height > 72);
```
We are assigning true to tall when height is over 72 and assigning false otherwise. The parentheses are completely optional.

```JavaScript
// Just as good. You be You.
const tall = height > 72;
```

#### Combining Booleans
&& means and. It resolves to true if the left and right sides are both true.
|| means or. It resolves to true if either the left side or the right side are true. It also resolves to true if both are true.

Combination  | Result
-------------|-------
true && true   | true
true && false  | false
false && true  | false
true &#124;&#124; true | true
true &#124;&#124; false| true
false &#124;&#124; true| true
false &#124;&#124; false | false

#### Building Blocks vs Long Conditionals
The fun starts when we combine small decisions into larger decisions and take different action.

```JavaScript
const tall = (height > 72);
const big = (weight > 200);
const rich = (income > 500000);
const chargeExtra = ( (big && tall) || rich);
```

Read this as make chargeExtra true when both big and tall or rich. 

Building complex conditionals from a series of simple conditionals allows the reader to get the big idea first and then fill in the details as needed. Consider the alternative:

```JavaScript
if ((weight > 200 && height > 72) || income > 500000) {
  doSomethingGreedy();
}
```

While this saves a lot of lines, it gets confusing as your  logic gets more 'interesting'. Also you will often need the same simple conditional later.

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

TBD unicode, interpolation, multiline TBD, comparisons

### Numbers
JavaScript has a very coder friendly approach to numbers. All of them, regardless of their mathematical type, are of type number.

```JavaScript
typeof(1.5);   // number
typeof(1/3);   // number
typeof(-1000); // number
```
#### Converting Strings to Numbers
JavaScript has two conversion functions that get a lot of use:

```JavaScript
parseInt('12', 10);  // 12
parseFloat('12.5');   // 12.5
```

> Warning
> The second argument to parseInt is the base which almost always defaults to 10. Every so often leaving it off hurts. A lot. 

```JavaScript
parseInt('012', 10);  // Always 12 so do this
parseInt('012');      // Probably 12 but might be 10
parseInt('012', 8);   // Always 10 and the reader remembers why
parseInt('0x12');     // Always 18
parseInt('0x12', 16); // Always 18 and the reader remembers why
```

#### Comparing Numbers
All of the normal comparisons are available to you:
```JavaScript
const tall = (height >= 72);
const exactlySixFoot = (height === 72);
```
> Note: Why triple equals?
Because triple equals checks that the left and right side are both the same type and also the same value. Double equals does not which makes it quirky, sometimes useful and sometimes dangerous.

Comparison   | Result
-------------|-------
1 == false   | false
1 == true    | true ?!?!
0 == false   | true
0 == true    | false



#### 
TBD - sizes

### Admitting Ignorance
In many cases you know what you are missing. By the time you are done processing user input you know which fields were not entered. Information that is deleted may leave a gap in data. You need a way to clearly indicate that we do not know something.

The right data type in this case is null as in:
```JavaScript
const firstName = 'fred';
const middleName = null;
const lastName = 'stone';
```

### Unknown Unknowns
In other cases there is no explicit decision that data is not known. This may mean that a mistake has been made or that the processing just hasn't happened yet.

The undefined data type serves this purpose in JavaScript.

```JavaScript
const firstName = 'fred';
typeof(frstName) // undefined
```
### Comparisons and Coercion
TBD - truthy, etc

### Related Resources
For more information, including coverage of the sixth primitive, Symbol, see:

[https://developer.mozilla.org/en-US/docs/Glossary/Primitive](https://developer.mozilla.org/en-US/docs/Glossary/Primitive)

## Complex Data Types
TBD

## Holding Data (More of the Story) 
Of course you need a way to hold data. Modern JavaScript takes a firm different stance on holding data - most data is not allowed to change. This takes two forms, constant assignment to immutable primitives and constant assignment to mutable complex things.

> It is so not as bad as it sounds... Maybe just ignore my words and take a look at the examples. Then come back to the words. 

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

## Type Conversion
TBD
Here or elsewhere?





