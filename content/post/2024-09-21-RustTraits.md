---
title: Rust Traits
subtitle: Learning Rust
date: 2024-09-21
tags: [ 
    "programming", 
    "code", 
    "rust",
] 
---

# Rust Traits, what are they?

This concept is interesting and I wanted to write it down as I learned it. I've just started learing Rust and will have
the terminology wrong! 

Traits can be added to types to allow them to do something, as if these were classes in C++ that already had methods 
implemented. 

In this scenario, I'm imagining that it's very importand to check if a number is divisible by seven, and if it actually is
the number seven. I can add a function to the "i32" and "u32" object. I would probably need to do this to i64 too, but 
this isn't particularly exciting to reiterate in code below.

```rust
trait Sevens {
    fn divisible_by_seven(&self) -> bool ;
    fn is_seven(&self) -> bool ;
}

impl Sevens for i32 {
    fn divisible_by_seven(&self) -> bool{
        self%7 == 0
    }
    fn is_seven(&self) -> bool{
        7 == *self
    }
}
```

And if I want the same to work on u32, I can add this to the code: 

```rust
impl Sevens for u32 {
    fn divisible_by_seven(&self) -> bool{
        self%7 == 0
    }
    fn is_seven(&self) -> bool{
        7 == *self
    }
}
```

And then main can be added (note, these are all in the same file at the moment as I haven't 
imported another file with a "use" declaration.


```rust
fn main() {
    let x: i32 = 9;
    let y: u32 = 49;
    println!("Is {} divisible by 7? {}", x, x.divisible_by_seven());
    println!("Is {} divisible by 7? {}", y, y.divisible_by_seven());
    println!("Is {} equal to 7? {}", y, y.is_seven());
    println!("Is {} equal to 7? {}", 7, 7.is_seven());
}
```

Ooh, notice I can now do `7.is_seven()`, isn't that interesting.
