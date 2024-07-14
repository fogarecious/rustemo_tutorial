# Changing Actions For Terminals

We can change the default action for terminals.
For a regular expression terminal, we can change the `fn` that will be executed when the terminal is parsed.
For example:

```text
S: A;

terminals

A: /[a-z]+/;
```

Terminal `A` is converted to:

```rust
pub type A = String;

pub fn a(_ctx: &Ctx, token: Token) -> A {
    token.value.into()
}
```

We can add a `println!` to `fn a`:

```rust
pub fn a(_ctx: &Ctx, token: Token) -> A {
    println!("A is parsed");
    token.value.into()
}
```

In the output, `A is parsed` will come before `Accept`, which means `fn a` is executed before the whole input is parsed completely.

Since there is no actions for string terminals, we cannot change its behavior.

<!-- :arrow_right:  Next:  -->

:blue_book: Back: [Table of contents](./../README.md)
