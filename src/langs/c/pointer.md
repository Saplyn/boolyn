# Pointer

## Basic

Pointers are a special type of variable, it stores the memory address of
another variable, instead of the value of the variable itself.

```c
int a = 1;

// `&` is the address-of operator
int *p = &a; // `p` is a pointer to `a`

// `*` is the dereference operator
*p = 2; // `a` is now 2
```

Pointers support pointer arithmetic, which "shifts" the pointer to another
location in memory.

```c
int arr[3] = {1, 2, 3};
int *p = arr; // `p` points to `arr[0]`

p++; // now points to `arr[1]`
p++; // now `arr[2]`
```

## Const
