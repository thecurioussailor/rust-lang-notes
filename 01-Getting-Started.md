# Getting Started with Rust

## Installation

Install Rust from the official website: [https://www.rust-lang.org/tools/install](https://www.rust-lang.org/tools/install)

The recommended way to install Rust is through `rustup`, which manages Rust versions and associated tools.

## Recommended VS Code Extensions

For the best Rust development experience, install these extensions:

- **rust-analyzer** - Provides IDE features like code completion, go-to-definition, and error checking
- **CodeLLDB** - Debugger support for Rust applications
- **Even Better TOML** - Enhanced TOML file support for `Cargo.toml` files

## Initializing a Rust Project

### Creating a New Binary Project

Follow these steps to create a new Rust binary project:

1. **Create a new directory:**
   ```bash
   mkdir my_rust_project
   cd my_rust_project
   ```

2. **Initialize the Rust project:**
   ```bash
   cargo init
   ```

   This creates:
   - `src/main.rs` - Your main source file
   - `Cargo.toml` - Project configuration and dependencies

### Project Structure

After initialization, your project structure will look like:

## Running Your Code

To compile and run your Rust program:

```bash
cargo run
```

## Additional Useful Commands

- **Check your code without building:** `cargo check`
- **Build without running:** `cargo build`
- **Build for release (optimized):** `cargo build --release`
- **Run tests:** `cargo test`
- **Format your code:** `cargo fmt`
- **Lint your code:** `cargo clippy`

## Next Steps

- Check out the [Rust Book](https://doc.rust-lang.org/book/) for comprehensive learning
- Explore [Rust by Example](https://doc.rust-lang.org/rust-by-example/) for practical examples
- Try the [Rustlings](https://github.com/rust-lang/rustlings) exercises for hands-on practice


