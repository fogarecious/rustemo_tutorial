# One Or More

Sometimes, we want to parse a string repeatedly.
In this case, we can use operator `+`.
For example:

```text
S: A+;

terminals

A: 'a';
```

This grammar accepts a sequence of `a` and at least one `a` (optional white spaces are allowed).

Formally, `S: A+;` is shorthand for the following grammar rules:

```text
S: A1;
@vec
A1: A1 A | A;
```

We will explain `@vec` later.

:arrow_right:  Next: [Zero Or More](./zero_or_more.md)

:blue_book: Back: [Table of contents](./../README.md)
