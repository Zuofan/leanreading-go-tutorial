

## 输入输出例子

### 01. 问好

- 描述

    提示用户输入姓名，随后，输出问候语句

- 难度：**简单**^-^

- 输入输出

    >What's your name? YourName
    >Hello, YourName, nice to meet you.


- 目的

    考察基本的输入输出函数用法

- 代码

    ```go{.line-numbers highlight=8}

    package main
    import "fmt"

    func main() {
        var name string
        fmt.Printf("请问你是谁? ")
        //跳过可能的错误检查
        fmt.Scanf("%s", &name)

        fmt.Printf("你好, %s, 欢迎你使用Go!", name)
    }
    ```

`line 8：` 从标准输入获取用户的输入

```go

// (1) Scanf从标准输入扫描文本，根据format参数指定的格式去读取由空白符分隔的值保存到传递给本函数的参数中。

// (2) 本函数返回成功扫描的数据个数和遇到的任何错误

func Scanf(format string, a ...interface{}) (n int, err error)

```
