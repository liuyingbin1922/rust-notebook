# rust-notebook
学习rust笔记

## 章节

### 变量绑定与解构

在rust语言中，赋值体现的是变量的绑定，通俗的理解可以是变量在内存中主人。
eg:

```rust
fn main() {
    let mut x = 5;
    println!("The value of x is: {}", x);
    x = 6;
    println!("The value of x is: {}", x);
}
```
`mut` 声明为可变对象，表示可以将其声明为动态的值；


解构式赋值：

```rust
struct Struct {
    e: i32
}

fn main() {
    let (a, b, c, d, e);

    (a, b) = (1, 2);
    [c, .., d, _] = [1, 2, 3, 4, 5];
    Struct { e, .. } = Struct { e: 5 };

    assert_eq!([1, 2, 1, 4, 5], [a, b, c, d, e]);
}
```
(a,b) = (1,2) 表示解构；

[c,...d] 表示元组；

Struct 表示结构体；

