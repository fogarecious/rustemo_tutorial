# Operator Precedence

Sometimes, our grammar may contain a few operators such as `Plus` and `Multiply` in the example below:

```text
S: S Plus S {left}
  | S Multiply S {left}
  | A
  ;

terminals

Plus: /\+/;
Multiply: /\*/;
A: /a/;
```

This grammar will parse string `a + a * a` as `(a + a) * a`, which is not what we expected.

To solve this problem, we can use production priority, which is able to to specify operator precedence.
We can make production `S Multiply S` to have higher priority, say `11`.

```text
S: S Plus S {left}
  | S Multiply S {left, 11}
  | A
  ;

terminals

Plus: /\+/;
Multiply: /\*/;
A: /a/;
```

Now string `a + a * a` is parsed as `a + (a * a)`.

<!-- :arrow_right:  Next:  -->

:blue_book: Back: [Table of contents](./../README.md)
