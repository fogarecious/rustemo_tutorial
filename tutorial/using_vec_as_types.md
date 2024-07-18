# Using Vec As Types

Consider the grammar below:

```text
S: S A | A;

terminals

A: /\d/;
```

By default, `S` is converted to `enum` possibly together with other `struct`s (such  as `SC1` below).

```rust
pub enum S {
    C1(SC1),
    A(A),
}

pub struct SC1 {
    pub s: Box<S>,
    pub a: A,
}
```

However, we know that this grammar accepts a sequence of `A`.
It would be more readable for the action file to represent `S` as an array of `A`.
In this case, we can precede grammar rule `S` with symbol `@vec`.

```rust
@vec
S: S A | A;

terminals

A: /\d/;
```

This changes the type of `S` to `Vec<A>` in the action file.

```rust
pub type S = Vec<A>;
```

Operators `*` and `+` implicitly add `@vec` to the grammar rules they are in.

<!-- :arrow_right:  Next:  -->

:blue_book: Back: [Table of contents](./../README.md)
