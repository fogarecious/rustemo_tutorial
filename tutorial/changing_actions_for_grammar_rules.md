# Changing Actions For Grammar Rules

Recall that a grammar rule may have a few productions.
To change an action when a substring is parsed as a production, we change the corresponding `fn` of the production.
For example:

```text
S: S Plus S {left}
  | A
  ;

terminals

Plus: '+';
A: /\d+/;
```

`S` has a production `A` and the corresponding action `fn` of the production is

```rust
pub fn s_a(_ctx: &Ctx, a: A) -> S {
    S::A(a)
}
```

We can add a `println!` to the `fn` such as

```rust
pub fn s_a(_ctx: &Ctx, a: A) -> S {
    println!("{a}");
    S::A(a)
}
```

By running the parser on input `1 + 2 + 3`, we can see `1`, `2` and `3` accordingly in the output.

:arrow_right:  Next: [Changing Types For Terminals](./changing_types_for_terminals.md)

:blue_book: Back: [Table of contents](./../README.md)
