# Memory Management in Rust

Rust manages memory through a system of ownership, borrowing, and lifetimes, allowing safe and efficient memory usage without a garbage collector.

## Stack vs Heap
- **Stack:**
  - Fast, fixed-size memory allocation.
  - Stores values with known, fixed size at compile time (e.g., integers, floats).
  - Data is pushed and popped in a last-in, first-out order.
- **Heap:**
  - Slower, dynamic memory allocation.
  - Used for values with unknown or variable size (e.g., `String`, `Vec<T>`).
  - Data is allocated and freed manually (by Rust's ownership system).

---

## Ownership and Memory
- Each value in Rust has a single owner.
- When the owner goes out of scope, Rust automatically frees the memory (calls `drop`).
- No need for manual memory management or garbage collection.

```rust
fn main() {
    let s = String::from("hello"); // Allocated on the heap
    // s is valid here
} // s goes out of scope, memory is freed automatically
```

---

## Move, Clone, and Copy
- **Move:** Transfers ownership, old variable is invalid.
- **Clone:** Deep copy, both variables own their own data.
- **Copy:** Simple types (like integers) are copied, not moved.

---

## Borrowing and References
- Borrowing lets you access data without taking ownership.
- Immutable references (`&T`): read-only access.
- Mutable references (`&mut T`): write access, but only one at a time.
- Prevents data races and dangling pointers at compile time.

---

## No Garbage Collector
- Rust does not use a garbage collector.
- Memory is managed at compile time using ownership and borrowing rules.
- This leads to predictable performance and no runtime overhead for memory management.

---

## Summary
- Rust manages memory safely and efficiently using ownership, borrowing, and lifetimes.
- Stack is for fixed-size, fast allocations; heap is for dynamic, growable data.
- Memory is freed automatically when values go out of scope.
- No garbage collector needed—Rust enforces safety at compile time.

---

For more, see the [Rust Book: Memory Management](https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html)


