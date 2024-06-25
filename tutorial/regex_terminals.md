# Regex Terminals

Another type of terminal definition is defined by a regular expression.

A regular expression is indicated by `/`.
The content of a regular expression is put between two `/`.
For example, `X: /\d+(\.\d*)?/;`, which represents a simple form of floating-point numbers.

For more information about how to write a regular expression, readers can refer to [the syntax of regex](https://docs.rs/regex/1.10.5/regex/#syntax).

Additionally, in the document of [Rustemo](https://github.com/igordejanovic/rustemo), it is suggested to always wrap alternative choices such as `A | B` in a pair of parentheses, i.e., `(A | B)`.

<!-- :arrow_right:  Next:  -->

:blue_book: Back: [Table of contents](./../README.md)
