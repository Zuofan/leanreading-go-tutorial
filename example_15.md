##  实例 - 密码验证

### 描述

创建一个程序：验证用户登录凭证。该程序必须提示用户输入用户名和密码。程序会将用户给出的密码与已知密码比较：如果匹配，程序应该显示“Welcome!”；不匹配则显示“I don’t know you.”

### 难度

**简单+**

### 输入输出(_加粗的是需要用户输入的内容_)

**输入：**
What is your name? **jzy**
What is the password? **123456**

**输出：**
What is the password? 12345
I don't know you.

**或者输出：**
What is the password? abc$123
Welcome!

### 目的
    - 考察Go的条件结构的用法
    - 考虑实际应用场景下关于密码方面的用法，比如登录是一个应用常见的功能

### 实现 - default


```go
package main

import (
    "fmt"
    "time"
)

func main() {
    var name, password string

    fmt.Printf("What is your name? ")
    fmt.Scanf("%s", &name)
    fmt.Printf("What is the password? ")
    fmt.Scanf("%s", &password)

    //(1)
    if password == 'abc$123' {
        fmt.Printf("Welcome!\n")
    } else {
        fmt.Printf("I don't know you.\n")
    }

}

```

**解释**

`line (1):` 使用了`if`控制结构，Go在`if`的条件中，也不使用圆括号，和C语言不同，但是程序体部分需要使用大括号扩起来

### 挑战

**version01 要求**

研究如何阻止在输入时密码以明文形式显示在屏幕上


**version01 实现**

```go
package main

import (
	"fmt"
	"golang.org/x/term" //(1)
	"syscall"
)

func main() {
	var name, password string
	db := map[string]string{
		"jzy" : "abc$123",
		"admin" : "admin123",
	}

	fmt.Printf("What is your name? ")
	fmt.Scanf("%s", &name)
	fmt.Printf("What is the password? ")
	bytePassword, err := term.ReadPassword(int(syscall.Stdin))
	if err != nil {
		fmt.Printf("error:%s\n", err)
	}

	password = string(bytePassword)

	if dbPassword, _ := db[name]; dbPassword == password {
		fmt.Printf("Welcome!\n")
	} else {
		fmt.Printf("I don't know you.\n")
	}

}
```

**解释**

`line (1):` 使用官方的term包来实现相应的功能，这里涉及两个问题：
 - term的文档信息：`go doc term`
 - 如何安装`golang.org/x/term` TODO:添加一份安装使用说明

**version02 要求**

创建一个用户名和密码的映射,确保用户名和密码组合都匹配。


**version02 实现**

```go
package main

import (
	"fmt"
)

func main() {
	var name, password string

	//(1)
	db := map[string]string{
		"jzy" : "abc$123",
		"admin" : "admin123",
	}

	fmt.Printf("What is your name? ")
	fmt.Scanf("%s", &name)
	fmt.Printf("What is the password? ")
	fmt.Scanf("%s", &password)

	//(2)
	if dbPassword, ok := db[name]; ok && dbPassword == password {
		fmt.Printf("Welcome!\n")
	} else {
		fmt.Printf("I don't know you.\n")
	}

}
```

**解释**

`line (1):` 使用了字面量来初始化`map`键值对，也可以使用以下的方式，先建立，后存储值：

```go
db := make(map[string]string)
db["jzy"] = "abc$123"
db["admin"] = "admin123$123"
```

`line (2):`在Go中，任何类型如果没有被显式的初始化，都会有一个类型相对的默认零值，比如`string`类型的零值就是：`""`，整型就是：`0`等等。所以默认我们从`map`中取出一个值的时候，即使map中没有键，取出来的值依然是值类型相对应的零值，但有时也需要确认某一键是否存于`map`中，此时用的就是这种形式：第二个返回值是`boolean`型，用于确认是否有键存在于`map`中。

另外，在`if`结构中，可以执行多个操作，这里首先进行定义两个变量：`dbPassword`和`ok`，然后使用两个变量进行判断

