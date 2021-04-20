---
title: golang小白入门4 键盘输入输出
date: 2021-02-11 21:21:52
tags: [golang, beginners]
categories:
    - coding
    - golang
index_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210211212406681.png
banner_img: https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/golang-hacker (1).jpg
---

# golang小白入门4 键盘输入输出

# 输出

## 4.1 fmt包

fmt包实现了类似C语言printf和scanf的格式化I/O。格式化verb（'verb'）源自C语言但更简单。

详见官网fmt的API：https://golang.google.cn/pkg/fmt/

## 4.2 导入包

```go
import "fmt"
```

## 4.3 常用打印函数

### 4.3.1 打印

[func Print(a ...interface{}) (n int, err error)](https://golang.google.cn/pkg/fmt/#Print)

### 4.3.2 格式化打印

[func Printf(format string, a ...interface{}) (n int, err error)](https://golang.google.cn/pkg/fmt/#Printf)

### 4.3.3 **打印后换行**

[func Println(a ...interface{}) (n int, err error)](https://golang.google.cn/pkg/fmt/#Println)

格式化打印中的常用占位符：

```go
			%v,原样输出
			%T，打印类型
			%t,bool类型
			%s，字符串
			%f，浮点
			%d，10进制的整数
			%b，2进制的整数
			%o，8进制
			%x，%X，16进制
				%x：0-9，a-f
				%X：0-9，A-F
			%c，打印字符
			%p，打印地址
```

示例代码：

```go
package main

import (
	"fmt"
)

func main() {
	a := 100           //int
	b := 3.14          //float64
	c := true          // bool
	d := "Hello World" //string
	e := `Ruby`        //string
	f := 'A'
	fmt.Printf("%T,%b\n", a, a)
	fmt.Printf("%T,%f\n", b, b)
	fmt.Printf("%T,%t\n", c, c)
	fmt.Printf("%T,%s\n", d, d)
	fmt.Printf("%T,%s\n", e, e)
	fmt.Printf("%T,%d,%c\n", f, f, f)
	fmt.Println("-----------------------")
	fmt.Printf("%v\n", a)
	fmt.Printf("%v\n", b)
	fmt.Printf("%v\n", c)
	fmt.Printf("%v\n", d)
	fmt.Printf("%v\n", e)
	fmt.Printf("%v\n", f)

}
```

运行结果：

![image-20210211213023297](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210211213023297.png)

# 键盘输入

## 4.4 fmt包读取键盘输入

[func Scan(a ...interface{}) (n int, err error)](https://golang.google.cn/pkg/fmt/#Scan)

[func Scanf(format string, a ...interface{}) (n int, err error)](https://golang.google.cn/pkg/fmt/#Scanf)

[func Scanln(a ...interface{}) (n int, err error)](https://golang.google.cn/pkg/fmt/#Scanln)

```go
package main

import (
	"fmt"
)

func main() {
	var x int
	var y float64
	fmt.Println("请输入一个整数，一个浮点类型：")
	fmt.Scanln(&x,&y)//读取键盘的输入，通过操作地址，赋值给x和y   阻塞式
	fmt.Printf("x的数值：%d，y的数值：%f\n",x,y)

	fmt.Scanf("%d,%f",&x,&y)
	fmt.Printf("x:%d,y:%f\n",x,y)
}
```

运行结果：

![image-20210211214111130](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210211214111130.png)

## 4.5 **bufio包读取**

官方文档：

https://golang.google.cn/pkg/bufio/

bufio包中都是IO操作的方法：

先创建Reader对象：

![image-20210211213941807](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210211213941807.png)

然后就可以各种读取了：

![image-20210211214042730](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210211214042730.png)

示例代码：

```go
package main

import (
	"fmt"
	"os"
	"bufio"
)

func main() {
	fmt.Println("请输入一个字符串：")
	reader := bufio.NewReader(os.Stdin)
	s1, _ := reader.ReadString('\n')
	fmt.Println("读到的数据：", s1)

}
```

运行效果：

![image-20210211214337403](https://cdn.jsdelivr.net/gh/Brook1711/fig_for_blog/img/image-20210211214337403.png)

