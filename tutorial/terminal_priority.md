# Terminal Priority

In some rare cases, a given grammar may have two terminals that accept the same string.
And `rcomp` will greedily select the first matching terminal.
Here is an example:

```text
S: A1 | A2;

terminals

A1: /[ab]/;
A2: /[ac]/;
```

When parsing string `a` with this grammar, we can see from the output that `a` is recognized as `A1`.

```text
Accept
Ok(
  A1(
    "a",
  ),
)
```

To change the behavior of the parser, we can adjust some terminal priority.
For example, we can make `A2` to have priority `11`.

```text
S: A1 | A2;

terminals

A1: /[ab]/;
A2: /[ac]/ {11};
```

The output of parsing string `a` shows that `a` is recognized as `A2` now.

```text
Accept
Ok(
  A2(
    "a",
  ),
)
```

<!-- :arrow_right:  Next:  -->

:blue_book: Back: [Table of contents](./../README.md)
