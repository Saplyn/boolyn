# C

[C](https://en.cppreference.com/w/c/language), a foundational pillar in the
realm of computer programming. Developed in the early 1970s by Dennis Ritchie
at Bell Labs, it was designed to provide a powerful and flexible tool for
system programming, offering low-level access to memory and hardware while
maintaining a high degree of portability.

## Features

- Compiled
- Statically typed
- Low-level control
- Efficient

## Sample Program (Guessing Game)

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    printf("Guess the number!\n");

    int secret_number = (rand() % 100) + 1;

    while (1) {
        printf("Please input your guess: ");

        int guess;
        scanf("%d", &guess);

        printf("You guessed: %d\n", guess);

        if (guess < secret_number) {
            printf("Too small!\n");
        } else if (guess > secret_number) {
            printf("Too big!\n");
        } else {
            printf("You win!\n");
            break;
        }
    }

    return 0;
}
```
