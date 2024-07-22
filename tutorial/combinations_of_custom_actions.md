# Combinations of Custom Actions

In this tutorial, we do an exercise using the previous tutorials.
Given a simple expression, our goal is to add parentheses that specify precedences to the expression.
For example, given `1 + 2 * 3 + 4`, we would like the program to output `((1 + (2 * 3)) + 4)`.

We consider the grammar below:

```text
S: left=S Plus right=S {Add, left}
  | left=S Times right=S {Mul, left, 11}
  | A
  ;

terminals

Plus: /\+/;
Times: /\*/;
A: /\d+/;
```

This grammar is able to parse the simple expressions that we target at.
The default action file of the grammar looks like this:

```rust
pub type A = String;
pub type Plus = String;
pub type Times = String;

pub enum S {
    Add(Add),
    Mul(Mul),
    A(A),
}

pub struct Add {
    pub left: Box<S>,
    pub plus: Plus,
    pub right: Box<S>,
}

pub struct Mul {
    pub left: Box<S>,
    pub times: Times,
    pub right: Box<S>,
}

pub fn s_add(_ctx: &Ctx, left: S, plus: Plus, right: S) -> S {
    S::Add(Add {
        left: Box::new(left),
        plus,
        right: Box::new(right),
    })
}

pub fn s_mul(_ctx: &Ctx, left: S, times: Times, right: S) -> S {
    S::Mul(Mul {
        left: Box::new(left),
        times,
        right: Box::new(right),
    })
}

pub fn s_a(_ctx: &Ctx, a: A) -> S {
    S::A(a)
}
```

We change the action file in the following way.

```rust
pub type S = String;

pub fn s_add(_ctx: &Ctx, left: S, plus: Plus, right: S) -> S {
    format!("({} {} {})", left, plus, right)
}

pub fn s_mul(_ctx: &Ctx, left: S, times: Times, right: S) -> S {
    format!("({} {} {})", left, times, right)
}

pub fn s_a(_ctx: &Ctx, a: A) -> S {
    a
}
```

We also remove struct `Add` and `Mul`.

Now, we can test input `1 + 2 * 3 + 4` (in `main`).

```rust
let input = "1 + 2 * 3 + 4";
```

The output is:

```text
((1 + (2 * 3)) + 4)
```

:arrow_right:  Next: [List Of All Commands](./list_of_all_commands.md)

:blue_book: Back: [Table of contents](./../README.md)
