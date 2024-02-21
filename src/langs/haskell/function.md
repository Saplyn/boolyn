# Function

## Guards

Guards are a way to define a function by pattern matching on the input
arguments. They are defined by a series of boolean expressions.

```haskell
max' :: Int -> Int -> Int
max' x y
  | x > y     = x
  | otherwise = y

fac n
  | n <= 1    = 1
  | otherwise = n * fac (n-1)
```

## `let` and `where`

In functions, `let` and `where` can be used to declare local expression aliases
in a function.

```haskell
inRange l r x =
  let in_lower_bound = l <= x
      in_upper_bound = r >= x
  in
    in_lower_bound && in_upper_bound

inRange l r x =
  in_lower_bound && in_upper_bound
  where
    in_lower_bound = l <= x
    in_upper_bound = r >= x
```

## Accumulator

Accumulator is a common pattern in functional programming to avoid stack
overflow when using recursion. It's also known as tail recursion.

```haskell
fac n = aux n 1  -- `aux` is a helper function
  where
    aux n acc    -- `aux` is declared here, and `acc` is the accumulator
      | n <= 1    = acc
      | otherwise = aux (n - 1) (n * acc)
```

## Higher Order Function

A higher order function is a function that takes a function as an argument or
returns a function as a result.

```haskell
app :: (a -> b) -> a -> b -- `app` takes a function `a -> b` and an argument `a`
app f x = f x             -- and returns a result `b`

add1 x = x + 1
app add1 1     -- 2
```

## Lambda Function

Lambda function is an anonymous function that is created using the `\` symbol.

```haskell
(\x -> x + 1) 1      -- 2
(\x y -> x + y) 1 2  -- 3

-- as first-class citizens, lambda functions can be bind to a name
add = \x y -> x + y
```

## Currying

In Haskell, any function can be rewritten to take only one argument:

```haskell
-- the function that takes 3 args
f :: a -> b -> c -> d
-- can be written as:
f :: a -> (b -> (c -> d))
-- a func that takes 1 arg and returns a func that takes 1 arg
-- which returns a func that takes 1 arg and returns the result
```

## Partial Application

Partial application is the process of supplying a function with fewer arguments
than it requires, resulting in a new function that takes the remaining
arguments.

```haskell
add :: Int -> Int -> Int
add = (\x -> (\y -> x + y))

map :: (a -> b) -> [a] -> [b]
doubleList :: [Int] -> [Int]
doubleList = map (\x -> x * 2)
```

## Folding

Folding is a way to reduce a list to a single value. It takes a binary function,
a starting value, and a list to fold up. In Haskell, there are two folding
functions: `foldl` and `foldr`.

```haskell
foldr :: (a -> b -> b) -> b -> [a] -> b

foldr (+) 0 [1, 2, 3] -- 1 + (2 + (3 + 0)) = 6
sum    = foldr (+) 0
and    = foldr (&&) True
or     = foldr (||) False
length = foldr (\x -> (+) 1) 0
length = foldr (const $ (+) 1) 0
map f  = foldr ((:) . f) []

-- https://wiki.haskell.org/Fold#List_folds_as_structural_transformations
foldr (\x acc -> <term>) <start_acc> <list>
foldl (\acc x -> <term>) <start_acc> <list>
```
