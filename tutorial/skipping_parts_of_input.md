# Skipping Parts Of Input

By default, the generated parser skips white spaces.
For example, consider the grammar below:

```text
S: A+;

terminals

A: /a/;
```

This grammar accepts string `a a a` even if there are white spaces among `a`'s.

We can change this behavior by the special grammar symbol `Layout`.
For example, we can disable accepting white spaces by `Layout: EMPTY;`, as described below:

```text
S: A+;
Layout: EMPTY;

terminals

A: /a/;
```

Now, `a a a` is not acceptable.

This feature is for parts like comments that are not important in the input string and can be skipped.
We can specify how to parse these comments by adding a grammar rule with grammar symbol `Layout`.
The string parsed by `Layout` will be skipped automatically and will not be shown in the output.

<!-- :arrow_right:  Next:  -->

:blue_book: Back: [Table of contents](./../README.md)
