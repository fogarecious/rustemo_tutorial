# Default Actions For Terminals

The default action for a regular expression terminal is to convert its internal data type to `String`.
For example, consider the grammar below:

```text
S: A;

terminals

A: /\d+/;
```

The action of terminal `A` is to convert `A`'s internal data type `Token` to type `A`, which is a `String`.

```rust
pub type A = String;

pub fn a(_ctx: &Ctx, token: Token) -> A {
    token.value.into()
}
```

Note that `token.value` is of type `Input`, which is also defined in the action file:

```rust
pub type Input = str;
```

On the other hand, string terminals have no actions.

<!-- :arrow_right:  Next:  -->

:blue_book: Back: [Table of contents](./../README.md)
