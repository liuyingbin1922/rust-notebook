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

### 基本类型之数值类型

```rust
i32: 创建数据时默认的类型;
```


序列：

```rust

for i in 1..=5 {
    println!("val:{}" , i)
}
```

bool 类型

### rust 所有权的理解

1. rust 的值有且只有一个 所有者；

2. 当所有者离开作用域范围时，这个值将被丢弃；


```rust
fn main() {
    let s1 = String::from("hello");
    let s2 = s1;

    println!("{}, world!", s1);
}
```

上述代码是所有权转移之后， 将会看到以下的报错：

```
error[E0382]: use of moved value: `s1`
 --> src/main.rs:5:28
  |
3 |     let s2 = s1;
  |         -- value moved here
4 |
5 |     println!("{}, world!", s1);
  |                            ^^ value used here after move
  |
  = note: move occurs because `s1` has type `std::string::String`, which does
  not implement the `Copy` trait
```

