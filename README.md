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
  * [Zero Or More](./tutorial/zero_or_more.md)
  * [Separators](./tutorial/separators.md)
* Disambiguation
  * [Ambiguous Grammar](./tutorial/ambiguous_grammar.md)
  * [Disambiguation By Associativity](./tutorial/disambiguation_by_associativity.md)
  * [Disambiguation By Priority](./tutorial/disambiguation_by_priority.md)
* More About Priority
  * [Operator Precedence](./tutorial/operator_precedence.md)
  * [Terminal Priority](./tutorial/terminal_priority.md)
* [Skipping Parts Of Input](./tutorial/skipping_parts_of_input.md)

## Actions

* Names In The Action File
  * [Default Names For Terminals](./tutorial/default_names_for_terminals.md)
  * [Default Names For Grammar Rules](./tutorial/default_names_for_grammar_rules.md)
* Default Actions
  * [Default Actions For Terminals](./tutorial/default_actions_for_terminals.md)
  * [Default Actions For Grammar Rules](./tutorial/default_actions_for_grammar_rules.md)
* Custom Actions
  * Changing Actions
    * [Changing Actions For Terminals](./tutorial/changing_actions_for_terminals.md)
    * [Changing Actions For Grammar Rules](./tutorial/changing_actions_for_grammar_rules.md)
  * Changing Types
    * [Changing Types For Terminals](./tutorial/changing_types_for_terminals.md)
    * [Changing Types For Grammar Rules](./tutorial/changing_types_for_grammar_rules.md)
    * [Using Vec As Types](./tutorial/using_vec_as_types.md)
  * [Changing Names Of Enum Variants And Functions](./tutorial/changing_names_of_enum_variants_and_functions.md)
  * Changing Names Of Struct Fields And Function Parameters
  * Combinations of Custom Actions

## Rcomp

* List Of All Commands
* Action File Regeneration
* GLR Parser Generation

## See Also

* [Rustemo](https://github.com/igordejanovic/rustemo) - the parser generator.
* [Rustemo Book](https://www.igordejanovic.net/rustemo/) - a detailed description of Rustemo.

## Contributions

Pull requests for typos, incorrect information, or other ideas are welcome!

## License

All code in the tutorial is provided under the MIT License.
