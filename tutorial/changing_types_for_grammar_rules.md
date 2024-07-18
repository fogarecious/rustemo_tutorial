# Changing Types For Grammar Rules

We can also change the types of grammar rules and their productions.
For example:

```text
S: T Plus A
  | A
  ;
T: A;

terminals

Plus: '+';
A: /\d+/;
```

Grammar rule `S` and its two productions are converted in the action file to:

```rust
pub enum S {
    C1(SC1),
    A(A),
}

pub struct SC1 {
    pub t: T,
    pub a: A,
}

pub type T = A;
```

And terminal `A` is converted to:

```rust
pub type A = String;
```

We can change all these types to `u32` (and remove `SC1`, which is unnecessary).

```rust
pub type A = u32;

pub type S = u32;
pub type T = u32;
```

Now we can compute the sum of the two input numbers.

```rust
// for terminal A
pub fn a(_ctx: &Ctx, token: Token) -> A {
    token.value.parse().unwrap()
}

// for production T: A
pub fn t_a(_ctx: &Ctx, a: A) -> T {
    a
}

// for production S: A
pub fn s_a(_ctx: &Ctx, a: A) -> S {
    a
}

// for production S: T Plus A
pub fn s_c1(_ctx: &Ctx, t: T, a: A) -> S {
    t + a
}
```

By passing input `1 + 2` (in `main`), we get the expected output.

```text
Accept
Ok(
  3,
)
```

:arrow_right:  Next: [Using Vec As Types](./using_vec_as_types.md)

:blue_book: Back: [Table of contents](./../README.md)
