## 使用例子
### 基本使用
```rust
enum Color {
    Red,
    Green,
    Blue,
}
```
 ### 包含数据
```rust
enum IpAddr {
    V4(u8, u8, u8, u8),
    V6(String),
}
```

```rust
enum Shape {
	//结构体
    Rectangle { width: u32, height: u32 },
    //元组结构体
    Circle(f64),
    Triangle { a: f64, b: f64, c: f64 },
}
```

### 和match联用
```rust
let color = Color::Red;
match color {
    Color::Red => println!("红色"),
    Color::Green => println!("绿色"),
    Color::Blue => println!("蓝色"),
}
```

---
### Option枚举
```rust
let x: Option<i32> = Some(5);
let y: Option<i32> = None;
```
`Option` 枚举是一种非常常用的类型,它的两个实例是`Some(T)`和`None`
```rust
enum Option<T> {
    None,
    Some(T),
}
```
使用例子:
在一个数组中查找第一个满足某个条件的元素：
```rust
// define
// F是个闭包
fn find_first<T, F>(array: &[T], f: F) -> Option<&T>
where
    F: Fn(&T) -> bool,
{
    for item in array {
        if f(item) {
            return Some(item);
        }
    }
    None
}
// use
let array = [1, 2, 3, 4, 5];
let result = find_first(&array, |&x| x > 3);
match result {
    Some(&value) => println!("找到了第一个大于 3 的元素：{}", value),
    None => println!("没有找到符合条件的元素"),
}
```
