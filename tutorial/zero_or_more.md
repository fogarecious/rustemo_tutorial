# Zero Or More

Another operator for repetition is `*`.
Here is an example:

```text
S: A*;

terminals

A: 'a';
```

This grammar accepts a sequence of `a` as well as *the empty string*.

Formally, `S: A*;` is shorthand for the following grammar rules:

```text
S: A0;
@vec
A0: A1 {nops} | EMPTY;
@vec
A1: A1 A | A;
```

We will explain `@vec` later.

Additionally, `nops` disables a greedy strategy that is applied by `rcomp`.
But since the strategy is disable by default, adding `nops` or not does not make any differences in this tutorial.

:arrow_right:  Next: [Separators](./separators.md)

:blue_book: Back: [Table of contents](./../README.md)
