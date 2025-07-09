# Variables in Rust

Variables in Rust are immutable by default. You can declare a variable using the `let` keyword:

```rust
let x: i32 = 123;
println!("the x value is {}", x);
```

## Integer Types

Rust provides several integer types, both signed and unsigned:

- Signed: `i8`, `i16`, `i32`, `i64`, `i128`
- Unsigned: `u8`, `u16`, `u32`, `u64`, `u128`

> **Note:** By default, integer variables are assigned the `i32` type if no type is specified.

## Floating-Point Types

- `f32` (32-bit float)
- `f64` (64-bit float, default for floats)

## Booleans

Booleans are either `true` or `false`:

```rust
let is_male = true;
let is_above_18 = false;

if is_male {
    println!("You are a male");
}

if is_above_18 && is_male {
    println!("You are a legal male.");
}
```

## Strings

There are two main string types:
- `String` (growable, heap-allocated)
- `&str` (string slice, usually used for string literals)

Example:

```rust
let greetings = String::from("Hello, Rust!");
println!("{}", greetings);

let name = "world"; // &str
println!("Hello, {}!", name);
```

## Mutability

Variables are immutable by default. To make a variable mutable, use the `mut` keyword:

```rust
let mut y = 10;
y = 20; // This is allowed
```

## Constants

Constants are declared using the `const` keyword and must have a type annotation:

```rust
const MAX_POINTS: u32 = 100_000;
```

# Shadowing in Rust

Shadowing lets you declare a new variable with the same name as a previous variable. The new variable "shadows" the previous one, so you can reuse the name and even change its type.

## What is Shadowing?
- You can redeclare a variable with `let` using the same name.
- The new variable is a separate binding and can have a different type or value.
- Shadowing is different from mutability: shadowing creates a new variable, mutability allows changing the value of the same variable.

---

## Example: Shadowing

```rust
fn main() {
    let x = 5;           // x = 5
    let x = x + 1;       // x = 6 (shadows previous x)

    {
        let x = x * 2;   // x = 12 (shadows outer x in this scope)
        println!("The value of x in the inner scope is: {x}");
    }

    println!("The value of x is: {x}"); // x = 6 (outer x)
}
```
- Each `let x = ...` creates a new variable named `x`.
- Inner scopes can shadow variables from outer scopes.
- After the inner scope, the outer variable is still accessible.

---

## Shadowing vs. Mutability
- **Shadowing:**
  - Allows changing the type or value by redeclaring with `let`.
  - Each shadowed variable is a new binding.
- **Mutability:**
  - Allows changing the value, but not the type, of the same variable.
  - Use `let mut` to make a variable mutable.

```rust
let spaces = "   ";
let spaces = spaces.len(); // Shadowing: changes type from &str to usize

let mut y = 10;
y = 20; // Mutability: changes value, type stays the same
```

---

## Why Use Shadowing?
- Useful for transforming a value while keeping the same variable name.
- Helps keep code clean and avoids introducing new variable names for each transformation.
- Allows type changes, which mutability does not.

---

For more, see the [Rust Book: Shadowing](https://doc.rust-lang.org/book/ch03-01-variables-and-mutability.html#shadowing)
