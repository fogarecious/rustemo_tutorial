# Parser Generation

In this example, we will use a grammar, named `my_grammar.rustemo`, with the following content:

```text
Expr: left=Expr '+' right=Expr {Add, 1, left}
  | left=Expr '*' right=Expr {Multiply, 2, left}
  | Number
;

terminals

Number: /\d+/;
Addition: '+';
Multiplication: '*';
```

We will explain the content of the grammar later.

By giving a grammar, we can generate a parser based on the grammar.
We use `rcomp`, which we have just installed in the previous tutorial, to generate the parser.

```sh
rcomp my_grammar.rustemo
```

This command outputs two files: `my_grammar.rs` and `my_grammar_actions.rs`.

* `my_grammar.rs` is the parser itself.
* `my_grammar_actions.rs` is the actions that will be performed after a successful parsing.

This parser will be called later in this example when we need to parse an input string.

:arrow_right:  Next: [A Project Template For Parsing](./a_project_template_for_parsing.md)

:blue_book: Back: [Table of contents](./../README.md)
