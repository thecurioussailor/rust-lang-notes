# Borsh Serialization in Rust

Borsh is a binary serialization format designed for speed, efficiency, and deterministic behavior. Commonly used in blockchain projects (e.g., NEAR protocol).

---

## Key Points
- **Borsh** stands for Binary Object Representation Serializer for Hashing.
- Used for serializing and deserializing Rust structs to/from binary.
- Requires the `borsh` crate and derive macros.

---

## Usage
- Add to `Cargo.toml`:
  ```toml
  borsh = "0.10"
  borsh-derive = "0.10"
  ```
- Import traits:
  ```rust
  use borsh::{BorshSerialize, BorshDeserialize};
  ```
- Annotate your struct:
  ```rust
  #[derive(BorshSerialize, BorshDeserialize, Debug)]
  struct User {
      username: String,
      password: String,
  }
  ```

---

## Example
```rust
let user = User {
    username: String::from("Alice"),
    password: String::from("secret"),
};

// Serialize to bytes
let mut bytes = Vec::new();
user.serialize(&mut bytes).unwrap();

// Deserialize from bytes
let decoded = User::try_from_slice(&bytes).unwrap();
println!("{:?}", decoded);
```

---

## Notes
- `serialize` writes the struct as bytes to a buffer.
- `try_from_slice` reconstructs the struct from bytes.
- Both methods return `Result` types, so handle errors as needed.
- Borsh is deterministic: same input always produces the same output.