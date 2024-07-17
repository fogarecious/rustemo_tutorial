# Changing Types For Terminals

The default type of a regular expression terminal is `String`.
We can change this type to any other types that we want.
For example:

```text
S: A;

terminals

A: /\d+/;
```

Terminal `A` is converted to a `type` and an `fn` in the action file.

```rust
pub type A = String;

pub fn a(_ctx: &Ctx, token: Token) -> A {
    token.value.into()
}
```

We can change `type A` from `String` to `u32` and parse it in the `fn`.

```rust
pub type A = u32;

pub fn a(_ctx: &Ctx, token: Token) -> A {
    token.value.parse().unwrap()
}
```

By passing `"123"` to the input (in `main`):

```rust
let input = "123";
```

We should see from the output that the input is recognized as integer `123`.

```text
Accept
Ok(
  123,
)
```

There is no type modifications we can do to string terminals.

:arrow_right:  Next: [Changing Types For Grammar Rules](./changing_types_for_grammar_rules.md)

:blue_book: Back: [Table of contents](./../README.md)
