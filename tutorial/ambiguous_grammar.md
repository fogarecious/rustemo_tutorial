# Ambiguous Grammar

There are grammars that `rcomp` does not know how to deal with.
For example:

```text
S: S Plus S
  | A;

terminals

Plus: '+';
A: /a/;
```

If we run this grammar with `rcomp`, we will get the following error:

```text
Error: Grammar is not deterministic. There are conflicts.
Parser(s) not generated.
```

The error message says that the grammar is not deterministic, which means there are at least two ways to parse strings according to the grammar.
So, `rcomp` does not know which way should it choose.

The example is one of the ambiguous grammars.
There are other ambiguous grammars.
We will talk about how to deal with these grammars in the following tutorials.

:arrow_right:  Next: [Disambiguation By Associativity](./disambiguation_by_associativity.md)

:blue_book: Back: [Table of contents](./../README.md)
