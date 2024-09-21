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
implemented. So if I want to check if an i32 is divisible by 7, I can add: 

```
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

fn main() {
    let x: i32 = 9;
    let y: u32 = 49;
    println!("Is {} divisible by 7? {}", x, x.divisible_by_seven());
    println!("Is {} divisible by 7? {}", y, y.divisible_by_seven());
    println!("Is {} equal to 7? {}", y, y.is_seven());
    println!("Is {} equal to 7? {}", 7, 7.is_seven());
}
```

And if I want the same to work on u32, I can add this to the code: 

```
impl Sevens for u32 {
    fn divisible_by_seven(&self) -> bool{
        self%7 == 0
    }
    fn is_seven(&self) -> bool{
        7 == *self
    }
}
```
