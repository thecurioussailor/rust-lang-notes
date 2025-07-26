# Data Types in Rust

Rust is a statically typed language, meaning all variable types must be known at compile time. Data types in Rust are divided into two main categories: scalar and compound types.

## Scalar Types
A scalar type represents a single value. Rust has four primary scalar types:
- **Integers**
- **Floating-point numbers**
- **Booleans**
- **Characters**

---

### Integer Types
- Numbers without a fractional component.
- Signed (`i8`, `i16`, `i32`, `i64`, `i128`, `isize`) and unsigned (`u8`, `u16`, `u32`, `u64`, `u128`, `usize`).
- Default integer type is `i32`.

```rust
let x: i32 = 42;
let y: u8 = 255;
```

---

### Floating-Point Types
- Numbers with fractional parts.
- `f32` (32-bit, single precision) and `f64` (64-bit, double precision, default).

```rust
let x = 2.0;    // f64 by default
let y: f32 = 3.0;
```

---

### Boolean Type
- Either `true` or `false`.

```rust
let is_active: bool = true;
```

---

### Character Type
- Represents a single Unicode scalar value (not just ASCII).

```rust
let letter = 'A';
let emoji = '😻';
```

---

## Compound Types
Compound types can group multiple values into one type. Rust has two primitive compound types:
- **Tuples**
- **Arrays**

---

### Tuple Type
- Group together values of different types.
- Fixed length; cannot grow or shrink.

```rust
let tup: (i32, f64, u8) = (500, 6.4, 1);
```

#### Accessing Tuple Elements
- Pattern matching:

```rust
let tup = (500, 6.4, 1);
let (x, y, z) = tup;
println!("The value of y is: {y}");
```
- By index:

```rust
let x: (i32, f64, u8) = (500, 6.4, 1);
let five_hundred = x.0;
let six_point_four = x.1;
let one = x.2;
```

---

### Array Type
- Collection of values of the same type.
- Fixed length.

```rust
let a = [1, 2, 3, 4, 5];
let months = ["January", "February", "March", "April", "May", "June", "July",
              "August", "September", "October", "November", "December"];
let a: [i32; 5] = [1, 2, 3, 4, 5];
```

#### Accessing Array Elements

```rust
let a = [1, 2, 3, 4, 5];
let first = a[0];
let second = a[1];
```

#### Example: Array Indexing with User Input

```rust
use std::io;

fn main() {
    let a = [1, 2, 3, 4, 5];
    println!("Please enter an array index.");
    let mut index = String::new();
    io::stdin().read_line(&mut index).expect("Failed to read line");
    let index: usize = index.trim().parse().expect("Index entered was not a number");
    let element = a[index];
    println!("The value of the element at index {index} is: {element}");
}
```

---

## Summary
- Rust has scalar (single value) and compound (multiple values) types.
- Scalar: integers, floats, booleans, characters.
- Compound: tuples (mixed types, fixed size), arrays (same type, fixed size).
- Types must be known at compile time.

---

## :: vs . - The Key Difference

### :: (Double Colon) - Static Access
- Used for types, traits, modules, and associated functions
- Access items that don't require an instance
- Examples:
  ```rust
  String::new()           // Associated function
  std::io::stdin()        // Module path
  Vec::<i32>::new()       // Type with generic parameter
  std::collections::HashMap::new()  // Type with module path
  ```

### . (Dot) - Instance Access
- Used for methods and fields on instances
- Access items that require a specific instance
- Examples:
  ```rust
  let s = String::new();
  s.push_str("hello");    // Method on instance
  s.len()                 // Method on instance
  ```

### Important Notes
- **Type annotations** use `::`:
  ```rust
  let x: Vec<i32> = Vec::new();  // Type annotation with ::
  ```
- **Turbofish syntax** uses `::`:
  ```rust
  let x = Vec::<i32>::new();     // Explicit type parameter
  ```
- **Module paths** always use `::`:
  ```rust
  use std::collections::HashMap;  // Module import
  ```
- **Associated constants** use `::`:
  ```rust
  let max = i32::MAX;             // Associated constant
  ```

---

For more, see the [Rust Book: Data Types](https://doc.rust-lang.org/book/ch03-02-data-types.html)