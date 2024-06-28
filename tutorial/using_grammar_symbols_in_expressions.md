# Using Grammar Symbols In Expressions

The `<expression>` part of a grammar rule can also contain grammar symbols.
Here is an example saying that the grammar symbol `S` is parsed by parsing the grammar symbol `T`:

```text
S: T;
T: A;

terminals

A: 'a';
```

In a grammar rule, a grammar symbol can also be concatenated with another grammar symbol as well as a terminal.
For example:

```text
S: T T C T;
T: A B;

terminals

A: 'a';
B: 'b';
C: 'c';
```

This grammar accepts exactly the string `ababcab` with optional white spaces allowed in between.

:arrow_right:  Next: [Empty String](./empty_string.md)

:blue_book: Back: [Table of contents](./../README.md)
