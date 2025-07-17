# Structs in Rust

Structs are custom data types that let you group related values together. Each piece of data in a struct is called a field.

## Defining a Struct
- Use the `struct` keyword and curly braces to define a struct.
- Field names and types are specified inside the struct.

```rust
struct User {
    active: bool,
    username: String,
    email: String,
    sign_in_count: u64,
}
```

---

## Creating an Instance
- Use the struct name and specify values for each field.

```rust
fn main() {
    let user1 = User {
        active: true,
        username: String::from("someusername123"),
        email: String::from("someone@example.com"),
        sign_in_count: 1,
    };
}
```

---

## Mutability
- To change a field, the entire struct instance must be mutable.

```rust
fn main() {
    let mut user1 = User {
        active: true,
        username: String::from("someusername123"),
        email: String::from("someone@example.com"),
        sign_in_count: 1,
    };
    user1.email = String::from("anotheremail@example.com");
}
```

---

## Field Init Shorthand
- If parameter names and field names are the same, you can use shorthand.

```rust
fn build_user(email: String, username: String) -> User {
    User {
        active: true,
        username,
        email,
        sign_in_count: 1,
    }
}
```

---

## Struct Update Syntax
- Create a new instance using values from another instance with `..` syntax.

```rust
let user2 = User {
    email: String::from("another@example.com"),
    ..user1
};
```
- Fields not specified are copied from `user1`.

---

## Tuple Structs
- Structs without named fields, just types.

```rust
struct Color(i32, i32, i32);
struct Point(i32, i32, i32);

fn main() {
    let black = Color(0, 0, 0);
    let origin = Point(0, 0, 0);
}
```
- Each tuple struct is a different type, even if the fields are the same.

---

## Unit-Like Structs
- Structs with no fields, useful for implementing traits without storing data.

```rust
struct AlwaysEqual;

fn main() {
    let subject = AlwaysEqual;
}
```

---

## Summary
- Structs group related data together with named fields.
- Use mutability on the whole instance to change fields.
- Field init shorthand and struct update syntax make code concise.
- Tuple structs and unit-like structs are special struct types.

---

For more, see the [Rust Book: Structs](https://doc.rust-lang.org/book/ch05-01-defining-structs.html)


