# A Project Template For Parsing

We will create a project.
The structure of this project can be treated as a template and can be used repeatedly later.

We use [Cargo](https://doc.rust-lang.org/cargo/index.html) to create a project:

```sh
cargo new my_project
```

where `my_project` is the name of the project.

Next, add the project dependencies that are needed by [Rustemo](https://github.com/igordejanovic/rustemo):

```sh
cd my_project
cargo add rustemo
cargo add regex --no-default-features --features std,unicode-perl
cargo add once_cell
cargo add colored
```

The dependencies in the `Cargo.toml` file should look like this:

```toml
[dependencies]
colored = "2.1.0"
once_cell = "1.19.0"
regex = { version = "1.10.5", default-features = false, features = ["std", "unicode-perl"] }
rustemo = "0.6.0"
```

This project will be working together with the parser generated from the previous tutorial.

:arrow_right:  Next: [Parsing](./parsing.md)

:blue_book: Back: [Table of contents](./../README.md)
