
## 常量

常量是一些在程序执行期不会变化的固定值。这些固定值也被称为字面量。

常量可以是任何基本数据类型之一：整型常量、浮点常量、字符常量、字符串常量。这些常量也被称为枚举常量。

常量一旦定义，其值就不可变，除此之外，使用方式和变量一样。

### 整型字面量

整型字面量可以是十进制、八进制、十六进制常量。前缀指定数值的基数：`0x`或者`0X`表示十六进制，`0`开始的表示八进制，默认没有前缀，表示十进制数。
整型字面量也可以有后缀：`U`和`L`的组合，分别表示无符号数和长整型。后缀大小写都可以，顺序任意。

下面是一些示例 −

```json
212         /* Legal */
215u        /* Legal */
0xFeeL      /* Legal */
078         /* Illegal: 8 is not an octal digit */
032UU       /* Illegal: cannot repeat a suffix */
```

下面是一些其它类型的整型常量 −

```json
85         /* decimal */
0213       /* octal */
0x4b       /* hexadecimal */
30         /* int */
30u        /* unsigned int */
30l        /* long */
30ul       /* unsigned long */
```

### 浮点字面量

浮点字面量可以包括整数部分，小数点，小数部分和指数部分。你可以将浮点表示成十进制形式或者指数形式。

十进制表示形式需要包括小数点，指数，或者两者都有；指数表示形式需要包括整数部分，小数部分，或者两者都有。由`e`或者`E`表示指数部分的符号。

下面是一些示例 −

```json
3.14159       /* Legal */
314159E-5L    /* Legal */
510E          /* Illegal: incomplete exponent */
210f          /* Illegal: no decimal or exponent */
.e55          /* Illegal: missing integer or fraction */
```

### 转义序列

使用反斜杠开始的特定字符，其在Go中有特殊的含义。它们被称为转义序列，比如换行符，`\n`、水平制表符`\t`、退格键等等。下面是一个转义字符的列表 - 

转义序列 | 描述
---| -------------
\\\ |	\ 字符
\\' |	' 字符
\\" |	" 字符
\\? |	? 字符
\a |	响铃或警告
\b |	退格键
\f |	换页符
\n |	换行符
\r |	回车符
\t |	水平制表符
\v |	垂直制表符
\ooo|	八进制表示的1到3个数字
\xhh ... |	十六进制表示的一个或多个数字

下面实例示范了如何使用`\t` - 

```go
package main

import "fmt"

func main() {
   fmt.Printf("Hello\tWorld!")
}
```

编译并执行上述实例，输出如下 −

```go
Hello World!
```

### 字符串字面量

字符串字面量使用`""`包括起来。字符串包含类似于字符文本的字符：普通字符、转义序列和通用字符。

字符串字母量和空白字符，可以将一个很长的行，断成多个短行。

下面是一些示例：三种形式的字符串是一样的。

```go
"hello, dear"

"hello, \

dear"

"hello, " "d" "ear"
```

### 关键字 —— `const`

Go使用 `const`定义常量，如下所示 −

```go
const variable type = value;
```

下面的实例示范了如何使用常量 −

```go
package main

import "fmt"

func main() {
   const LENGTH int = 10
   const WIDTH int = 5   
   var area int

   area = LENGTH * WIDTH
   fmt.Printf("value of area : %d", area)   
}
```

编译并执行上述实例，输出如下 −

```go
value of area : 50
```

注意，使用大写字母来定义常量，是一件值得提倡的编程方式。


## 原文 [Go - Constants](https://www.tutorialspoint.com/go/go_constants.htm)

Constants refer to fixed values that the program may not alter during its execution. These fixed values are also called literals.

Constants can be of any of the basic data types like an integer constant, a floating constant, a character constant, or a string literal. There are also enumeration constants as well.

Constants are treated just like regular variables except that their values cannot be modified after their definition.

### Integer Literals

An integer literal can be a decimal, octal, or hexadecimal constant. A prefix specifies the base or radix: 0x or 0X for hexadecimal, 0 for octal, and nothing for decimal.

An integer literal can also have a suffix that is a combination of U and L, for unsigned and long, respectively. The suffix can be uppercase or lowercase and can be in any order.

Here are some examples of integer literals −

```json
212         /* Legal */
215u        /* Legal */
0xFeeL      /* Legal */
078         /* Illegal: 8 is not an octal digit */
032UU       /* Illegal: cannot repeat a suffix */
```

Following are other examples of various type of Integer literals −

```json
85         /* decimal */
0213       /* octal */
0x4b       /* hexadecimal */
30         /* int */
30u        /* unsigned int */
30l        /* long */
30ul       /* unsigned long */
```

### Floating-point Literals

A floating-point literal has an integer part, a decimal point, a fractional part, and an exponent part. You can represent floating point literals either in decimal form or exponential form.

While representing using decimal form, you must include the decimal point, the exponent, or both and while representing using exponential form, you must include the integer part, the fractional part, or both. The signed exponent is introduced by e or E.

Here are some examples of floating-point literals −

```json
3.14159       /* Legal */
314159E-5L    /* Legal */
510E          /* Illegal: incomplete exponent */
210f          /* Illegal: no decimal or exponent */
.e55          /* Illegal: missing integer or fraction */
```

### Escape Sequence

When certain characters are preceded by a backslash, they will have a special meaning in Go. These are known as Escape Sequence codes which are used to represent newline (\n), tab (\t), backspace, etc. Here, you have a list of some of such escape sequence codes −

Escape sequence | Meaning
---| -------------
\\\ |	\ character
\\' |	' character
\\" |	" character
\\? |	? character
\a |	Alert or bell
\b |	Backspace
\f |	Form feed
\n |	Newline
\r |	Carriage return
\t |	Horizontal tab
\v |	Vertical tab
\ooo|	Octal number of one to three digits
\xhh . . .i |	Hexadecimal number of one or more digits

The following example shows how to use \t in a program −

```go
package main

import "fmt"

func main() {
   fmt.Printf("Hello\tWorld!")
}
```

When the above code is compiled and executed, it produces the following result −

```go
Hello World!
```
### String Literals in Go

String literals or constants are enclosed in double quotes "". A string contains characters that are similar to character literals: plain characters, escape sequences, and universal characters.

You can break a long line into multiple lines using string literals and separating them using whitespaces.

Here are some examples of string literals. All the three forms are identical strings.

```go
"hello, dear"

"hello, \

dear"

"hello, " "d" "ear"
```

### The const Keyword

You can use const prefix to declare constants with a specific type as follows −

```go
const variable type = value;
```

The following example shows how to use the const keyword −

```go
package main

import "fmt"

func main() {
   const LENGTH int = 10
   const WIDTH int = 5   
   var area int

   area = LENGTH * WIDTH
   fmt.Printf("value of area : %d", area)   
}
```

When the above code is compiled and executed, it produces the following result −

```go
value of area : 50
```

Note that it is a good programming practice to define constants in CAPITALS.