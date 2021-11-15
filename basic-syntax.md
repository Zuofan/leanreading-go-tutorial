
## Go - 基本语法

上一章节我们讨论了Go 程序的基本结构，这里我们继续看一下组成Go程序的其它基本组成部分。

### Go的词法单元——Tokens

Go程序中包含多个词法单元。词法单元可能是关键字，也可能是标识符，或者常量，字符串字面量或者符号，比如下面的语句包含6个词法单元 - 

```go
fmt.Println("Hello, World!")
```

词法单元分别是 −

```go
fmt
.
Println
(
   "Hello, World!"
)
```

### 行分隔符

在Go语言中，语句和语句的分隔符是使用行分隔符来进行的，不需要类似于`C语言`中的`;`分隔符。Go编译器内部在实现时，自动添加`;`分隔符，做为逻辑块结束的标志。比如下面使用行分隔符的两个语句 - 
```go
fmt.Println("Hello, World!")
fmt.Println("I am in Go Programming World!")
```



### 注释
注释的作用类似于帮助文档，在编译时会被忽略。注释以`/*`开始，以`*/`结束。
```go
/* my first program in Go */
```
注释不可嵌套，它们也不能出现在字符串中。

### 标识符

Go标识符表示一个变量、函数或者其它用户定义任何程序单元。标识符以字符（`A-Z 或 a-z`）或者下划线——`_`开始，后面跟着零个或多个字符、下划线、数字（`0-9`）

identifier = letter { letter | unicode_digit }* [^1]

标识符中不允许包含一些标点符号，比如`@, $, %`。Go是一门区分大小写的语言，故而标识符——`Manpower`和`manpower`不一样，下面是一些编译器可接受的标识符 -
```go
mahesh      kumar   abc   move_name   a_123
myname50   _temp    j      a23b9      retVal
```
### 关键字

Go包含一定数量的关键字，此类保留关键字不可用于常量、变量，或者做为任何其它标识符的名字。

break	       | default      | 	func	   | interface    | 	select
------------   | -------------| ---------------| -------------| -------------|
case	       | 	defer	  | 	Go	       | 	map		  | Struct
chan	       | else	      | 	Goto	   |package	      |Switch
const	       |fallthrough   |	if	           |range	      |Type
continue	   |for	          |import	       |return	      |Var

### Go中的空白符

空白符用于表示空格、制表符、回车和注释。只包含空白符的被定义为一个空行，Go编译器在处理时会忽略。

空白符用于语句内部组成部分的分隔符，比如在下面的示例中，`int`做为本申明语句的结束词法单元 - 
```go
var age int
```
在`age`和`int`中，至少有一个空格符用于区分这两个词法单元。在下面的示例中 -
```go
fruit = apples + oranges;   // get the total fruit
```
无需空白符分割`fruit`和`=`，或者`=`和`apple`。不过你也可以加上空白符，方便用户阅读代码。

## 原文 [Go - Basic Syntax](tutorialspoint.com/go/go_basic_syntax.htm) 

We discussed the basic structure of a Go program in the previous chapter. Now it will be easy to understand the other basic building blocks of the Go programming language.

### Tokens in Go

A Go program consists of various tokens. A token is either a keyword, an identifier, a constant, a string literal, or a symbol. For example, the following Go statement consists of six tokens −

```go
fmt.Println("Hello, World!")
```
The individual tokens are −
```go
fmt
.
Println
(
   "Hello, World!"
)
```
### Line Separator

In a Go program, the line separator key is a statement terminator. That is, individual statements don't need a special separator like “;” in C. The Go compiler internally places “;” as the statement terminator to indicate the end of one logical entity.

For example, take a look at the following statements −
```go
fmt.Println("Hello, World!")
fmt.Println("I am in Go Programming World!")
```
### Comments

Comments are like helping texts in your Go program and they are ignored by the compiler. They start with /* and terminates with the characters */ as shown below −
```go
/* my first program in Go */
```
You cannot have comments within comments and they do not occur within a string or character literals.

### Identifiers

A Go identifier is a name used to identify a variable, function, or any other user-defined item. An identifier starts with a letter A to Z or a to z or an underscore _ followed by zero or more letters, underscores, and digits (0 to 9).

identifier = letter { letter | unicode_digit }.

Go does not allow punctuation characters such as @, $, and % within identifiers. Go is a case-sensitive programming language. Thus, Manpower and manpower are two different identifiers in Go. Here are some examples of acceptable identifiers −
```go
mahesh      kumar   abc   move_name   a_123
myname50   _temp    j      a23b9      retVal
```
### Keywords

The following list shows the reserved words in Go. These reserved words may not be used as constant or variable or any other identifier names.



break	       | default      | 	func	   | interface    | 	select
------------   | -------------| ---------------| -------------| -------------|
case	       | 	defer	  | 	Go	       | 	map		  | Struct
chan	       | else	      | 	Goto	   |package	      |Switch
const	       |fallthrough   |	if	           |range	      |Type
continue	   |for	          |import	       |return	      |Var

### Whitespace in Go

Whitespace is the term used in Go to describe blanks, tabs, newline characters, and comments. A line containing only whitespace, possibly with a comment, is known as a blank line, and a Go compiler totally ignores it.

Whitespaces separate one part of a statement from another and enables the compiler to identify where one element in a statement, such as int, ends and the next element begins. Therefore, in the following statement −
```go
var age int;
```
There must be at least one whitespace character (usually a space) between int and age for the compiler to be able to distinguish them. On the other hand, in the following statement −
```go
fruit = apples + oranges;   // get the total fruit
```
No whitespace characters are necessary between fruit and =, or between = and apples, although you are free to include some if you wish for readability purpose.


[^1]: 这里使用正则表达式来表示标识符的组成，在编译相关的书籍中经常出现