# Conditionals and Loops in Rust

## If Statements

Use `if`, `else if`, and `else` for conditional logic:

```rust
let is_even = true;

if is_even {
    println!("It is an even number");
} else {
    println!("It is an odd number");
}
```

- The condition must be a `bool`.
- No parentheses are needed around the condition.

## Loops

### For Loop

Iterate over a range:

```rust
for i in 0..10 {
    println!("{}", i);
}
```
- `0..10` is a range from 0 to 9 (end is exclusive).

### While Loop

```rust
let mut n = 0;
while n < 5 {
    println!("{}", n);
    n += 1;
}
```

### Loop (Infinite Loop)

```rust
let mut count = 0;
loop {
    if count == 3 {
        break;
    }
    println!("count: {}", count);
    count += 1;
}
```

## Example: Get First Word from a String

```rust
fn get_first_word(sentence: String) -> String {
    let mut ans = String::new();
    for char in sentence.chars() {
        if char == ' ' {
            break;
        }
        ans.push(char);
    }
    ans
}

fn main() {
    let sentence = String::from("my name is harkirat");
    let first_word = get_first_word(sentence);
    println!("First word is: {}", first_word);
}
```

---

For more, see the [Rust Book: Control Flow](https://doc.rust-lang.org/book/ch03-05-control-flow.html)