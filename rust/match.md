## 使用例子
### 基本语法
```rust
enum Color {
    Red,
    Green,
    Blue,
}

let color = Color::Green;
match color {
    Color::Red => println!("The color is red"),
    Color::Green => println!("The color is green"),
    Color::Blue => println!("The color is blue"),
}
// 匹配区间
let x = 5;
match x {
    1..=5 => println!("x is between 1 and 5"),
    _ => println!("x is not between 1 and 5"),
}

//匹配元组
let tuple = (1, "hello");

match tuple {
    (0, _) => println!("First element is 0"),
    (_, "world") => println!("Second element is 'world'"),
    (x, y) => println!("Tuple contains {} and {}", x, y),
}
```

