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

---

For more details, see the [Rust Book: Variables and Mutability](https://doc.rust-lang.org/book/ch03-01-variables-and-mutability.html)
