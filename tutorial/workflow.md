# Workflow

Our workflow is presented by the flowchart below.
The workflow starts from the circle at the top.

```mermaid
flowchart TD
  O(( ))
  G(Grammar)
  P(Parser)
  A(Actions)
  M1{ }
  I(Input)
  M2{ }
  R(Result)
  O -->|Write grammar| G
  G -->|Generate parser by 'rcomp'| M1
  M1 --> P & A
  A -->|Change actions| A
  O -->|Prepare input| I
  P & A & I --> M2
  M2 -->|Parse input by 'cargo run'| R
```

:arrow_right:  Next: [Grammar File Format](./grammar_file_format.md)

:blue_book: Back: [Table of contents](./../README.md)
