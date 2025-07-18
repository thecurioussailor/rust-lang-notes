# Error Handling in Rust

Rust handles errors with two main strategies: unrecoverable errors (using `panic!`) and recoverable errors (using the `Result` type).

## Unrecoverable Errors with panic!
- Use `panic!` when your program cannot recover from an error.
- The program will print an error message and exit.

```rust
fn main() {
    panic!("crash and burn");
}
```

- Example: Index out of bounds will also cause a panic.

```rust
fn main() {
    let v = vec![1, 2, 3];
    println!("{}", v[99]); // This will panic
}
```

---

## Recoverable Errors with Result
- The `Result` enum is used for functions that can succeed or fail.
- `Result<T, E>` is either `Ok(T)` for success or `Err(E)` for error.

```rust
use std::fs;

fn main() {
    let result = fs::read_to_string("example.txt");
    match result {
        Ok(content) => {
            println!("File content: {}", content);
        },
        Err(err) => {
            println!("Error: {}", err)
        }
    }
    println!("This is new line");
}
```

---

## Matching on Different Errors
- You can match on specific error kinds for more control.

```rust
use std::fs::File;
use std::io::ErrorKind;

fn main() {
    let greeting_file_result = File::open("hello.txt");
    let greeting_file = match greeting_file_result {
        Ok(file) => file,
        Err(error) => match error.kind() {
            ErrorKind::NotFound => match File::create("hello.txt") {
                Ok(fc) => fc,
                Err(e) => panic!("Problem creating the file: {e:?}"),
            },
            _ => panic!("Problem opening the file: {error:?}"),
        },
    };
}
```

---

## The ? Operator
- The `?` operator is a shortcut for propagating errors.
- If the result is `Ok`, the value is returned. If it's `Err`, the error is returned from the function.

```rust
use std::fs::File;

fn read_file() -> Result<String, std::io::Error> {
    let content = std::fs::read_to_string("example.txt")?;
    Ok(content)
}
```

---

## Summary
- Use `panic!` for unrecoverable errors.
- Use `Result` for recoverable errors and handle them with `match` or the `?` operator.
- Matching on error kinds allows for more specific error handling.
- Rust encourages handling errors explicitly for safer code.

---

For more, see the [Rust Book: Error Handling](https://doc.rust-lang.org/book/ch09-02-recoverable-errors-with-result.html)



