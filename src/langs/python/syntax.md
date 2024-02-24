# Basic Syntax

## Variables

```python
# variable
score = 90
name = "Saplyn"
MAX = 100

# string
name = "Saplyn"
desc = """
he's a
very very
long
cat
"""
fstr = f"Hello, {name}!"
```

## Operators

```python
# arithmetic
+ - * / % // **
# `/` is float division
# `//` is floor division
# `**` is exponentiation

# comparison
== != < > <= >=

# logical
and or not

# assignment
= += -= *= /= %= //= **=
```

## Flow Control

### Branching

```python
# if-else
if age < 12:
    print("Kitty!")
elif age < 18:
    print("Cat!")
else:
    print("Adult Cat!")

# simple if-else
print("Kitty!") if age < 12 else print("Cat!")
```

### Looping

```python
# while
i = 0
while i < 5:
    print(i)
    i += 1

# for
for i in range(5):
    print(i)
for i in range(1, 5):
    print(i)
fruits = ['apple', 'banana', 'orange']
for fruit in fruits:
    print(fruit)

# loop-else
# code inside the else block will be executed only if the loop completes all
# iterations without any break statement being encountered.
i = 1
while i <= 5:
    print(f"loop: {i}")
    i += 1
else:
    print("Loop completed without any breaks")

# break
i = 0
while True:
    i += 1
    if i > 5:
        break

# continue
for i in range(5):
    if i % 2 == 0:
        continue
    print(i)
```

## Functions

```python
# definition
def add(a, b=1):
    return a + b
add(3, 4)     # => 7
add(3)        # => 4
add(b=3, a=4) # => 7, keyword arguments

# arbitrary arguments
def add(*args):
    return sum(args)
add(1, 2, 3, 4, 5) # => 15

# arbitrary keyword arguments
def display(**kwargs):
    for key, value in kwargs.items():
        print(f"{key}: {value}")
display(name="Saplyn", age=18) # => name: Saplyn, age: 18
```

## Lists, Tuples & Dictionaries

```python
# list
numbers = [1, 2, 3, 4, 5]
numbers[0]   # => 1
numbers[-1]  # => 5, backward index
numbers[1:3] # => [2, 3], slicing
numbers[::2] # => [1, 3, 5], step slicing

# tuple (immutable)
normal_tuple = (1, 2, 4, 8, 16)
single_tuple = 1,
empty_tuple  = ()

# dictionary (map)
person = {
    "name": "Saplyn",
    "age": 18,
    "height": 1.75
}
person["name"]  # => "Saplyn"
person["age"]   # => 18
person["height"]# => 1.75
```
