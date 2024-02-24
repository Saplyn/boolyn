# Basic Syntax

## Program Structure

```rust
// optional, when we need external functionality
// notably, rust has a prelude that is used by default.
use std::io;

// required, `main()` the entry of every rust program.
fn main() {
    println!("Hello, world!");
}
```

## Variables & Types

```rust,noplayground
// variable
// most of the time, rustc infers the type.
let score = 90;        // immutable variable
let first_name: char;  // type annotation, optional
let mut height = 1.75; // mutable variable

// constant (computable at compile time)
const MAX: i32 = 100;  // requires type annotation
const PI: f64 = 3.14;  // requires initialization too

// array
let numbers = [1, 2, 3, 4, 5];
let mut str: [char; 5];

// tuple
let tup = (500, 6.4, 1);
let tuple: (i32, f64, char) = (42, 6.28, 'J');

// shadowing
let x = 5;     // immutable (5)
let x = x + 1; // shadowing, new variable (6)
let x = x * 2; // shadowing, another new variable (12)

// basic types
i8, i16, i32, i64, i128
u8, u16, u32, u64, u128
isize, usize // architecture dependent
f32, f64
char // unicode scalar value
bool

// type conversion
let x: i32 = 42;
let y: f64 = x as f64;
let z: i32 = y as i32;
```

## Operators

```rust,noplayground
// arithmetic
+ - * / %
// `/` is integer division if both operands are integers.
// `%` is the remainder of the division.

// relational
== != > < >= <=

// logical
&& || !
// `&&` and `||` are short-circuit operators.

// bitwise
& | ^ ! << >>

// assignment
= += -= *= /= %= <<= >>= &= |= ^=
```

## Control Flow

### Branching

Branching in Rust is more powerful than just this, for details, see the
[Pattern Matching chapter](pattern_matching.md).

```rust,noplayground
// if-else expression (can "return" values)
if condition { /* ... */ }
else if condition { /* ... */ }
else { /* ... */ }

// match expression (can "return" values)
match value {
    pattern1 => /* ... */,
    pattern2 => /* ... */,
    _ => /* ... */,  // catch-all (wildcard)
}
```

### Looping

```rust,noplayground
// loop expression (while true)
loop { /* ... */ }

// while loop
while condition { /* ... */ }

// for loop
for element in iterable { /* ... */ }

// range
1..=5 // 1, 2, 3, 4, 5
1..5  // 1, 2, 3, 4

// break and continue
loop {
    if condition { break; }
    if condition { continue; }
}

// the `loop` can be labeled and `break` to the label.
'outer: loop {
    'inner: loop {
        break 'outer;
    }
}

// it can also `break` with a value
let result = loop {
    if condition { break 1; }
    else { break 2; }
};
```

## Functions

This is only a brief introduction to functions and closures. For details, see
the [Function chapter](function.md).

```rust,noplayground
// function
// fn name(param: type) -> return_type { /* ... */ }
fn add(a: i32, b: i32) -> i32 {
    a + b // last expression implicitly returned
}
let sum = add(3, 5);

// closure (anonymous function)
let closure = |a: i32, b: i32| -> i32 { a + b }; // functions are values.
let add = |a, b| a + b;  // type is inferred.
let sum = add(3, 5);
```

## Structs

```rust,noplayground
struct Point {
    // fields are private by default
    x: i32,
    // `pub` makes the field public
    pub y: i32,
}

// methods
impl Point {
    // associated function, also constructor
    fn new(x: i32, y: i32) -> Point {
        Point { x, y }
    }
    // captures `self` by immutable reference
    fn get_x(&self) -> i32 {
        self.x
    }
    // captures `self` by mutable reference
    fn set_x(&mut self, x: i32) {
        self.x = x;
    }
}

// method implementation can be separated
impl Point {
    // consumes `self`
    fn move_to(self, x: i32, y: i32) -> Point {
        Point { x, y }
    }
}

// construction
let p0 = Point::new(0, 0);
let x = p.get_x();
let p1 = Point {
    x, // field init shorthand
    y: 4
};
let p2 = Point { y: 4, ..p1 }; // struct update syntax
```

```rust,noplayground
// tuple struct
struct Color(i32, i32, i32);
let black = Color(0, 0, 0); // construction
let r = black.0; // accessing fields by index
let g = black.1;
let b = black.2;

// unit-like struct (no fields, marker)
struct PlayerMarker;
```

## Enums

```rust,noplayground
// marker enum
enum IpAddrKind {
    V4,
    V6,
}
let four = IpAddrKind::V4;
let six = IpAddrKind::V6;

// with data
enum AppError {
    NoContext,
    IoError(io::Error),
    InvalidInput {
        encountered: String,
        expected: String
    },
}
let unknown = AppError::NoContext;
let io_err = AppError::IoError(/* ... */);
let invalid = AppError::InvalidInput {
    encountered: "sapling".to_string(),
    expected: "saplyn".to_string()
};

// methods (like structs)
impl AppError {
    fn is_io_error(&self) -> bool {
        match self {
            AppError::IoError(_) => true,
            _ => false,
        }
    }
}
```
