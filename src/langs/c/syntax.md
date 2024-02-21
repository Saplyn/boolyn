# Basic Syntax

## Program Structure

```c
// optional, when we need external functionality
#include <header>
#include "header.h"

// required, `main()` the entry of every c program.
int main() {
    return 0;
}
```

## Variables & Types

```c
// variable
int age;             // declaration
int score = 90;      // declaration with initialization
float height = 1.75;
char initial = 'J';

// constant
const int MAX = 100;
const double PI = 3.14;

// array
char str[5];                     // declaration
int numbers[] = {1, 2, 3, 4, 5}; // declaration with initialization

// basic types
int, float, double, char, void

// type modifiers
long, short, signed, unsigned

// type conversion
(int) 3.14; // => 3
(float) 3;  // => 3.0
```

## Operators

Note that when doing calculations, compiler will tries to promote the operands to
the same type by converting "lower" type to "higher" type.

```c
// arithmetic
+ - * / % ++ --
// `/` is integer division if both operands are integers.
// `%` is the remainder of the division.

// relational
== != > < >= <=

// logical
&& || !
// `&&` and `||` are short-circuit operators.

// bitwise
& | ^ ~ << >>

// assignment
= += -= *= /= %= <<= >>= &= |= ^=
// `x op= y` is equivalent to `x = x op y`

// conditional
?:
// `x ? y : z` is equivalent to `if (x) {y}; else {z};`
```

## Control Flow

### Branching

```c
// if-else
if (condition) { /* ... */ }
else if (condition) { /* ... */ }
else { /* ... */ }

// switch-case
switch (enumerable) {
    case variant1: /* ... */ break;
    case variant2: /* ... */ break;
    default: /* ... */
}
```

### Looping

```c
// while loop
while (condition) { /* ... */ }

// do-while loop
do { /* ... */ } while (condition);

// for loop
for (init; condition; update) { /* ... */ }
for (int i = 0; i < 10; i++) { /* ... */ }

// break, continue
break;    // exits the loop
continue; // skips the current iteration.
```

### Jumping

```c
// label
label: // statement

// goto
goto label; // jumps to the label.
```

## Functions

```c
// declaration
int add(int a, int b);

// definition (implementation)
int add(int a, int b) {
    return a + b;
}

// calling
int sum = add(3, 5);
```

## Compound Data Types

### Structures

Allowing to group different data types together.

```c
// declaration
struct Point {
    int x;
    int y;
};

// construction
struct Point p1 = {0, 0};

// accessing members
p1.x = 3;
p1.y = 4;
```

### Unions

Allowing storing different data types in the same memory location.
With only one variant (member) being accessible at a time.

```c
// declaration
union Data {
    int i;
    float f;
};

// construction
union Data data;

// accessing members
data.i = 10;    // only `i` is accessible now
data.f = 220.5; // only `f` is accessible now
// note that accessing `i` after assigned `f` is undefined behavior.
```

### Enumerations

Allowing to define a type with a set of named values.

```c
// declaration
enum Color { RED, GREEN, BLUE };

// construction
enum Color c = BLUE;

// Using enum values
if (c == RED) { /* ... */ }
```
