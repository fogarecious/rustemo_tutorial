# Separators

There is a convenient way to parse repeated strings that are separated by a separator string, such as `,` in `a,a,a`.
This can be done by `+[]` or `*[]`.

Here is an example for `+[]`:

```text
S: A+[Comma];

terminals

A: 'a';
Comma: ',';
```

This grammar accepts the strings `a`, `a,a`, `a,a,a`, etc.

Formally, `S: A+[Comma];` is shorthand for the following grammar rules:

```text
S: A1Comma;
@vec
A1Comma: A1Comma Comma A | A;
```

We will explain `@vec` later.

For `*[]`, it has almost the same method of use.

```text
S: A*[Comma];

terminals

A: 'a';
Comma: ',';
```

This grammar accepts the empty string in addition to the accepted strings in the previous grammar.

Note that both `A` and `Comma` in `A+[Comma]` and `A*[Comma]` can not only be a terminal but also a grammar symbol.

<!-- :arrow_right:  Next:  -->

:blue_book: Back: [Table of contents](./../README.md)
