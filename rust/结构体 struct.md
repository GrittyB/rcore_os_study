## 使用例子
### 基本语法
```rust
// 定义
struct Person {
    name: String,
    age: u32,
    is_male: bool,
}

// 实例化
let person = Person {
    name: "Tom".to_string(),
    age: 20,
    is_male: true,
};

// 访问
println!("姓名：{}", person.name);
println!("年龄：{}", person.age);
println!("性别：{}", if person.is_male { "男" } else { "女" });

// 简化创建(构建函数)
fn build_user(email: String, username: String) -> User {
    User {
        email: email, // 参数和字段同名时,可以简写成email
        username: username,
        active: true,
        sign_in_count: 1,
    }
}

// 更新
let user2 = User {
    email: String::from("another@example.com"),
    ..user1
};
```


### 自定义方法
```rust
impl Person {
    fn say_hello(&self) {
        println!("大家好，我是{}，今年{}岁", self.name, self.age);
    }
}
let person = Person {..};
person.say_hello();
```
### 关联函数
定义在 `impl` 中且没有 `self` 的函数被称之为**关联函数**： 
因为它没有 `self`，不能用`.` 而要用`::`的形式调用，
因此它是一个**函数**而不是方法，
它又在 `impl` 中，与结构体紧密关联，因此称为关联函数。

关联函数例子: `String::from`，用于创建一个动态字符串。
```rust
impl Person {
	// 大写开头的Self指代 特征 或者 方法 类型的别名
    fn new(name: &str, age: u32, is_male: bool) -> Self {
        Self {
            name: name.to_string(),
            age,
            is_male,
        }
    }
}
```
