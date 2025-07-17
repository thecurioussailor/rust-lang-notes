# Methods in Rust

Methods are similar to functions, but are defined within the context of a struct, enum, or trait object. The first parameter of a method is always `self`, representing the instance the method is called on.

## Defining Methods
- Methods are defined inside an `impl` block for a struct.
- The first parameter is usually `&self` (a reference to the instance).

```rust
struct Rectangle {
    width: u32,
    height: u32,
}

impl Rectangle {
    fn area(&self) -> u32 {
        self.width * self.height
    }
}

fn main() {
    let rect1 = Rectangle { width: 30, height: 50 };
    println!("The area of the rectangle is {} square pixels.", rect1.area());
}
```
- Call methods using dot syntax: `instance.method()`.

---

## Methods with the Same Name as Fields
- Methods can have the same name as struct fields.

```rust
impl Rectangle {
    fn width(&self) -> bool {
        self.width > 0
    }
}

fn main() {
    let rect1 = Rectangle { width: 30, height: 50 };
    if rect1.width() {
        println!("The rectangle has a nonzero width; it is {}", rect1.width);
    }
}
```

---

## Methods with More Parameters
- Methods can take additional parameters besides `self`.

```rust
impl Rectangle {
    fn can_hold(&self, other: &Rectangle) -> bool {
        self.width > other.width && self.height > other.height
    }
}

fn main() {
    let rect1 = Rectangle { width: 30, height: 50 };
    let rect2 = Rectangle { width: 10, height: 40 };
    let rect3 = Rectangle { width: 60, height: 45 };
    println!("Can rect1 hold rect2? {}", rect1.can_hold(&rect2));
    println!("Can rect1 hold rect3? {}", rect1.can_hold(&rect3));
}
```

---

## Associated Functions
- Functions defined in an `impl` block without `self` are called associated functions.
- Called using `::` syntax, e.g., `Rectangle::square(3)`.
- Often used as constructors.

```rust
impl Rectangle {
    fn square(size: u32) -> Self {
        Self { width: size, height: size }
    }
}

fn main() {
    let sq = Rectangle::square(10);
}
```

---

## Multiple impl Blocks
- You can have multiple `impl` blocks for a single struct.

```rust
impl Rectangle {
    fn area(&self) -> u32 {
        self.width * self.height
    }
}

impl Rectangle {
    fn can_hold(&self, other: &Rectangle) -> bool {
        self.width > other.width && self.height > other.height
    }
}
```

---

## Summary
- Methods are functions defined within an `impl` block and operate on an instance via `self`.
- Associated functions do not take `self` and are called with `::`.
- Methods can take additional parameters and can share names with fields.
- Multiple `impl` blocks are allowed for a single type.

---

For more, see the [Rust Book: Methods](https://doc.rust-lang.org/book/ch05-03-method-syntax.html)

