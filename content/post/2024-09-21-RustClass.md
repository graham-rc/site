---
title: Rust "Classes" -> struct + impl
subtitle: Learning Rust
date: 2024-09-21
tags: [ 
    "programming", 
    "code", 
    "rust",
] 
---

## Q: How do I write a class in Rust?
## A: Use a struct and "impl" some functions.
</br>
Following is the code for a very basic struct with accessors and mutators.

```rust
struct MyStruct{
    word: String,
    number: i32
}

impl MyStruct{
    pub fn new(s: String, i: i32) -> MyStruct {
        return MyStruct{
            word: s,
            number: i
        }
    }
    pub fn set_word(&mut self, w: String) { self.word = w; }
    pub fn set_number(&mut self, n: i32) { self.number = n; }
    pub fn word(&self) -> String { self.word.to_string() }
    pub fn number(&self) -> i32 { self.number }
}

fn main() {
    let mut m = MyStruct::new("potato".to_string(), 3);
    println!("{}, {:>5}", m.word(), m.number());
    println!("{}, {:>5}", m.word(), m.number());
    m.set_number(1234);
    m.set_word("Balls".to_string());
    println!("{}, {:>6}", m.word(), m.number());
}
```

Output: 
```
potato,     3
potato,     3
Balls,   1234
```
