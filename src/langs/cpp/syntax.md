# "Plus"-ed Syntax

C++ is a superset of C, and nearly every valid C program is a valid C++
program. For this reason, please refer to the [C section](../c/syntax.md) for
the basic syntax of C++.

## Types

```cpp
// boolean
bool b = true;  // native boolean type, without `cstdbool`

// auto typing (type inference)
auto x = 6;   // x is an int
auto y = 3.14; // y is a double

// decltype typing (type inference)
int i = 114;
decltype(i) j = 514; // j is an int

// using type (type alias)
using Distance = double;
Distance d = 5.0; // d is a double

// nullptr
int* p = nullptr; // p is a pointer to int

// reference
int i = 1919;
int& r = i; // r is a reference to i
r = 810;    // i is now 810, r is just another name for i
```

## Namespaces

```cpp
namespace lyn {
    int number;  // number is a member of namespace lyn (lyn::number)
}

int main() {
    lyn::number = 32;
}
```

## Functions

```cpp
// default arguments
void print(int x, int y = 0) {
    std::cout << x << " " << y << std::endl;
}
print(5);     // => 5 0
print(5, 10); // => 5 10

// function overloading
int add(int x, int y) { return x + y; }
double add(double x, double y) { return x + y; }
add(1, 2);     // => 3
add(1.1, 2.2); // => 3.3

// lambda
auto add = [/* captures */](int x, int y) { return x + y; };
add(1, 2); // => 3
```

## Dynamic Memory

```cpp
// new and delete
int* p = new int; // allocate memory for an int
*p = 1919;
delete p; // release memory

// new[] and delete[]
int* p = new int[5]; // allocate memory for 5 integers
p[0] = 1919;
delete[] p; // release memory
```
