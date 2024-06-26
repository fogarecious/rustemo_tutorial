# Using Terminals In Expressions

The `<expression>` part of a grammar rule can contain terminals.
For example:

```text
S: A;

terminals

A: 'a';
```

This grammar accepts exactly the string `a`.

Alternatively, this grammar can also be written as the grammar below, where we replace `A` with `'a'` in the grammar rule:

```text
S: 'a';

terminals

A: 'a';
```

In general, we can replace a terminal name with its content in any grammar rules.
The new grammar is equivalent to the old one.
It would have better readabilities especially for long grammar files.

Multiple terminals can be concatenated in a grammar rule such as the grammar below:

```text
S: A B C;

terminals

A: 'a';
B: 'b';
C: 'c';
```

This grammar accepts exactly the string `abc` with optional white spaces allowed in between.

<!-- :arrow_right:  Next:  -->

:blue_book: Back: [Table of contents](./../README.md)
