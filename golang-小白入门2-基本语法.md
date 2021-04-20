---
title: 'golang 小白入门2:基本语法'
date: 2021-02-11 13:16:24
tags: [golang, beginners]
categories:
    - coding
    - golang
index_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210211131859686.png
banner_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/golang-hacker (1).jpg
---

# golang 小白入门2:基本语法

本帖大部分内容摘抄自

https://github.com/rubyhan1314/Golang-100-Days

麻烦给人家点个`star`ヽ(✿ﾟ▽ﾟ)ノ

## 2.1 变量

变量是为存储特定类型的值而提供给内存位置的名称。在go中声明变量有多种语法。

所以变量的本质就是一小块内存，用于存储数据，在程序运行过程中数值可以改变

var名称类型是声明单个变量的语法。

> 以字母或下划线开头，由一个或多个字母、数字、下划线组成

### 2.1.1 声明

第一种，指定变量类型，声明后若不赋值，使用默认值

```go
var name type

name = value
```

第二种，根据值自行判定变量类型(类型推断Type inference)

如果一个变量有一个初始值，Go将自动能够使用初始值来推断该变量的类型。因此，如果变量具有初始值，则可以省略变量声明中的类型。

```go
var name = value
```

第三种，省略var, 注意 :=左侧的变量不应该是已经声明过的(多个变量同时声明时，至少保证一个是新变量)，否则会导致编译错误(简短声明)

```go
name := value
// 例如
var a int = 10
var b = 10
c : = 10
```

> 这种方式它只能被用在函数体内，而不可以用于全局变量的声明与赋值

**示例代码：**

```go
package main
var a = "Hello"
var b string = "World"
var c bool

func main(){
    println(a, b, c)
}
```

### 2.1.2 多变量声明

第一种，以逗号分隔，声明与赋值分开，若不赋值，存在默认值

```go
var name1, name2, name3 type
name1, name2, name3 = v1, v2, v3
```

第二种，直接赋值，下面的变量类型可以是不同的类型

```go
var name1, name2, name3 = v1, v2, v3
```

第三种，集合类型

```go
var (
    name1 type1
    name2 type2
)
```

**注意事项：**

- 变量必须先定义才能使用

- go语言是静态语言，要求变量的类型和赋值的类型必须一致。

- 变量名不能冲突。(同一个作用于域内不能冲突)

- 简短定义方式，左边的变量名至少有一个是新的

- 简短定义方式，不能定义全局变量。

- 变量的零值。也叫默认值。

- 变量定义了就要使用，否则无法通过编译。

如果在相同的代码块中，我们不可以再次对于相同名称的变量使用初始化声明，例如：a := 20 就是不被允许的，编译器会提示错误 no new variables on left side of :=，但是 a = 20 是可以的，因为这是给相同的变量赋予一个新的值。

如果你在定义变量 a 之前使用它，则会得到编译错误 undefined: a。如果你声明了一个局部变量却没有在相同的代码块中使用它，同样会得到编译错误，

在同一个作用域中，已存在同名的变量，则之后的声明初始化，则退化为赋值操作。但这个前提是，最少要有一个新的变量被定义，且在同一作用域，例如，下面的y就是新定义的变量

```go
package main

import (
	"fmt"
)

func main() {
	x := 140
	fmt.Println(&x)
	x, y := 200, "abc"
	fmt.Println(&x, x)
	fmt.Print(y)
}
```

## 2.2 常量

### 2.2.1 普通常量

常量是一个简单值的标识符，在程序运行时，不会被修改的量。

```go
const identifier [type] = value
//显式类型定义： 
const b string = "abc"
//隐式类型定义： 
const b = "abc"
```

示例代码：

```go
package main

import "fmt"

func main() {
   const LENGTH int = 10
   const WIDTH int = 5   
   var area int
   const a, b, c = 1, false, "str" //多重赋值

   area = LENGTH * WIDTH
   fmt.Printf("面积为 : %d", area)
   println()
   println(a, b, c)   
}
```

常量可以作为枚举，常量组

```go
const (
    Unknown = 0
    Female = 1
    Male = 2
)
```

常量组中如不指定类型和初始化值，则与上一行非空常量右值相同

```go
package main

import (
	"fmt"
)

func main() {
	const (
		x uint16 = 16
		y
		s = "abc"
		z
	)
	fmt.Printf("%T,%v\n", y, y)
	fmt.Printf("%T,%v\n", z, z)
}
```

注意事项：

- 常量中的数据类型只可以是布尔型、数字型（整数型、浮点型和复数）和字符串型

- 不曾使用的常量，在编译的时候，是不会报错的

- 显示指定类型的时候，必须确保常量左右值类型一致，需要时可做显示类型转换。这与变量就不一样了，变量是可以是不同的类型值

### 2.2.2 iota

iota，特殊常量，可以认为是一个可以被编译器修改的常量

iota 可以被用作枚举值：

```go
const (
    a = iota
    b = iota
    c = iota
)
```

第一个 iota 等于 0，每当 iota 在新的一行被使用时，它的值都会自动加 1；所以 a=0, b=1, c=2 可以简写为如下形式：

```go
const (
    a = iota
    b
    c
)
```

示例代码：

```go
package main

import "fmt"

func main() {
    const (
            a = iota   //0
            b          //1
            c          //2
            d = "ha"   //独立值，iota += 1
            e          //"ha"   iota += 1
            f = 100    //iota +=1
            g          //100  iota +=1
            h = iota   //7,恢复计数
            i          //8
    )
    fmt.Println(a,b,c,d,e,f,g,h,i)
}
```

如果中断iota自增，则必须显式恢复。且后续自增值按行序递增

自增默认是int类型，可以自行进行显示指定类型

数字常量不会分配存储空间，无须像变量那样通过内存寻址来取值，因此无法获取地址