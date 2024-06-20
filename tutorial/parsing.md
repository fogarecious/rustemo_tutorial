# Parsing

Now we combine the parser and the Cargo project, which we generate in the previous two tutorials.

First, we put the two parser files `my_grammar.rs` and `my_grammar_actions.rs` into the `src` directory in the Cargo project.

Second, in the `src/main.rs` file, we include the two parser files:

```rust
mod my_grammar;
mod my_grammar_actions;
```

Third, we declare our input string and pass it to the parser:

```rust
let input = "1 + 2 * 3 + 4";
let result = MyGrammarParser::new().parse(input);
```

We will print out the `result`.

The following is the full code:

```rust
use my_grammar::MyGrammarParser;
use rustemo::Parser;

mod my_grammar;
mod my_grammar_actions;

fn main() {
    let input = "1 + 2 * 3 + 4";
    let result = MyGrammarParser::new().parse(input);
    
    println!("{:#?}", result);
}
```

Next, we can run the program:

```sh
cargo run
```

The program outputs the progress of parsing the input.
Here is the final part of the output:

```text
Accept
Ok(
    Add(
        Add {
            left: Add(
                Add {
                    left: Number(
                        "1",
                    ),
                    right: Multiply(
                        Multiply {
                            left: Number(
                                "2",
                            ),
                            right: Number(
                                "3",
                            ),
                        },
                    ),
                },
            ),
            right: Number(
                "4",
            ),
        },
    ),
)
```

We can see that the program transforms the input to a tree structure.

By default, [Rustemo](https://github.com/igordejanovic/rustemo) parsers skip whitespaces in the input.

:arrow_right:  Next: [Changing Parser Actions](./changing_parser_actions.md)

:blue_book: Back: [Table of contents](./../README.md)
