---
description: overview
---

## `Go`概览

`Go`是一门从设计之初就考虑系统编程的一门通用语言，在2007年由Google的三位工程师——`Robert Griesemer`、`Rob Pike`、 `Ken Thompson`开始设计并开发。`Go`语言是一门强类型的静态语言，内置垃圾回收、并行编程。

`Go`应用通过包来实现对依赖的有效管理。`Go`语言实现机制是基于传统的编译和链接模型来生成一个可执行的二进制文件。在2009年11月份，`Go`语言被正式发布。目前，`Go`语言也被用在Google的一些生产系统中。

### `Go`语言特性

Go语言重要特性如下：

- 采用类似动态语言的上下文推断机制：比如，类型推导（语句`x := 0` ，表示一个变量类型是`int`有效申明语句）

- 编译时间极快

- 内置并行编程机制：轻量级的进程（通过go语言的协程，即`go routines`）

- `Go`程序简洁、扼要、安全

- 支持接口和`Type Embedding` [^1]

- 通过静态链接生成的本地二进制可执行文件没有外部依赖

### `Go`语言深思熟虑不支持的其它语言常用特性 TODO:optimize

`Go`语言实现为了保证语言的简洁、扼要，针对下面一些其它语言常有的语言特性，`Go`并没有包含进来：

- 类继承

- 方法或操作符的重载

- 包的循环依赖 TODO:optimize

- 指针运算

- 泛型编程

### `Go`程序

`Go`程序可能很小，只包含3行代码；也可能很大，包含几百万行的代码。程序可被划分到一个或多个以`.go`作为文件后缀的文本文件中，比如`hello.go`。

可以使用`vi`、`vim`或其它文本编辑器来编写您的`Go`程序。


## 原文 [Go - Overview](https://www.tutorialspoint.com/go/go_overview.htm) 


Go is a general-purpose language designed with systems programming in mind. It was initially developed at Google in the year 2007 by Robert Griesemer, Rob Pike, and Ken Thompson. It is strongly and statically typed, provides inbuilt support for garbage collection, and supports concurrent programming.

Programs are constructed using packages, for efficient management of dependencies. Go programming implementations use a traditional compile and link model to generate executable binaries. The Go programming language was announced in November 2009 and is used in some of the Google's production systems.

### Features of Go Programming

The most important features of Go programming are listed below −

- Support for environment adopting patterns similar to dynamic languages. For example, type inference (x := 0 is valid declaration of a variable x of type int)

- Compilation time is fast.

- Inbuilt concurrency support: lightweight processes (via go routines), channels, select statement.

- Go programs are simple, concise, and safe.

- Support for Interfaces and Type embedding.

- Production of statically linked native binaries without external dependencies.

### Features Excluded Intentionally

To keep the language simple and concise, the following features commonly available in other similar languages are omitted in Go −

- Support for type inheritance

- Support for method or operator overloading

- Support for circular dependencies among packages

- Support for pointer arithmetic

- Support for assertions

- Support for generic programming

### Go Programs

A Go program can vary in length from 3 lines to millions of lines and it should be written into one or more text files with the extension ".go". For example, hello.go.

You can use "vi", "vim" or any other text editor to write your Go program into a file.


[^1]: [Type Embedding](https://go101.org/article/type-embedding.html)