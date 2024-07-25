# GLR Parser Generation

GLR is another way to deal with ambiguous grammars.
It parses the input in all possible ways.

Consider the grammar below:

```text
S: S Plus S
  | A
  ;

terminals

Plus: /\+/;
A: /\d+/;
```

If we use `rcomp` as usual

```rust
rcomp my_grammar.rustemo
```

we will get an error.

```text
Error: Grammar is not deterministic. There are conflicts.
Parser(s) not generated.
```

Now we make `rcomp` to generate a GLR parser.

```sh
rcomp --parser-algo glr my_grammar.rustemo
```

After running this command, it generates a parser successfully.
We can also use the shorter command below.

```sh
rcomp -p glr my_grammar.rustemo
```

However, the output of running the parser is complicated (more than 300 lines).
Let us make the output simple.
We replace `S`, `s_c1` and `s_a` in the action file with the code below.

```rust
pub type S = String;

pub fn s_c1(_ctx: &Ctx, s_1: S, plus: Plus, s_3: S) -> S {
    format!("({} {} {})", s_1, plus, s_3)
}

pub fn s_a(_ctx: &Ctx, a: A) -> S {
    a
}
```

Basically, we make a parser that adds a pair of parentheses when a partial expression is parsed.
(We can remove struct `SC1` in the action file as it is unnecessary here.)

In function `main`, we do the changes:

```rust
fn main() {
    let input = "1 + 2 + 3";
    let result = MyGrammarParser::new().parse(input);

    for tree in result.unwrap() {
      let result = tree.build(&mut DefaultBuilder::new());
      println!("{:#?}", result);
    }
}
```

The code iterates all parse trees (or iterates each possible way of parsing) and then executes our actions on each parse tree.
(Note that be sure to `use my_grammar::DefaultBuilder`.)

For input `1 + 2 + 3`, we can see from the output that there are two ways of parsing:

```text
"((1 + 2) + 3)"
"(1 + (2 + 3))"
```

:arrow_right:  Next: [Turning Off Log Output](./turning_off_log_output.md)

:blue_book: Back: [Table of contents](./../README.md)
