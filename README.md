# Unofficial Tutorial Of Rustemo

[Rustemo](https://github.com/igordejanovic/rustemo) is a parser generator written in [Rust](https://www.rust-lang.org/), where a parser is able to parse some input according to a predefined grammar.
This tutorial serves as a quick start for [Rustemo](https://github.com/igordejanovic/rustemo).
We try to keep each part of the tutorial as simple as possible.

## Quick Start

* [Installation](./tutorial/installation.md)
* First Example
  * Parser Generation
  * A Project Template For Parsing
  * Parsing
  * Changing Parser Actions
* Workflow

## Grammar

* Grammar File Format
* Comments
* Terminals
  * String Terminals
  * Regex Terminals
* Grammar Rules
  * Terminals In Expressions
  * Grammar Symbols In Expressions
  * Empty String
  * Or
  * Optional
  * One Or More
  * Zero Or More
  * Separators
* Disambiguation
  * Ambiguous Grammar
  * Disambiguation By Associativity
  * Disambiguation By Priority
    * Production Priority
    * Terminal Priority
  * Preference Of Grouping
* Skipping Parts Of An Input

## Actions

* Names In The Action File
  * Names For Terminals
  * Names For Grammar Rules
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
