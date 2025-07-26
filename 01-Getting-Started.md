# Getting Started with Rust

## Install Rust

Get Rust from the official site: [rust-lang.org/tools/install](https://www.rust-lang.org/tools/install)

The easiest way is to use `rustup`.

## VS Code Extensions (Recommended)
- **rust-analyzer**
- **CodeLLDB**
- **Even Better TOML**

## Create a New Project

1. Make a folder and go inside it:
   ```bash
   mkdir my_project
   cd my_project
   ```
2. Initialize the project:
   ```bash
   cargo init
   ```
   This creates `src/main.rs` and `Cargo.toml`.

## Run Your Code

```bash
cargo run
```

## Useful Commands
- `cargo check` – Check code quickly
- `cargo build` – Build project
- `cargo build --release` – Build optimized release version (creates target/release)
- `cargo test` – Run tests
- `cargo fmt` – Format code

---

For more, see the [Rust Book](https://doc.rust-lang.org/book/) or [Rust by Example](https://doc.rust-lang.org/rust-by-example/)


