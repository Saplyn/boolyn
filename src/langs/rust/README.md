# Rust

Rust is a systems programming language that is performant, reliable, and
productive. It is a multi-paradigm, general-purpose language that is safe
and concurrent by design. Created by Graydon Hoare as a personal project
in 2006 and later sponsored by Mozilla, it made its first stable release
in 2015.

## Features

- Compiled
- Statically typed
- Low-level control
- Efficient
- Memory safe
- Expressive

## Sample Program (Guessing Game)

```rust,noplayground
// https://doc.rust-lang.org/book/ch02-00-guessing-game-tutorial.html
use rand::Rng; // external crate
use std::cmp::Ordering;
use std::io;

fn main() {
    println!("Guess the number!");

    let secret_number = rand::thread_rng().gen_range(1..=100);

    loop {
        println!("Please input your guess.");

        let mut guess = String::new();

        io::stdin()
            .read_line(&mut guess)
            .expect("Failed to read line");

        let guess: u32 = match guess.trim().parse() {
            Ok(num) => num,
            Err(_) => continue,
        };

        println!("You guessed: {guess}");

        match guess.cmp(&secret_number) {
            Ordering::Less => println!("Too small!"),
            Ordering::Greater => println!("Too big!"),
            Ordering::Equal => {
                println!("You win!");
                break;
            }
        }
    }
}
```
