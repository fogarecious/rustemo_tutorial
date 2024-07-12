# Default Names For Grammar Rules

Each grammar rule is converted to an `enum`.
For example:

```text
S: T | B;
T: A;

terminals

A: 'a';
B: 'b';
```

For grammar symbol `S` and `T`, we have their corresponding `enum`s in the action file.

```rust
pub enum S {
    T(T),
    B,
}

pub enum T {
    A,
}
```

Each production appears as a variant in `enum`.
For grammar rule starting with `S`, which has two productions `T` and `B`, we can see that the corresponding variants of `enum S` are `S::T(T)` and `S::B`.

If a production is too complicated (say, containing many grammar symbols), `rcomp` will create a new struct for it.
For example:

```text
S: X Y | Y Z;
X: A A;
Y: B B;
Z: A B;

terminals

A: 'a';
B: 'b';
```

Productions `X Y` and `Y Z` are converted to structs `SC1` and `SC2`.

```rust
pub enum S {
    C1(SC1),
    C2(SC2),
}

pub struct SC1 {
    pub x: X,
    pub y: Y,
}

pub struct SC2 {
    pub y: Y,
    pub z: Z,
}
```

Each production also has an `fn` with name `<grammar_symbol>_<variant_name>`.

```rust
pub fn s_c1(_ctx: &Ctx, x: X, y: Y) -> S { /* ... */ }
pub fn s_c2(_ctx: &Ctx, y: Y, z: Z) -> S { /* ... */ }
```

:arrow_right:  Next: [Default Actions For Terminals](./default_actions_for_terminals.md)

:blue_book: Back: [Table of contents](./../README.md)
