**## Docstrings
```rust
/// this is a doc string
/// # arguments
/// * `name` - explanation
```

## Futures
https://cfsamson.github.io/books-futures-explained/1_futures_in_rust.html

## Typedef
```rust
type AudioBuf = [i16; 1024];
```

# slices
A region of an array or vector `[T]`. 

Reference to slice is "fat pointer", has pointer to address and number of elements 

# str vs String vs &str
`str` is a string literally. Allocated onto stack
&str alternatively `&[u8]` - a reference to a series of elements 
String is `Vec<u8>` - allocated on heap

`.to_string()` or `.to_owned()` takes string literals and outputs String

# mem::replace
Can use to move a value out that was allocated in an array as long as you replace it with something else 

# Copy vs Clone
Copy is a bit for bit duplicate of whatever it is. 

If any kind of special handling is required for a value when it is dropped, it cannot be a copy type. Structs and enums are not copy by default. If all fields of a struct and enums are copyable, then the struct can be too.

# `RC<T>`
Creates a pointer to a heap allocated T with a reference count associated. When you clone the Rc, it creates a new pointer to the same memory block.

Rc doesn't not allow direct mutability. Read only
You can accidentally leak memory if two Rc's point to one another, which would result in the count to never go to 0 (but this is hard to do). You can use `std::rc::weak` to deal with this issue
Pg 98

# Lifetime rules
![[Lifetime diagram rust]]
- A function's signature indicates everything regarding the lifetime of its variables.
ex: `g<'a>(p: &'a i32)'` indicates that it does not "stash" `p` anywhere that will outlive the call

# Error handling
## err.source()
Returns the underlying error that caused err

## all available information for the error
```rust
use std::error::Error;
use std::io::{Write, stderr}

/// Dump an error to stderr
/// If another error happens while building the error message or writing to stderr, it is ignoted
fn print_error(mut err: &dyn Error) {
    let _ = writeln!(stderr(), "error: {}", err);
    while let Some(source) = err.source() {
        let _ = writeln!(stderr(), "caused by: {}", source);
        err = source;
    }
}
```

## Question mark operator
Propagates the error. Is equivalent to something like this 
```rust
let weather = match get_weather() {
    Ok(success_val) => success_val,
    Err(err) => return Err(err)
}
```

## Multiple error types
Page 166
- end up losing information when down casting the error to a generic one 

## Error crates
`thiserror`

# Crates
## Modules
pub(crate) makes a function available everywhere in the crate but not externally
pub(super) makes item visible to parent module and descendents
`pub(in <path>)` for making public to specific module pg 180

You can declare a module folder by creating `mod.rs` and inside it declaring each file in it as part of the module. Alternatively, you can not use a mod.rs file and use a new file with the same name as the folder (but not in the folder) for the same purposes as mod.rs . Page 182

If you declare `mod <filename>;` rust checks that filename.rs exists 

## Imports
Paths are relative to the current module
The current module can be referred to as `self`
The parent module can be referred to as `super`
`crate` refers to the crate containing the current module 
If you have conflicting imports with a crate you are using and a local module, you can refer to the crate absolutely by prefixing with `::<crate name>`. To refer to the local module, prefix with `self::`

### Preludes
Are meant to be imported via *

# statics and constants
Constants are compiled into your code everywhere it is used. Use for magic numbers and strings

A static variable is setup before a program runs and lasts until it exits 

# Attributes
## crate/file wide attributes
At the top of main.rs or lib.rs, use `#![]` instead of `#[]`. This is sometimes used to enable unstable rust features.

Can actually use this to document a module or a crate with `//!`

## `#[inline]`
This is a suggestion to take the body of the function and insert it directly. There are some specific settings that you can use to force it
Pg 193

## allow
Rust doesn't try to prove that something will panic and will let it happen (page 194)

# Macros
## assert!
Assert is compiled into a release build, unless you use debug_assert!

# Test
## `Result<(), E>`
Can be returned from unit tests 
## Module for testing
`#[cfg(test)]` above a module only includes it while testing. 


# Documentation
Main command `cargo doc`
`--no-deps` only generate for current project
`--open` opens docs in browser

`///` are actual equiv to doc attributes `#[doc = ""]`

Markdown is used in doc comments. For links can use rust paths instead of file paths it exits 

# Pattern matching
## [ref keyword](https://doc.rust-lang.org/std/keyword.ref.html)
`ref n`  borrows `n` if `Some(n)` is matched, as opposed to `Some(&n)` which matches if n is a reference. 
```rust
match maybe_name {
    Some(ref n) => println!("Hello, {n}"),
    _ => println!("Hello, world"),
}
```

# Enums
## memory storage
Pg 235

# Structs
## associated consts
You can attach default instantiations into a struct
```rust
pub struct Vector2 {
	x: f32,
	y: f32
}

impl Vector2 {
	const ZERO: Vector2 = Vector 2 { x: 0.0, y: 0.0 };
}
```

## Interior mutability
### `Cell<T>`
Can get and set without `mut` access to Cell. Only works for types that implement Copy because get() returns a copy and (i assume) set() uses a mem::move(). Not thread safe.

### `RefCell<T>`
This one also supports borrowing references to `T`'s value. Rust checks at compile time to see references are handled properly (no mut and normal references simultaneously). Not thread safe.

## Generics
### Turbofish
Can supply type parameter explicitly for generics
```rust
Queue::<char>::new()
```

### Generic impls
```rust
impl<T> Queue<T> { ... }
```
Is read as for any type T, here are the associated functions for `Queue<T>`.
This helps distinguish between impls for a specific type, like
```rust
impl Queue<f32> {}
```

### Lifetime params
For any given lifetime `'a`, you can make `MyStruct<'a>` that holds references with that lifetime 

### constant parameters
You can have generic structs accept a constant and use it to allocate a different number of elements. Only works for integer, bool, char
```rust
struct Polynomial<const N: usize> {
	coefficients: [f64; N]
}
impl<const N: usize> Polynomial<N> {}
```

Note: If you want to have a specific case of a parameter, for example, where N=2, you need to have a separate impl:
```rust
impl<const N: usize> Polynomial<2> {}
```

See matrix example from my code: https://discord.com/channels/273534239310479360/1133875121036206110

### generic ordering
1. lifetime
2. types
3. const values

## Compile-time checks
You can use associated constants to run code at runtime to make sure that values are what they should be.
https://doc.rust-lang.org/reference/items/associated-items.html#associated-constants


## Generic Associated Types
https://stackoverflow.com/q/54791718/10521417
"They allow to delay the application of the concrete type (or lifetime)" 

```rust
/// NOT THE RIGHT WAY
trait Iterator<'a> {
    type Item;
    fn next(&'a self) -> Option<Self::Item>;
}
```
In this example, the items returned from `next` need to live for as long as the iterator itself. But that is not a reasonable assumption.

Here the values that are being returned have a lifetime of the _reference passed to `next`_. 

```rust
trait Iterator {
    type Item<'a>;
    fn next<'a>(&'a mut self) -> Option<Self::Item<'a>>;
}
```

This is what allows you to loop and have mutable, overlapping, slices of a list. We want that mutable slice to exist for ONLY the loop iteration or else then you would have multiple mutable references (across loop iterations) potentially. If we used the first implementation of `Iterator`, the mutable slice would need to exist for the entire loop duration which is pretty useless.

```rust
fn count<I: Iterator>(it: I) -> usize {
    let mut count = 0;
    while let Some(_) = it.next() {
        count += 1;
    }
    count
}
```

## Orphan Rule
If you are implementing a trait, either the *trait* or the *type* must be new in the current crate.

For example, you cannot implement
```rust
impl Write for u8 {}
```
This is because you did not create `Write` or `u8`. If this was allowed, you would not be able to distinguish between someone else's implementation since they all look the same. 

# Macros
## Declarative macros
Like a match statement. Takes an expression, compares to patterns and runs patterns in block.
- `$` indicates a macro variable
- `$()` is like a capture group
- Can match any fragment into a variable `$x: expr` (`block` | `expr` | `ident` | `item` | `lifetime` | `literal` | `meta` | `pat` | `pat_param` | `path` | `stmt` | `tt` | `ty` | `vis`)
```rust
macro_rules! my_macro {
	()
}
```

### `#[macro_export]`
Makes macro available whenever crate is brought into scope

# Build settings
## Profiler 
Page 177


# resources
https://google.github.io/comprehensive-rust/

# articles
https://opensource.googleblog.com/2023/06/rust-fact-vs-fiction-5-insights-from-googles-rust-journey-2022.htm

## Useful crates
`enum_primitive` - enables casting from integer or whatever to enum (like the macro I made)