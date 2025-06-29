# Functions in Rust

Functions are declared using the `fn` keyword. They can take parameters and return values.

## Example

```rust
fn main() {
    let a = 34;
    let b = 90;

    println!("sum: {}", do_sum(a, b));
}

fn do_sum(a: i32, b: i32) -> i32 {
    a + b // The last expression is returned
}
```

- Function names are usually written in snake_case.
- Parameters must have types.
- The return type is specified after `->`.
- The last expression is returned automatically (no `return` needed unless you want to return early).

## Notes
- Functions can return nothing (unit type `()`), which is the default if no return type is specified.
- You can use `return` to return early from a function.

---

For more, see the [Rust Book: Functions](https://doc.rust-lang.org/book/ch03-03-how-functions-work.html)