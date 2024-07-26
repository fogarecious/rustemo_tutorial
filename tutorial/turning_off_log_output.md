# Turning Off Log Output

When we run our parser, we always see a long output that explains how the parser parses the given input.
This log output can be turned off.

Here is a simple grammar:

```text
S: A;

terminals

A: 'a';
```

When we run the parser that the grammar generates with input `a`, we get a long output:

```text
*** Parsing started

file: <str>
Context at 0[1,0]: '-->a'
Stack: ParseStack {
    stack: [
        State(0:AUG, 0..0 [1,0]),
    ],
}
Current state: 0:AUG
  Trying recognizers: [(A, true)]
    Recognizing A -- recognized
Token ahead: A("\"a\"" [1,0-1,1])
Shifting to state 1:A at location [1,0-1,1] with token A("\"a\"" [1,0-1,1])
Context at 1[1,1]:
a-->

  Trying recognizers: [(STOP, false)]
    Recognizing STOP -- recognized
Token ahead: STOP("\"\"" [1,1-1,1])
Stack: ParseStack {
    stack: [
        State(0:AUG, 0..0 [1,0]),
        State(1:A, 0..1 [1,0-1,1]),
    ],
}
Current state: 1:A
Reduce by production 'S: A', size 1
GOTO 0:AUG -> 2:S
  Trying recognizers: [(STOP, false)]
    Recognizing STOP -- recognized
Token ahead: STOP("\"\"" [1,1-1,1])
Stack: ParseStack {
    stack: [
        State(0:AUG, 0..0 [1,0]),
        State(2:S, 0..1 [1,0-1,1]),
    ],
}
Current state: 2:S
Accept
Ok(
    A,
)
```

This log output will only appear in the debug mode.
So, we will not see the long output in the release mode.

```sh
cargo run --release
```

The output now is:

```text
Ok(
    A,
)
```

For the debug mode, if we want to disable the log output, we can use the following command:

```sh
RUSTEMO_NOTRACE=1 cargo run
```

:arrow_right:  Next: [Generating Parsers Automatically](./generating_parsers_automatically.md)

:blue_book: Back: [Table of contents](./../README.md)
