
## Go - 基本程序结构 (4/29)

在讨论 Go 语言编程之前，我们先来讨论一下 Go 程序的一般结构，为下面章节打下基础。

### `Hello World`实例

一个 Go 程序大概包含一下几个部分 - 

- 包申明语句
- 包导入语句
- 方法
- 变量
- 语句和表达式
- 注释

我们来看第一个简单实例，打印"Hello, World"的实例 - 

```go
package main
import "fmt"
func main() {
   /* 第一个简单的程序。 */
   fmt.Println("Hello, World!")
}
```

`package main`：包申明语句，表明程序所在的包的名字。Go 程序必须要有包，因为 Go 是运行在包中，基于包来管理依赖。包名为`main`的包，是程序运行的入口点。每一个包都包含相应的路径和名字。

`import "fmt"`：Go编译器在编译之前会提前处理此类语句，它表明需要编译器导入包名为`fmt`的文件。

方法`main`：是程序执行的入口点。

`/*...*/`：表示注释，编译器在编译时会忽律此类语句。注释也支持以`//`开头的形式，和`Java`、`C++`的注释形式类似。

`fmt.Println(...)`：是一个函数调用，用于将字符串`"Hello，World"`输出到屏幕上。包`fmt`导出了其它包可以使用的公开函数——`Println`，用于显示信息的操作。

请注意方法——`Println`的第一个字母`P`是大写的。在 Go 语言中，如果函数、变量或常量的第一个字母是大写的，表明它们是**导出**的。这里的**导出**的意思是：这些函数、变量、常量可供其它导入的包所使用，它们不是私有的，是公开的。


### 运行一个 Go 程序

接下来讨论如何保存、编译，最后运行一个程序，步骤如下 -

1. 打开编辑器，创建文件，并输入上述代码

2. 保存文件，文件名为 `hello.go`

3. 打开命令行工具

4. 转到`hello.go`文件所在目录

5. 执行命令：`go run hello.go`

如果没有其它问题，屏幕将会输出：`Hello World!`

```bash
$ go run hello.go
Hello, World!
```

执行运行命令前，需要确保设置好包含Go编译器的环境变量。


## 原文 [Go - Programm Structure](https://www.tutorialspoint.com/go/go_program_structure.htm) 

Before we study the basic building blocks of Go programming language, let us first discuss the bare minimum structure of Go programs so that we can take it as a reference in subsequent chapters.

### Hello World Example

A Go program basically consists of the following parts −

- Package Declaration
- Import Packages
- Functions
- Variables
- Statements and Expressions
- Comments

Let us look at a simple code that would print the words "Hello World" −

```go
package main
import "fmt"
func main() {
   /* This is my first sample program. */
   fmt.Println("Hello, World!")
}
```

Let us take a look at the various parts of the above program −

The first line of the program package main defines the package name in which this program should lie. It is a mandatory statement, as Go programs run in packages. The main package is the starting point to run the program. Each package has a path and name associated with it.

The next line import "fmt" is a preprocessor command which tells the Go compiler to include the files lying in the package fmt.

The next line func main() is the main function where the program execution begins.

The next line /*...*/ is ignored by the compiler and it is there to add comments in the program. Comments are also represented using // similar to Java or C++ comments.

The next line fmt.Println(...) is another function available in Go which causes the message "Hello, World!" to be displayed on the screen. Here fmt package has exported Println method which is used to display the message on the screen.

Notice the capital P of Println method. In Go language, a name is exported if it starts with capital letter. Exported means the function or variable/constant is accessible to the importer of the respective package.

### Executing a Go Program

Let us discuss how to save the source code in a file, compile it, and finally execute the program. Please follow the steps given below −

1. Open a text editor and add the above-mentioned code.

2. Save the file as hello.go

3. Open the command prompt.

4. Go to the directory where you saved the file.

5. Type go run hello.go and press enter to run your code.

If there are no errors in your code, then you will see "Hello World!" printed on the screen.

```bash
$ go run hello.go
Hello, World!
```

Make sure the Go compiler is in your path and that you are running it in the directory containing the source file hello.go.