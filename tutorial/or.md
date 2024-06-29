# Or

There is an operator `|` for alternatives in a grammar rule.
For example:

```text
S: A | B;

terminals

A: 'a';
B: 'b';
```

This grammar accepts two strings: `a` and `b`.
The grammar rule `S: A | B;` means `S` can be parsed by parsing `A` or by parsing `B`.

Each operand of alternatives is called a *production*.
In the grammar rule `S: A | B;`, there are two productions.
One is `A` and the other is `B`.

For a grammar rule that has no operators of alternatives, the grammar rule has only one production.

<!-- :arrow_right:  Next:  -->

:blue_book: Back: [Table of contents](./../README.md)
