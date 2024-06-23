# Comments

Comments are texts in the grammar file that are skipped by `rcomp`.

To write a comment, we use `//` or `/* */`:

* `//` is a single-line comment.
It starts from `//` and ends with a line break.
* `/* */` is a multiple-line comment.
It starts from `/*` and ends with `*/`.

Here is an example:

```text
/*
  This grammar parses the string 'a' only.
*/

S: A; // a grammar rule says that S is parsed by parsing A

terminals

A: 'a'; // the terminal A is parsed by parsing 'a'
```

<!-- :arrow_right:  Next:  -->

:blue_book: Back: [Table of contents](./../README.md)
