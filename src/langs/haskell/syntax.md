# Basic Syntax

## Values, Functions & Types

Haskell is a purely functional programming language, which means that every
variable is immutable (value) and every function is a first-class citizen.

```haskell
-- values
x :: Int  -- declare x as an Int
x = 1     -- bind 1 to x
y = 2     -- bind 2 to y (type inferred)
z = x + y -- bind (x + y) to z

-- functions
add :: Int -> Int -> Int -- declare `add` as a function from Int to Int to Int
                         -- (can be seen as "take 2 Ints and return an Int")
add x y = x + y          -- declare `add x + y` as a `x + y`
add 1 2                  -- 3

-- types
Int      -- integer, fixed-precision integer
Integer  -- integer, arbitrary-precision integer
Float    -- floating-point number, single-precision
Double   -- floating-point number, double-precision
Bool     -- boolean, either True or False
Char     -- character, single unicode character
[a]      -- list, a sequence of elements of type `a`
(a, b)   -- tuple, a pair of elements of type `a` and `b`
```

## Operators

```haskell
-- arithmetic 
+ - *  -- (binary, infix)
div    -- (binary, prefix)

-- comparison (binary, infix)
== /= < <= > >=

-- logical
&& ||  -- (binary, infix)
not    -- (unary, prefix)
```

```haskell
-- infix marker
4 `add` 2  -- add 4 2
4 `div` 2  -- div 4 2

-- function application
($) :: (a -> b) -> a -> b
($) f x = f x
$ add 1 2  -- 3

-- function composition
(.) :: (b -> c) -> (a -> b) -> a -> c
(.) f g x = f (g x)
descSort = reverse . sort
```

## List

Unlike imperative programming languages, List in Haskell is considered to be
a primary data structure, and one of the most important and widely used types.

```haskell
-- list of Ints
list = [1, 2, 3]
-- `:` put an element at the beginning of a list
list' = 4 : 5 : 6 : [] 
-- `++` concatenate two lists
list'' = list ++ list' ++ [7, 8, 9]
```

To work with lists, Haskell provides a set of useful functions:

```haskell
head [1, 2, 3, 4]   -- 1
tail [1, 2, 3, 4]   -- [2, 3, 4]
init [1, 2, 3, 4]   -- [1, 2, 3]
last [1, 2, 3, 4]   -- 4
length [1, 2, 3, 4] -- 4
null []             -- True
```

## Flow Control

### Branching

```haskell
-- multiple bindings
isZero :: Int -> Bool
isZero 0 = True
isZero _ = False  -- `_` wildcard, matches anything

-- if-then-else
max :: Int -> Int -> Int
max x y =
  if x > y then
    x
  else
    y
```

### Recursion

In a pure functional language like Haskell, there is no way to change the
value, making loops impossible. Instead, recursion is used to replace its
functionality.

```haskell
-- factorial
factorial :: Int -> Int
factorial 0 = 1                     -- base case, also termination condition
factorial n = n * factorial (n - 1) -- recursive case

-- fibonacci
fib :: Int -> Int
fib 0 = 0
fib 1 = 1
fib n = fib (n - 1) + fib (n - 2)
```

## Custom Types

In Haskell, we can define our own types using `type` and `data` keywords.

```haskell
-- type synonym
type Name = String
type Age = Int

-- data type
data Color = Red | Green | Blue  -- different constructors
data Calculation =
  Add Int Int    -- constructor with parameters
  | Sub Int Int
  | Mul Int Int
  | Div Int Int
calc :: Calculation -> Int
calc (Add x y) = x + y
calc (Sub x y) = x - y
calc (Mul x y) = x * y
calc (Div x y) = x `div` y

-- recursive data type
data PeaNum = Succ PeaNum | Zero
four :: PeaNum
four = Succ $ Succ $ Succ $ Zero

data Tree a = Leaf | Node (Tree a) a (Tree a)
tree :: Tree Int
tree = 
  Node (Node Leaf 1 Leaf) 2 (Node (Node Leaf 3 Leaf) 4 Leaf)
```
