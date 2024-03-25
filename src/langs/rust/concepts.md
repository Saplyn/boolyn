# Concepts

## Understanding Lifetimes

When a reference with a lifetime is used, the borrow checker tracks the flow of
where it starts to where it's used, and checks along the way to ensure that no
conflict happens.

Lifetime often coincide with a scope, but they don't have to, the
following code demonstrates this: The lifetime `'a` is alive up until
the end of the code block, however the `if` branch needs a `&mut x` to
mutate `x`. This code compiles because  `&'a x` and `&mut x` don't cause
conflict, as they are in different flows.

```rust,noplayground
let mut x = 114;        // #      
let r = &x;             // ├───── &'a x
if condition {          // ├──┐
    x = 514;            // │  └── &mut x
} else {                // │
    println!("{}", r);  // └───── &'a x
}
```

## Variance: Co/In/Contra-variant

Variance is a concept in type theory, it describes what types are subtypes of
other types, and when a subtype can be used in place of a supertype (and vice
versa). Specifically, if `'b: 'a` (`'b` outlives `'a`), then `'b` is a subtype
of `'a`. There are three kinds of variance: covariant, invariant, and
contravariant. For detailed in-depth reference, see
[The Rust Reference](https://doc.rust-lang.org/reference/subtyping.html)
and [The Rustonomicon](https://doc.rust-lang.org/nomicon/subtyping.html).

A type is covariant if we can use a subtype in place of the type.

```rust,noplayground
// covariant in 'short
fn covariant<'short>(s: &'short str);
let valid: &'static str;
let valid: &'longer str;  // 'longer: 'short  ('longer outlives 'short)

// covariant in T
fn covariant<'short>(v: &Vec<&'short str>);
let valid: &Vec<&'longer str>;  // 'longer: 'short

/*
'short              ----
'longer     ----------------
'static --------------------------------
*/
```

A type is invariant if we must provide exactly the same type.

```rust,noplayground
fn invariant<'exact>(
    v: &mut Vec<&'exact str>
    str: &'exact str
) {
    v.push(str);
}

// will otherwise allow short-lived str be seen as 'static
let invalid: &mut Vec<&'static str>;
```

A type is contravariant if we can use a supertype in place of the type.

```rust,noplayground
fn contravariant(s: &'static str);        // strict, accepts fewer types
fn contravariant<'short>(s: &'short str); // flexible, accepts more types

let longer: &'static str; // more useful, lives longer
let short: &'short str;   // less useful, lives shorter
```
