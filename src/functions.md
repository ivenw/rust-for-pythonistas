# Functions

Keeping with tradition, we are starting with `Hello, world`!
No, I changed my mind. We won't. Let's hold on to `Hello, world!` for
just a moment. Let's start with another classic, the `add` function
and how to call it.

In Rust:
```rust
fn main() {
    add(1, 1);
}

fn add(a: &i32, b: &i32) -> i32 {
    a + b
}
```

And in Python:
```python
def add(a: int, b: int) -> int:
    return a + b

def main():
    add(1, 1)

if __name__ == "__main__":
    main()
```

The similarities are, so far, uncanny! But we should make note of the following:
- We define a function with `fn`.
- Instead of through intendation, a function body is declared through use of `{}`
- The `main` function is defined before the `add` function. The Rust compiler
would have actually been perfectly happy if we followed Python rules here, but it is
often seen as idiomatic to start with the highest degree of abstraction at the top
of the file. (It does make sense. I am a big fan.)
- The `main` function has special meaning in Rust, whereas in Python we have to
perform the go' ol' if-name-main-dance.
- There is no `return` statement in the Rust function. We shall learn more about
this in the [blocks]() section.
- A semicolon

Ok, back to `Hello, world!`. Every new rust project initialized with `cargo new` or `cargo init`,
contains a `src/main.rs` file with the following contents:

```rust
fn main() {
    println!("Hello, world!")
}
```

In Python the equivalent would of course be:

```python
def main() -> None:
    print("Hello, world!")
```

What is that? There is an exclamation point behind the `println!` "function".
This certainly seems odd.

In fact, `println` is *not* a function, but a `macro`. Macros are a part of the Rust
language often kept to the very end of the curriculum; that is how to write them.
But then why do we encounter them already in the most basic of examples? 

Consider that in Python the print function could also have been given the input
as follows, producing the same output:

```python
print("Hello", ",", " ", "world", "!")
```

This is possible because in Python we can declare a function to take `*args` as input,
so that the function can run over an arbitrary number of arguments (a *variadic* function).
In Rust writing these type of functions is not possible. For the Rust compiler to perform
it's memory safety "magic", it needs to know exactly how many arguments a function takes.

The macro system provides a solution to this conundrum by providing us with a way to
write code *that writes code*. Metaprogramming. *At compiletime*, the `println!` macro
declares a function that takes *exactly* the number of arguments that we provided to
the macro.
