# Basic Syntax

## Variables & Types

```js
// variable
var score = 90;       // old-fashioned
let name = 'Saplyn';  // preferred in modern JS
// var vs let: https://stackoverflow.com/questions/762011/what-is-the-difference-between-let-and-var

// constant
const PI = 3.14;      // cannot be reassigned

// array (dictionary, associative array)
let numbers = [1, 2, 3, 4, 5];
let names = ['Saplyn', 'Moxie', 'Nyx'];
let mixed = [1, 'Saplyn', true, { name: 'Moxie' }];

// basic types
number, string, boolean
null       // absence of value
undefined  // uninitialized variable
symbol     // guaranteed unique value type
// symbol: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Symbol
```

## Operators

```js
// arithmetic
+ - * / % ++ --
// `/` is floating-point division
// `%` is the remainder of the division

// relational
== !=    // loss equality
=== !==  // strict equality
>= <= > <

// logical
&& || !
// `&&` and `||` are short-circuit operators.

// bitwise
& | ^ ~ << >> >>>

// assignment
= += -= *= /= %=
```

## Control Flow

### Branching

```js
// if-else statement
if (score >= 90) {
  console.log('A');
} else if (score >= 80) {
  console.log('B');
} else {
  console.log('C');
}

// switch statement
switch (score) {
  case 90:
    console.log('A');
    break;
  case 80:
    console.log('B');
    break;
  default:
    console.log('C');
}

// ternary operator
let result = (score >= 60) ? 'Pass' : 'Fail';

// nullish coalescing operator
let name = null;
let username = name ?? 'Anonymous';
```

### Looping

```js
// while loop
let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}

// do-while loop
let j = 0;
do {
  console.log(j);
  j++;
} while (j < 5);

// for loop
for (let k = 0; k < 5; k++) {
  console.log(k);
}

// for-in loop (iterate over object properties)
let person = { name: 'Saplyn', age: 25 };
for (let key in person) {
  console.log(key, person[key]);
}

// for-of loop (iterate over iterable objects)
let numbers = [1, 2, 3, 4, 5];
for (let number of numbers) {
  console.log(number);
}

break // exit the loop
continue // skip the rest of the loop
```

## Functions

```js
// function declaration
function add(a, b) {
  return a + b;
}
let sum = add(3, 5);

// function expression (function as value)
let greet = function(name) {
  console.log(`Hello, ${name}!`);
};
greet('Saplyn');

// arrow function (ES6)
let greet = (name) => {
  console.log(`Hello, ${name}!`);
};
greet('Saplyn');
```
