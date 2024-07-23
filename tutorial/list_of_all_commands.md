# List Of All Commands

A manual of `rcomp` can be found by its option `help`.

```sh
rcomp --help
```

This command outputs the version of `rcomp` and all options that we can use.

```text
rustemo-compiler 0.6.0-
Igor R. Dejanović <igor.dejanovic@gmail.com>
Rustemo compiler and development tools

USAGE:
    rcomp [OPTIONS] <GRAMMAR FILE/DIR>

ARGS:
    <GRAMMAR FILE/DIR>    Grammar file or directory to process

OPTIONS:
    -a, --outdir-actions-root <OUT DIR ACTIONS ROOT>
            Output directory for actions. Default is the same as input grammar file

    -b, --builder-type <BUILDER_TYPE>
            Generated builder type [default: default] [possible values: default, generic, custom]

        --dot
            Create DOT automata visualization

    -e, --exclude <EXCLUDE>
            Exclude dirs containing these parts. Used with dir processing

    -f, --force
            Regenerate output actions file even if exists

        --fancy-regex
            Should fancy_regex crate be used instead of regex

    -g, --generator-table-type <GENERATOR_TABLE_TYPE>
            Parser generator table type [default: functions] [possible values: arrays, functions]

    -h, --help
            Print help information

    -i, --input-type <INPUT_TYPE>
            The type of the input if non-default lexer is used [default: str]

    -l, --lexer-type <LEXER_TYPE>
            What kind of lexer should be used [default: default] [possible values: default, custom]

        --lexical-disamb-grammar-order=<LEXICAL_DISAMB_GRAMMAR_ORDER>
            Lexical disambiguation using grammar order

        --lexical-disamb-longest-match=<LEXICAL_DISAMB_LONGEST_MATCH>
            Lexical disambiguation using longest match strategy

        --lexical-disamb-most-specific=<LEXICAL_DISAMB_MOST_SPECIFIC>
            Lexical disambiguation using most specific match strategy

    -n, --noactions
            Do not generate actions

        --no-shifts-over-empty
            Do not prefer shifts over empty reductions

        --no-skip-ws
            Should whitespace be skipped. Not used if Layout rule exists in the Grammar

        --notrace
            Do not print trace logs

    -o, --outdir-root <OUT DIR ROOT>
            Output root directory for the parser. Default is the same as input grammar file

    -p, --parser-algo <PARSER_ALGO>
            Parser algorithm [default: lr] [possible values: lr, glr]

        --partial-parse
            Parser can succeed without consuming the whole input

        --prefer-shifts
            Prefer shifts in case of possible shift/reduce conflicts

        --print-table
            Print LR table

    -t, --table-type <TABLE_TYPE>
            The type of LR table [default: lalr-pager] [possible values: lalr, lalr-pager, lalr-rn]

    -v, --verbosity
            Verbosity level 0-2

    -V, --version
            Print version information
```

A shorter option for `help` is `h`.
It outputs the same manual.

```sh
rcomp -h
```

:arrow_right:  Next: [Action File Regeneration](./action_file_regeneration.md)

:blue_book: Back: [Table of contents](./../README.md)
