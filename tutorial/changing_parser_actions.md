# Changing Parser Actions

Currently, our program outputs a tree structure after a successful parsing.
We can change this behavior.

To change the behavior of a successful parsing, we need to modify the `my_grammar_actions.rs` file.
For example, we can replace the content of `my_grammar_actions.rs` with the following code:

```rust
use super::my_grammar::{Context, TokenKind};
/// This file is maintained by rustemo but can be modified manually.
/// All manual changes will be preserved except non-doc comments.
use rustemo::Token as RustemoToken;
pub type Input = str;
pub type Ctx<'i> = Context<'i, Input>;
#[allow(dead_code)]
pub type Token<'i> = RustemoToken<'i, Input, TokenKind>;

pub type Number = u32;
pub fn number(_ctx: &Ctx, token: Token) -> Number {
    token.value.parse().unwrap()
}

pub type Expr = u32;
pub fn expr_add(_ctx: &Ctx, left: Expr, right: Expr) -> Expr {
    left + right
}
pub fn expr_multiply(_ctx: &Ctx, left: Expr, right: Expr) -> Expr {
    left * right
}
pub fn expr_number(_ctx: &Ctx, number: Number) -> Expr {
    number
}
```

This code will perform a real calculation based on the input expression.
Let us run the program.

```sh
cargo run
```

The final part of the output is:

```text
Accept
Ok(
    11,
)
```

The output shows `11`, which corresponds to the input `1 + 2 * 3 + 4`.

:arrow_right:  Next: [Workflow](./workflow.md)

:blue_book: Back: [Table of contents](./../README.md)
