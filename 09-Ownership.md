# Ownership in Rust

Rust uses a system called **ownership** to manage memory safely and efficiently. Understanding ownership is key to writing safe and fast Rust code.

## What is Ownership?
- Each value in Rust has a variable that owns it.
- There can only be one owner at a time.
- When the owner goes out of scope, the value is dropped (memory is freed).

---

## Move

```rust
fn main() {
    let s1 = String::from("hello");
    let s2 = s1; // s1 is moved to s2
    // println!("{s1}"); // Error: s1 is no longer valid
}
```
- Assigning a value to another variable moves ownership.
- The original variable is no longer valid after the move.

---

## Clone

```rust
fn main() {
    let s1 = String::from("hello");
    let s2 = s1.clone(); // Deep copy
    println!("s1 = {s1}, s2 = {s2}"); // Both are valid
}
```
- Use `.clone()` to make a deep copy.
- Both variables are valid and own their own data.

---

## Copy

```rust
fn main() {
    let x = 5;
    let y = x;
    println!("x = {x}, y = {y}"); // Both are valid
}
```
- Simple types (integers, bool, char, floats, etc.) are copied, not moved.
- These types implement the `Copy` trait.

---

## Drop

```rust
fn main() {
    let mut s = String::from("hello");
    s = String::from("ahoy"); // Old value is dropped
    println!("{s}");
}
```
- When a variable is reassigned, the old value is dropped (memory freed).

---

## Ownership and Functions

```rust
fn main() {
    let s = String::from("hello");
    takes_ownership(s); // s is moved
    // println!("{s}"); // Error: s is no longer valid

    let x = 5;
    makes_copy(x); // x is copied
    println!("{x}"); // x is still valid
}

fn takes_ownership(some_string: String) {
    println!("{some_string}");
}

fn makes_copy(some_integer: i32) {
    println!("{some_integer}");
}
```
- Passing a variable to a function moves or copies it, depending on the type.

---

## Returning Ownership

```rust
fn main() {
    let s1 = gives_ownership(); // Ownership returned
    let s2 = String::from("hello");
    let s3 = takes_and_gives_back(s2); // s2 moved, s3 gets ownership
}

fn gives_ownership() -> String {
    String::from("yours")
}

fn takes_and_gives_back(a_string: String) -> String {
    a_string
}
```
- Functions can give ownership back by returning values.

---

## What Types Implement Copy?
- All integer types (u32, i32, etc.)
- bool
- char
- All floating-point types (f32, f64)
- Tuples if all elements are Copy (e.g., (i32, i32)), but not (i32, String)

> Note: Types that implement the `Drop` trait cannot implement `Copy`.

---

## Summary
- Assigning or passing ownership moves the value.
- Use `.clone()` for deep copies.
- Simple types are copied, not moved.
- Ownership rules help prevent memory bugs and double frees.

---

For more, see the [Rust Book: Ownership](https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html)



