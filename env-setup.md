

## Go - 环境变量 (3/24）

### 设置本地环境

您需要以下两个软件来设置您本地的Go语言的开发环境 - 

文本编辑器和Go编译器

### 文本编辑器

您需要一个文本编辑器来编写您的程序，比如Windows Notepad、OS Edit command、Brief、Epsilon、EMACS、vim、vi等

软件及其版本可能会因为操作系统而有不同，比如Notepad只有在Windows下才支持，而vim和vi可以同事用在Windows、Linux、UNIX操作系统下。

使用文本编辑器创建的文件被称为源文件，包含程序代码。在Go语言中，go源文件是以`.go`做为文件后缀名的。

在开始之前，您需要知道如何编写一个程序，保存、编译，最后执行。

### Go 编译器

源文件是供人类阅读，它需要被编译，转换为本地机器指令，这样您机器上的CPU才能一条指令一条指令的执行。Go编译器编译源文件，生成最终可执行的程序。

Go编译器的二进制可执行版本有FreeBSD(发布版8或者以上)、Linux、Mac OS X(雪豹或以上)、Windows下32位和64位的x86架构版本。

下面的章节阐述如何在不同的操作系统下二进制安装Go编译器。

### 压缩包下载

下载最新版本的[Go编译器](https://golang.org/dl/)版本，本份指南采用的是：go1.4.windows-amd64.msi，拷贝至`C:\>go`文件夹下：

操作系统        |   压缩包的名字
------------   | -------------
Windows	       |    go1.4.windows-amd64.msi
Linux	       |    go1.4.linux-amd64.tar.gz
Mac	           |	go1.4.darwin-amd64-osx10.8.pkg
FreeBSD	       |    go1.4.freebsd-amd64.tar.gz

###  `UNIX/Linux/Mac OS X、FreeBSD`系统下安装

解压压缩包至 `/usr/local`路径下，构建如下所示的路径：`/usr/local/go` 命令如下：

`tar -C /usr/local -xzf go1.4.linux-amd64.tar.gz`

将`/usr/local/go/bin`添加到环境变量`PATH`中，

操作系统 |	命令
------------   | -------------
Linux	       |    export PATH = $PATH:/usr/local/go/bin
Mac	           |    export PATH = $PATH:/usr/local/go/bin
FreeBSD	       |    export PATH = $PATH:/usr/local/go/bin

### Windows系统下安装

使用如下的步骤进行安装，将MSI安装包安装在C:\Go下，安装程序会将c:\Go\bin的目录添加到Windows的环境变量中。重启命令行工具使配置生效。

### 验证安装是否有效

创建一个名为`test.go`的文件至**C:\\>Go_WorkSpace.**目录下

文件: test.go

```go
package main

import "fmt"
func main() {
   fmt.Println("Hello, World!")
}
```

编译并执行test.go −

```bash
C:\Go_WorkSpace>go run test.go
```

输出

```text
Hello, World!
```

## 原文 [Go - Overview](https://www.tutorialspoint.com/go/go_overview.htm) 

### Local Environment Setup
If you are still willing to set up your environment for Go programming language, you need the following two software available on your computer −

A text editor
Go compiler


### Text Editor

You will require a text editor to type your programs. Examples of text editors include Windows Notepad, OS Edit command, Brief, Epsilon, EMACS, and vim or vi.

The name and version of text editors can vary on different operating systems. For example, Notepad is used on Windows, and vim or vi is used on Windows as well as Linux or UNIX.

The files you create with the text editor are called source files. They contain program source code. The source files for Go programs are typically named with the extension ".go".

Before starting your programming, make sure you have a text editor in place and you have enough experience to write a computer program, save it in a file, compile it, and finally execute it.

### The Go Compiler

The source code written in source file is the human readable source for your program. It needs to be compiled and turned into machine language so that your CPU can actually execute the program as per the instructions given. The Go programming language compiler compiles the source code into its final executable program.

Go distribution comes as a binary installable for FreeBSD (release 8 and above), Linux, Mac OS X (Snow Leopard and above), and Windows operating systems with 32-bit (386) and 64-bit (amd64) x86 processor architectures.

The following section explains how to install Go binary distribution on various OS.

### Download Go Archive

Download the latest version of Go installable archive file from Go Downloads. The following version is used in this tutorial: go1.4.windows-amd64.msi.

It is copied it into C:\>go folder.
	
OS             |   Archive name
------------   | -------------
Windows	       |    go1.4.windows-amd64.msi
Linux	       |    go1.4.linux-amd64.tar.gz
Mac	           |	go1.4.darwin-amd64-osx10.8.pkg
FreeBSD	       |    go1.4.freebsd-amd64.tar.gz


### Installation on UNIX/Linux/Mac OS X, and FreeBSD

Extract the download archive into the folder /usr/local, creating a Go tree in /usr/local/go. For example −

tar -C /usr/local -xzf go1.4.linux-amd64.tar.gz

Add /usr/local/go/bin to the PATH environment variable.

OS	            | Output
------------   | -------------
Linux	       |    export PATH = $PATH:/usr/local/go/bin
Mac	           |    export PATH = $PATH:/usr/local/go/bin
FreeBSD	       |    export PATH = $PATH:/usr/local/go/bin

### Installation on Windows

Use the MSI file and follow the prompts to install the Go tools. By default, the installer uses the Go distribution in c:\Go. The installer should set the c:\Go\bin directory in Window's PATH environment variable. Restart any open command prompts for the change to take effect.

### Verifying the Installation

Create a go file named test.go in **C:\\>Go_WorkSpace.**

File: test.go

```go
package main

import "fmt"
func main() {
   fmt.Println("Hello, World!")
}
```

Now run test.go to see the result −

```bash
C:\Go_WorkSpace>go run test.go
```

Output

```text
Hello, World!
```