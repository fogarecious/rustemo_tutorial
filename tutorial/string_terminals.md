# String Terminals

There are two terminal definitions.
The first one is to define a terminal by a string.

A string is indicated by `'` or `"`.
The content of a string is put between two `'` or two `"`.
Here are some examples:

```text
X: 'a';
Y: 'abc123';
Z: "abc.com";
```

When parsing a terminal, the corresponding string content is parsed, which means the string content should be consumed in the input.

If there are `'` or `"` in a string, they needs to be replaced with `\'` or `\"` respectively.
For example, `'\''` represents a single `'`.

Similarly, if there is `\` intentionally in a string, it also needs to be replaced with `\\`.

:arrow_right:  Next: [Regex Terminals](./regex_terminals.md)

:blue_book: Back: [Table of contents](./../README.md)
