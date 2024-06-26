# Unofficial Tutorial Of Rustemo

[Rustemo](https://github.com/igordejanovic/rustemo) is a parser generator written in [Rust](https://www.rust-lang.org/), where a parser is able to parse some input according to a predefined grammar.
This tutorial serves as a quick start for [Rustemo](https://github.com/igordejanovic/rustemo).
We try to keep each part of the tutorial as simple as possible.

## Quick Start

* [Installation](./tutorial/installation.md)
* First Example
  * [Parser Generation](./tutorial/parser_generation.md)
  * [A Project Template For Parsing](./tutorial/a_project_template_for_parsing.md)
  * [Parsing](./tutorial/parsing.md)
  * [Changing Parser Actions](./tutorial/changing_parser_actions.md)
* [Workflow](./tutorial/workflow.md)

## Grammar

* [Grammar File Format](./tutorial/grammar_file_format.md)
* [Comments](./tutorial/comments.md)
* Terminals
  * [String Terminals](./tutorial/string_terminals.md)
  * [Regex Terminals](./tutorial/regex_terminals.md)
* Grammar Rules
  * [Using Terminals In Expressions](./tutorial/using_terminals_in_expressions.md)
  * [Using Grammar Symbols In Expressions](./tutorial/using_grammar_symbols_in_expressions.md)
  * [Empty String](./tutorial/empty_string.md)
  * [Or](./tutorial/or.md)
  * [Optional](./tutorial/optional.md)
  * [One Or More](./tutorial/one_or_more.md)
  * Zero Or More
  * Separators
* Disambiguation
  * Ambiguous Grammar
  * Disambiguation By Associativity
  * Disambiguation By Priority
    <!-- Production Priority -->
* More About Priority
  * Operator Precedence
  * Terminal Priority
* Skipping Parts Of Input

## Actions

* Names In The Action File
  * Default Names For Terminals
  * Default Names For Grammar Rules
* Default Actions
  * Default Actions For Terminals
  * Default Actions For Grammar Rules
* Custom Actions
  * Changing Actions
    * Changing Actions For Terminals
    * Changing Actions For Grammar Rules
  * Changing Types
    * Changing Types For Terminals
    * Changing Types For Grammar Rules
    * Using Vec As Types
  * Changing Enum Value Names
  * Changing Names Of Struct Fields And Function Parameters

## See Also

* [Rustemo](https://github.com/igordejanovic/rustemo) - the parser generator.
* [Rustemo Book](https://www.igordejanovic.net/rustemo/) - a detailed description of Rustemo.

## Contributions

Pull requests for typos, incorrect information, or other ideas are welcome!

## License

All code in the tutorial is provided under the MIT License.
