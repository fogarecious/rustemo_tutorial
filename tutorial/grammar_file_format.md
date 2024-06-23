# Grammar File Format

A grammar file consists of three parts: some grammar rules, the keyword `terminals`, and some terminal definitions.
For example, the following is a valid grammar.

```text
NegativeNumber: MinusSign Number;

terminals

MinusSign: '-';
Number: /\d+/;
```

The format of these three parts are explained below:

* Grammar rules

  ```text
  <grammar_symbol>: <expression> ;
  ```

  The `<expression>` explains how to parse the corresponding `<grammar_symbol>`.
  Consider the following example.
  
  ```text
  NegativeNumber: MinusSign Number;
  ```

  The example means: parsing `NegativeNumber` is done by parsing `MinusSign` and then parsing `Number`.

* The keyword `terminals`

  ```text
  terminals
  ```

  This is just a line containing a word `terminals`.

* Terminal definitions

  ```text
  <terminal_name>: <string_or_regex> ;
  ```

  This line describes how to parse `<terminal_name>`.
  The part on the right can be a string or a regular expression.
  The following is two examples of terminal definitions.

  ```text
  MinusSign: '-';
  Number: /\d+/;
  ```

Grammar rules and terminal definitions are similar but the right parts of them are different.
Terminal definitions accept a string or a regular expression on its right, whereas grammar rules accept grammar symbols or terminal names on its right.
Since grammar rules accept terminal names on its right, its description capability is more powerful than that of terminal definitions.

The detail about grammar rules and terminal definitions will be explained later.

The white spaces in the grammar file is skipped by `rcomp`.

:arrow_right:  Next: [Comments](./comments.md)

:blue_book: Back: [Table of contents](./../README.md)
