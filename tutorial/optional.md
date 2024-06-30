# Optional

There is a special alternative symbol `?`, which allows a grammar to parse a string optionally.
For example:

```text
S: A?;

terminals

A: 'a';
```

This grammar accepts both `a` and the empty string.

Formally, `S: A?;` is shorthand for the following grammar rules:

```text
S: AOpt;
AOpt: A | EMPTY;
```

<!-- :arrow_right:  Next:  -->

:blue_book: Back: [Table of contents](./../README.md)
