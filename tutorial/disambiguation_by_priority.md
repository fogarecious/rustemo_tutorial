# Disambiguation By Priority

Another type of ambiguous grammar looks like this:

```text
S: A S
  | A S B
  | EMPTY
  ;

terminals

A: /a/;
B: /b/;
```

By running `rcomp` with this grammar, we also get the error: `Grammar is not deterministic.`
This is because the two productions `A S` and `A S B` are so similar that `rcomp` cannot distinguish them and thus cannot decide which one should be used.

To solve this problem, we can give every production a priority.
In [Rustemo](https://github.com/igordejanovic/rustemo), the default priority for a production is `10`.
So, any priorities larger than `10` tell `rcomp` to consider using that production first.

The priority number should be put in a pair of braces at the end of a production.
In the example, we can change the priority of production `A S B` to `11` as presented below:

```text
S: A S
  | A S B {11}
  | EMPTY
  ;

terminals

A: /a/;
B: /b/;
```

This makes `rcomp` to give preference to `A S B` (instead of `A S`).
The string `a a b` is parsed as `a (a b)`, which can be seen from the following output:

```text
Accept
Ok(
  Some(
    C1(
      SC1 {
        a: "a",
        s: Some(
          C2(
            SC2 {
              a: "a",
              s: None,
              b: "b",
            },
          ),
        ),
      },
    ),
  ),
)
```

:arrow_right:  Next: [Operator Precedence](./operator_precedence.md)

:blue_book: Back: [Table of contents](./../README.md)
