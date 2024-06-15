# Unofficial Tutorial Of Rustemo

[Rustemo](https://github.com/igordejanovic/rustemo) is a parser generator written in [Rust](https://www.rust-lang.org/), where a parser is able to parse some input according to a predefined grammar.
This tutorial serves as a quick start for [Rustemo](https://github.com/igordejanovic/rustemo).
We try to keep each part of the tutorial as simple as possible.

## Quick Start

* Installation
  <!-- cargo install rustemo-compiler -->
  <!-- executable rcomp, in ~/.cargo -->
* First Example
  * Parser Generation
    <!-- use my grammar (should not modify later) -->
    <!-- my_grammar.rustemo, including left= and right= -->
    <!-- generate parser by rcomp -->
    <!-- rcomp my_grammar.rustemo -->
    <!-- my_grammar.rs, the parser -->
    <!-- my_grammar_actions.rs, the actions performed after successfully parsing -->
  * A Project Template For Parsing
    <!-- create project -->
    <!-- cargo new my_project -->
    <!-- project dependencies -->
    <!-- cd my_project -->
    <!-- cargo add rustemo -->
    <!-- cargo add regex --no-default-features --features std,unicode-perl -->
    <!-- cargo add once_cell -->
    <!-- cargo add colored -->
    <!-- toml -->
  * Parsing
    <!-- put files in src -->
    <!-- my_grammar.rs and my_grammar_actions.rs to ./src/ -->
    <!-- include files by mod -->
    <!-- mod my_grammar; -->
    <!-- mod my_grammar_actions; -->
    <!-- input string -->
    <!-- let input = "1 + 2 * 3 * 4 + 5"; -->
    <!-- let result = MyGrammarParser::new().parse(input); -->
    <!-- println!("{:#?}", result); -->
    <!-- run parser -->
    <!-- cargo run -->
  * Changing Parser Actions
    <!-- use my_grammar_actions.rs -->
    <!-- run parser -->
    <!-- cargo run -->
* Workflow
  <!-- flowchart, mermaid -->
  <!-- write grammar->, grammar -->
  <!-- (grammar), generate parser->, parser, actions -->
  <!-- (actions), change actions->, actions -->
  <!-- prepare input->, input -->
  <!-- (parser, actions, input), parse->, result -->

## Grammar

* Grammar File Format
  <!-- the whole grammar mentioned below -->
  <!-- grammar rules, the keyword `terminals`, terminal definitions -->
  <!-- grammar rules -->
    <!-- <grammar_symbol>: <expression> ; -->
    <!-- expression explains, how to parse grammar_symbol -->
    <!-- example, NegativeNumber: MinusSign Number, parsing NegativeNumber, parse MinusSign and then parse Number -->
  <!-- the keyword `terminals` -->
    <!-- `terminals` -->
  <!-- terminal definitions -->
    <!-- <terminal_name>: <string_or_regex> ; -->
    <!-- how to parse terminal_name -->
    <!-- example, MinusSign: '-' -->
  <!-- grammar rules and terminal definitions are similar but different -->
  <!-- terminal definitions can have string and regex on its right hand side -->
  <!-- grammar rules need grammar symbols or terminal names on its right hand side -->
  <!-- skip whitespace in grammar file -->
* Comments
  <!-- use // or /* */ -->
  <!-- example -->
  <!-- /* */, the grammar parses 'a' -->
  <!-- S: A, // a grammar rule says that S is parsed by parsing A -->
  <!-- terminals -->
  <!-- A: 'a', // the terminal A is parsed by parsing 'a' -->
* Terminals
  * String Terminals
    <!-- parse terminal by string -->
    <!-- define string by ' or " -->
    <!-- example, X: 'a', Y: 'abc123', Z: "abc.com" -->
    <!-- escape character \' \" \\ -->
    <!-- example, '\'' -->
  * Regex Terminals
    <!-- inside / / -->
    <!-- example, /\d+(\.\d*)?/, simple floating-point number -->
    <!-- give ref -->
    <!-- https://docs.rs/regex/1.10.5/regex/#syntax -->
    <!-- suggest, always wrap alternative choices in parentheses, (A | B) -->
* Grammar Rules
  * Terminals In Expressions
    <!-- expression of grammar rules can contain terminals -->
    <!-- example, S: A; terminals, A: 'a'; -->
    <!-- or S: 'a'; terminals, A: 'a'; for better readability -->
    <!-- concatenation, example, S: A B C; terminals, A: 'a'; B: 'b'; C: 'c'; -->
  * Grammar Symbols In Expressions
    <!-- expression of grammar rules can also contain grammar symbols -->
    <!-- example, S: T; T: A; terminals, A: 'a'; -->
    <!-- another example, S: T T C T, T: A B, terminals, A: 'a', B: 'b', C: 'c', ababcab -->
  * Empty String
    <!-- EMPTY -->
    <!-- example, S: EMPTY; terminals -->
    <!-- only accept empty string -->
  * Or
    <!-- | -->
    <!-- example, S: A | B; terminals, A: 'a'; B: 'b' -->
    <!-- 'a' or 'b' -->
  * Optional
    <!-- ? -->
    <!-- example, S: A?; terminals, A: 'a'; -->
    <!-- 'a' or empty string -->
    <!--
      S: AOpt;
      AOpt: A | EMPTY;
    -->
  * One Or More
    <!-- + -->
    <!-- example, S: A+; terminals, A: 'a'; -->
    <!-- a sequence of 'a' and at least one `a` -->
    <!--
      S: A1;
      @vec
      A1: A1 A | A;
    -->
    <!-- @vec later -->
  * Zero Or More
    <!-- * -->
    <!-- example, S: A*; terminals, A: 'a'; -->
    <!-- a sequence of 'a' and can be empty -->
    <!--
      S: A0;
      @vec
      A0: A1 {nops} | EMPTY;
      @vec
      A1: A1 A | A;
    -->
    <!-- @vec, nops later -->
  * Separators
    <!-- +[] or *[] -->
    <!-- example, S: A+[Comma]; terminals, A: 'a'; Comma: ','; -->
    <!-- 'a', 'a,a', 'a,a,a', ... -->
    <!-- * example, S: A*[Comma]; terminals, A: 'a'; Comma: ','; -->
    <!-- also empty string -->
    <!--
      S: A1Comma;
      @vec
      A1Comma: A1Comma Comma A | A;
    -->
    <!-- @vec later -->
* Disambiguation
  * Ambiguous Grammar
    <!-- a + b + c -->
  * Disambiguation By Associativity
    <!-- left, right -->
  * Disambiguation By Priority
    <!-- default priority, 10 -->
  * Preference Of Grouping
    <!-- global shift preference control, nops, nopse -->
    <!-- if if else, if (if else) or if (if) else -->
* Skipping Parts Of An Input
  <!-- ? skip whitespaces by default -->
  <!-- the special symbol Layout -->

## Actions

* Names In The Action File
  <!-- name in grammar, name in action file (and where is it) -->
  * Names For Terminals
  * Names For Grammar Rules
* Default Actions
  * Default Actions For Terminals
  * Default Actions For Grammar Rules
* Custom Actions
  * Changing Actions
    <!-- where is the fn -->
    * Changing Actions For Terminals
    * Changing Actions For Grammar Rules
  * Changing Types
    <!-- type, and return value in fn -->
    * Changing Types For Terminals
    * Changing Types For Grammar Rules
    * Using Vec As Types
      <!-- @vec -->
      <!-- for grammar rules created by ourselves -->
      <!-- build-in grammar rules use @vec automatically -->
  * Changing Enum Value Names
    <!-- by {} in each derivation (grammar rule) -->
    <!-- production kind -->
  * Changing Names Of Struct Fields And Function Parameters
    <!-- Named matches, in grammar, = -->

<!-- Context -->
<!-- custom lexer, see Lexers -->
  <!-- use the VarInts grammar -->
  <!--
    rcomp --lexer-type custom my_gram.rustemo
        without --lexer-type custom, error
  -->
  <!-- it seems TokenKind and State are from my_gram.rs -->
  <!-- result = MyParser::new(MyLexer::new()).parse(&bytes); -->
<!-- glr -->

## See Also

* [Rustemo](https://github.com/igordejanovic/rustemo) - the parser generator.
* [Rustemo Book](https://www.igordejanovic.net/rustemo/) - a detailed description of Rustemo.

## Contributions

Pull requests for typos, incorrect information, or other ideas are welcome!

## License

All code in the tutorial is provided under the MIT License.
