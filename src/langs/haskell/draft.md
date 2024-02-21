# Unsorted Notes

## List Comprehension

List comprehension is a concise way to generate lists in Haskell.

```haskell
[ <gen> | <elem> <- <list>, ..., <guard>, ...]

[ 2*x | x <- [1, 2, 3] ]        => [2, 4, 6]
[ 2*x | x <- [1, 2, 3], x > 1 ] => [4, 6]

[ (x,y) | x <- [1, 2, 3], y <- ['a', 'b'] ]
  => [(1, 'a'), (1, 'b'), (2, 'a'), (2, 'b'), (3, 'a'), (3, 'a')]
```
