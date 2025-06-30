# Borrowing and References in Rust

Borrowing and references let you access data without taking ownership. This helps you write safe, efficient code.

## What is a Reference?
- A reference lets you refer to a value without taking ownership.
- References are created using the `&` symbol.
- The opposite of referencing is dereferencing, done with `*`.

---

## Immutable References

```rust
fn main() {
    let s1 = String::from("hello");
    let len = calculate_length(&s1);
    println!("The length of '{s1}' is {len}");
}

fn calculate_length(s: &String) -> usize {
    s.len()
}
```
- `&s1` passes a reference to `s1` into the function.
- The function can read the value but cannot modify it.
- The original value is still valid after the function call.

---

## Mutable References

```rust
fn main() {
    let mut s = String::from("hello");
    change(&mut s);
    println!("{}", s);
}

fn change(some_string: &mut String) {
    some_string.push_str(", world!");
}
```
- Use `&mut` to create a mutable reference.
- The function can modify the borrowed value.
- The original value is updated after the function call.

---

## Reference Rules
- At any given time, you can have either:
  - One mutable reference, **or**
  - Any number of immutable references
- You cannot have a mutable reference while immutable references exist.
- References must always be valid (no dangling references).

---

## Example: Multiple Mutable References (Error)

```rust
fn main() {
    let mut s = String::from("hello");
    let r1 = &mut s;
    let r2 = &mut s; // Error: cannot borrow `s` as mutable more than once at a time
    println!("{}, {}", r1, r2);
}
```
- Only one mutable reference allowed at a time to prevent data races.

---

## Example: Mixing Mutable and Immutable References (Error)

```rust
fn main() {
    let mut s = String::from("hello");
    let r1 = &s;
    let r2 = &s;
    let r3 = &mut s; // Error: cannot borrow as mutable because it is also borrowed as immutable
    println!("{} {} {}", r1, r2, r3);
}
```
- Cannot have a mutable reference while immutable references are active.

---

## Dangling References

```rust
fn dangle() -> &String {
    let s = String::from("hello");
    &s // Error: `s` will be dropped at the end of the function
}
```
- Returning a reference to a local variable is not allowed (dangling reference).
- Solution: return the value directly to transfer ownership.

```rust
fn no_dangle() -> String {
    let s = String::from("hello");
    s // Ownership is moved out, no reference
}
```

---

## Summary
- References let you access data without taking ownership.
- Use `&` for immutable and `&mut` for mutable references.
- Only one mutable reference or many immutable references at a time.
- No dangling references allowed.

---

For more, see the [Rust Book: References and Borrowing](https://doc.rust-lang.org/book/ch04-02-references-and-borrowing.html)