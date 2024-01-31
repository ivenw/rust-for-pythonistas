# Blocks

Both in Python and in Rust, scope is a fundamentally important concept.
As will become a trend, Rust is more expressive and often easier to understand.

In Python, certain keywords like `def`, `with`, `for`, `while`, `if`, etc. that
are followed by an indended line, signify the beginning of a new scope. That
is a section of code in which newly declared variables are not accessible from
the outside.

```python
def my_func():
    # `i` is available
# `i` is no longer available
```

In Rust things are much the same, only we are not signifying scope through
indendation but through use of `{}`.
(There was something in the [Functions]() section right...).

```rust
fn my_func() {
    // `i` is available 
}
// `i` is no longer available
```

So far so good, but Rust has more up it's sleve. Rust is an expression based
language and a `{}` block is nothing else than a expression.

Seeing that expressions are used to declare a function body, we can summazie
that they can return values (aren't we clever?).
