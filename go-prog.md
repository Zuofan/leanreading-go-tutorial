
## 工具

### 离线文档工具 —— `go doc`

请熟悉使用`go doc`工具。

```bash
# 获取关于go中字符串的方法
go doc strings

# 获取关于os包中的Args的相关申明
go doc os.Args
```

## 初级实例

### 例1  -  `Hello World`实例

```go {.line-numbers highlight=5}

package main
import "fmt"

func main() {
    fmt.Println("Hello, せかい")
}

```

解释

`line 1：` 关键字`package`指定包。这里包的名字为`main`。指定`main`包的程序表示独立可运行的程序，同时，它的入口函数和`C`程序一样，也是`main`，如第四行代码所示。

`line 2:` 导入包——`fmt`。`fmt`提供了输出的方法——`Println`以供下面使用。

`line 4:` `func`表示定义一个方法，这里定义的独立可直接运行程序的起始入口函数——`main`。

`line 5:` 注意，这里是日文，表示世界的意思，这里主要是为了说明，`Go`内置了对于`unicode`的支持；另外，语句的结尾没有分号。

需要注意`import`语句在`package`语句后面，在`import`语句后面可以申明常量、变量、方法等。


### 例2  -  命令行参数例子

```go {.line-numbers highlight=[4 8 9-12]}
package main
import (
    "fmt"
    "os"
)

func main() {
    var s, sep string
    for i := 1; i < len(os.Args); i++ {
        s += sep + os.Args[i]
        sep = " "
    }
    fmt.Println(s)
}

```

`line 4:` 引入包`os`，因为用到`os.Args`方法，从命令行获取参数。

`line 8:` 申明两个变量：`s`和`sep`，类型为内置的`string`类型。在`Go`中，若变量未进行初始化，则初始化为默认值，这里字符串类型的值默认为`""`。

`line 10:` 表示对`string`类型的变量执行连接操作。

`line 9:` `i := 1` 表示申明并初始化数值为`1`的`int`变量，这个是采用和动态语言类似的做做法，利用上下文进行类型推导；表示一段循环，此循环的数组为：`os.Args`；`len`是内置的方法，表示获取`os.Args`数组的长度。


## 中级实例 TODO:to add

## 高级实例 TODO:to add