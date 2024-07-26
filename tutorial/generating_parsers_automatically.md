# Generating Parsers Automatically

Sometimes, we may want to generate parsers while running our program (i.e., `cargo run`).
In this case, we can use [rustemo-compiler](https://docs.rs/rustemo-compiler/latest/rustemo_compiler/index.html) (i.e., the library of `rcomp`) in the build script of [Cargo](https://doc.rust-lang.org/cargo/index.html).

First, we have to add [rustemo-compiler](https://docs.rs/rustemo-compiler/latest/rustemo_compiler/index.html) to the build dependencies.

```sh
cargo add --build rustemo-compiler
```

The `build-dependencies` in `Cargo.toml` should look like this:

```toml
[build-dependencies]
rustemo-compiler = "0.6.0"
```

Next, we create the build script, `build.rs`:

```rust
fn main() {
    rustemo_compiler::Settings::new().process_dir().unwrap();
}
```

For more information about the settings, please refer to [rustemo_compiler::Settings](https://docs.rs/rustemo-compiler/latest/rustemo_compiler/struct.Settings.html).
Note that `build.rs` is put in the project root directory, sharing the same parent as `src` folder's.

Assume our grammar is called `my_grammar.rustemo` and is put in the folder `src`.
Previously, we use `rcomp` to generate parsers and include them in `main.rs` like this:

```rust
mod my_grammar;
mod my_grammar_actions;
```

Now, we remove the two lines and include the auto-generated parsers in the following way:

```rust
rustemo::rustemo_mod!(my_grammar, "/src");
rustemo::rustemo_mod!(my_grammar_actions, "/src");
```

The parsers will be generated automatically when we run `cargo run`.

<!-- :arrow_right:  Next:  -->

:blue_book: Back: [Table of contents](./../README.md)
