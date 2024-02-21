# Basic Syntax

## Program Structure

In Java, a program is made up of one or more classes, each file is a class.
The class with the `main` method acts as the entry point of the program.

```java
// HelloWorld.java
public class HelloWorld {
    // other methods
    public static void sayHello() { /* ... */ }
    // main method
    public static void main(String[] args) {
        System.out.println("Hello world!");
    }
}
```

## Variables & Types

```java
// variable
int score = 90;
char first_name;
double height = 1.75;

// constant
final int MAX = 100;
final double PI = 3.14;

// array
int[] numbers = {1, 2, 3, 4, 5};
char[] str = new char[5];
```

## Operators

```java
// arithmetic
+ - * / % ++ --

// relational
== != > < >= <=

// bitwise
& | ^ ~ << >>
>>> // Unsigned right shift

// logical
&& || !
// `&&` and `||` are short-circuit operators.

// assignment
= += -= *= /= %= 
```

## Control Flow

### Branching

```java
if (condition) {
    // ...
} else if (condition) {
    // ...
} else {
    // ...
}

switch (expression) {
    case value1:
        // ...
        break;
    case value2:
        // ...
        break;
    default:
        // ...
}
```

### Looping

```java
// while loop
int i = 0;
while (i < 10) {
    System.out.println(i);
}

// do-while loop
int i = 0;
do {
    System.out.println(i);
} while (i < 10);

// for loop
for (int i = 0; i < 10; i++) {
    System.out.println(i);
}

// for each loop
int[] numbers = {1, 2, 3, 4, 5};
for (int number : numbers) {
    System.out.println(number);
}

break;    // exits the loop
continue; // skips the current iteration.

// label jump
outerLoop:
for (int i = 0; i < 5; i++) {
    innerLoop:
    for (int j = 0; j < 5; j++) {
        if (i == 1 && j == 1) {
            // continue with the next iteration of the inner loop
            continue innerLoop;
        }
        if (i == 2 && j == 2) {
            // break out of the outer loop
            break outerLoop;
        }
        System.out.println(i);
    }
}
```

## Functions

```java
// declaration
int add(int num1, int num2) {
    int sum = num1 + num2;
    return sum;
}
add(3, 5); // call

// lambda
Function<Integer, Integer> add = (a, b) -> a + b;
add.apply(3, 5);
```
