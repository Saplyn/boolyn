# C++

[C++](https://en.cppreference.com/w/cpp/language), or CPP, is an extension of
the C programming language. Bjarne Stroustrup developed C++ in the early 1980s
at Bell Labs, aiming to enhance C's capabilities with features such as
object-oriented programming (OOP), generic programming, and improved type
safety.

## Features

- Compiled
- Statically typed
- Low-level control
- Efficient
- Support object-oriented diagram

## Sample Program (Guessing Game)

```cpp
#include <ctime>
#include <iostream>
#include <random>

int main() {
    std::cout << "Guess the number!" << std::endl;

    std::mt19937 rng(time(0));
    int secret_number = (rng() % 100) + 1;

    while (true) {
        std::cout << "Please input your guess: ";

        int guess;
        std::cin >> guess;

        std::cout << "You guessed: " << guess << std::endl;

        if (guess < secret_number) {
            std::cout << "Too small!" << std::endl;
        } else if (guess > secret_number) {
            std::cout << "Too big!" << std::endl;
        } else {
            std::cout << "You win!" << std::endl;
            break;
        }
    }

    return 0;
}
```
