# Typed JS

TypeScript is a superset of JavaScript, and it not possible to learn TypeScript
without learning JavaScript. For this reason, please refer to the
[JavaScript](../javascript/README.md) section for the basics.

## Type Annotations

```ts
// typing variables
let n: number = 1;
let s: string = "hello";
let b: boolean = true;
let a: number[] = [1, 2, 3];
let o: {
    name: string,
    age: number
} = { name: "John", age: 30 };

// special types
let n: null = null;
let u: undefined = undefined;

// any type, opt out of type checking
let a: any = 1;

// typing functions
function add(a: number, b: number): number {
  return a + b;
}
```
