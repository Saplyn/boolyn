# Pattern Matching

## Destructuring

```rust,noplayground
// Destructuring a tuple
let (x, y, z) = (1, 2, 3);
let (first, .., last) = (2, 4, 8, 16, 32);
for (index, value) in v.iter().enumerate() {
    println!("{} is at index {}", value, index);
}

// Destructuring a struct
let Point { x, y } = Point::new(1, 2);   // extract x and y
let Vec3 { z, .. } = Vec3::new(4, 5, 6); // extract z, ignore others

// Destructuring an enum
let Some(x) = compute();
```

## `match` Expression

```rust,noplayground
// matching a enum
match compute() {
    Some(x) => println!("got a number: {}", x),
    None => println!("got nothing"),
}

// various match patterns
match x {
    1 => println!("one"),
    2 => println!("two"),
    3 | 4 => println!("three or four"),
    5..=10 => println!("five through ten"),
    _ => {
        print!("it ");
        print!("can ");
        print!("be ");
        println!("anything!");
    },
}

// match guards
match x {
    Some(0) => println!("zero"),
    Some(n) if n < 0 => println!("negative"),
    Some(n) if n > 0 => println!("positive"),
    _ => println!("nothing"),
}

// @ bindings
match x {
    Some(n @ 0) => println!("zero: {}", n),
    Some(n) => println!("non-zero: {}", n),
    None => println!("nothing"),
}

// @ bindings with renaming
let msg = Message::Hello { id: 5 };
match msg {
    Message::Hello {
        id: id_variable @ 3..=7,
    } => println!("Found an id in range: {}", id_variable),
    Message::Hello { id: 10..=12 } => {
        println!("Found an id in another range")
    }
    Message::Hello { id } => println!("Found some other id: {}", id),
}
```

## `if let` and `let else`

```rust,noplayground
if let Some(x) = compute() {
    println!("got a number: {}", x);
} else {
    println!("got nothing");
}

let x = Some(5) else {
    println!("got nothing");
};
```

## `while let` Loop

```rust,noplayground
let mut stack = Vec::new();

stack.push(1);
stack.push(2);
stack.push(3);

while let Some(top) = stack.pop() {
    println!("{}", top);
}
```
