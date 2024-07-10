# Default Names For Terminals

Symbols in a grammar will be converted to different data types in the action file.
Let's start from terminals.

There are two types of terminals: strings and regular expressions.
String terminals will not be converted to any data types and thus cannot be found in the action file.
They are just for the parser to find the correct way to parse the input.

On the other hand, regular expression terminals will be converted to `type`.
For example:

```text
S: A;

terminals

A: /\d+/;
```

Regular expression terminal `A` is converted to a `type` of `String`.

```rust
pub type A = String;
```

There is an `fn` with the same name as the regular expression terminal but in lower case.
This `fn` is associated with the terminal and will be introduced later.

```rust
pub fn a(_ctx: &Ctx, token: Token) -> A
```

<!-- :arrow_right:  Next:  -->

:blue_book: Back: [Table of contents](./../README.md)
