# Dart

<div class="warning">

**This page is <u>INCOMPLETE</u>**

This page is incomplete and is still being written.

</div>

## Program Structure

```dart
// required, `main()` the entry of every dart program.
void main() {
    print('Hello, world!');
}
```

## Variables & Types

```dart
// variable
int score = 90;
String name = 'John';

// type inference
var year = 1998;
var height = 1.75;
var map = {
    'name': 'John',
    'age': 23,
};

// null safety
int? age = null;  // nullable
int age = 23;     // non-nullable

// objects
List<int> numbers = [1, 2, 3];
Map<String, int> dict = {
    'one': 1,
    'two': 2,
};
```

## Operators

```dart
// TODO
```

## Control Flow

```dart
// if statement
if (cond) { /* ... */ }
else if (cond) { /* ... */ }
else { /* ... */ }

// c-style for loop
for (var i = 0; i < 10; i++) { /* ... */ }

// for-in loop
for (var item in items) { /* ... */ }

// while loop
while (cond) { /* ... */ }
```

## Functions

```dart
// function
int add(int a, int b) {
    return a + b;
}
add(1, 2); // => 3

// arrow function
int minus(int a, int b) => a - b;
minus(3, 2); // => 1
```
