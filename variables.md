## Go - 变量

变量定义了一处可供程序进行各种操作的存储空间。在Go中，每个变量都属于一个特定的类别，这个类别决定了变量所需要的内存空间大小和结构，在此空间中所能存储的值的范围，以及一系列可以对变量进行的操作。

变量的名字由字母、数字、下划线所组成。名字的开头必须是一个字符或一个下划线。Go区分大小写——一个大写的字符和小写的字母是不同的。上一章阐述了基本的数据类型，本章阐述基本的变量类型。

序号    | 类型和描述
-------| -------------
1      | **byte** <br/> 一个8位长度的byte型，长度同于uint8
2      | **int** <br/> 机器上一般整数类型的大小
3      | **float32** <br/> 单精度浮点

Go 语言也可以定义其它变量类型，比如枚举、指针、数组、结构体、联合体。本节主要关注基础的变量类型，其它类型在其它章节讨论。

### 变量定义

定义变量就是告诉编译器为变量在特定的位置处定义一个特定大小的空间。变量定义指定一个数据类型，以及一个或多个的变量列表，如下所示 - 

```go
var variable_list optional_data_type;
```

**optional_data_type** 表示一个数据类型，比如有byte、int、float32, complex64, boolean 或者其它用户自定义的类型；**variable_list** 表示一个或多个，使用逗号进行分隔的变量，下面是一些例子 - 

```go
var  i, j, k int;
var  c, ch byte;
var  f, salary float32;
d =  42;
```

语句 **“var i, j, k;”** 声明并定义了变量i,j和k，这告诉编译器创建类型为`int`的变量i，j和k。

变量在声明的时候，可以进行初始化——给变量一个初始值。变量的类型由编译器依据初始值进行推断。初始表达式由一个等号，并后接一个常量表达式所组成 - 

```go
variable_name = value;
```

比如下面的例子 - 

```go
d = 3, f = 5;    // declaration of d and f. Here d and f are int 
```
如果变量没有进行初始化操作，具有静态存储周期的变量以 nil 隐式初始化（即所有的字节值都为0）；其它变量的初始值是其变量所属类型的零值。


### 静态类型声明

一个静态类型的变量声明可以告诉编译器变量的类型和变量名字，编译器可以利用此进行进行接下来的编译处理，无需变量的其它信息。编译器编译程序只需要变量声明即可，但在编译器链接并形成可执行的程序时，需要变量的实际类型。

**实例**

下面的例子在main函数中，声明了变量的类型，并进行了初始化 -

```go
package main

import "fmt"

func main() {
   var x float64
   x = 20.0
   fmt.Println(x)
   fmt.Printf("x is of type %T\n", x)
}
```

上述例子编译并执行，输出如下 −

```go
20
x is of type float64
```

### 动态类型声明和类型推断

动态类型声明需要编译器依据初始值推断变量的类型。编译器并不一定需要指明变量的类型。

**实例**

在下面的例子中，变量并未指明类型。需要留意的是，在类型推断中，Go使用的是`:=`操作符，而非赋值所使用的`=`的形式。

```go
package main

import "fmt"

func main() {
   var x float64 = 20.0

   y := 42 
   fmt.Println(x)
   fmt.Println(y)
   fmt.Printf("x is of type %T\n", x)
   fmt.Printf("y is of type %T\n", y)	
}
```
上述例子编译并执行，输出如下 −

```go
20
42
x is of type float64
y is of type int
```

### 混合的变量声明语句


基于类型推导，多种不同的变量可以在一句 go 语句中完成声明。

**实例**

```go
package main

import "fmt"

func main() {
   var a, b, c = 3, 4, "foo"  
	
   fmt.Println(a)
   fmt.Println(b)
   fmt.Println(c)
   fmt.Printf("a is of type %T\n", a)
   fmt.Printf("b is of type %T\n", b)
   fmt.Printf("c is of type %T\n", c)
}
```

上述例子编译并执行，输出如下 −

```go
3
4
foo
a is of type int
b is of type int
c is of type string
```

### 左值（`lvalue`）和右值（`rvalue`）

Go有两种表达式 - 

- **lvalue** − 左值表达式是指一个内存存储位置。左值可以出现在赋值表达式的左边和右边。

- **rvalue** − 右值指的是一个可以存储到某一内存位置的数据值。右值只能出现在赋值表达式的右边，而不能出现在赋值表达式的左边。

变量是左值表达式，可以出现在赋值表达式的左边，而数值字面量是右值，不能出现在赋值表达式的左边，而被赋值，只能出现在赋值表达式的右边。

下面是有效的语句 −

```go
x = 20.0
```

下面的语句是非法的，会出现编译错误 −

```go
10 = 20
```



## 原文 [Go - Variables](https://www.tutorialspoint.com/go/go_variables.htm)

A variable is nothing but a name given to a storage area that the programs can manipulate. Each variable in Go has a specific type, which determines the size and layout of the variable's memory, the range of values that can be stored within that memory, and the set of operations that can be applied to the variable.

The name of a variable can be composed of letters, digits, and the underscore character. It must begin with either a letter or an underscore. Upper and lowercase letters are distinct because Go is case-sensitive. Based on the basic types explained in the previous chapter, there will be the following basic variable types −


Sr.No. | Types & Description
-------| -------------
1      | **byte** <br/> Typically a single octet(one byte). This is an byte type.
2      | **int** <br/> The most natural size of integer for the machine.
3      | **float32** <br/> A single-precision floating point value.


Go programming language also allows to define various other types of variables such as Enumeration, Pointer, Array, Structure, and Union, which we will discuss in subsequent chapters. In this chapter, we will focus only basic variable types.

### Variable Definition in Go

A variable definition tells the compiler where and how much storage to create for the variable. A variable definition specifies a data type and contains a list of one or more variables of that type as follows −

```go
var variable_list optional_data_type;
```

Here, **optional_data_type** is a valid Go data type including byte, int, float32, complex64, boolean or any user-defined object, etc., and **variable_list** may consist of one or more identifier names separated by commas. Some valid declarations are shown here −

```go
var  i, j, k int;
var  c, ch byte;
var  f, salary float32;
d =  42;
```

The statement **“var i, j, k;”** declares and defines the variables i, j and k; which instructs the compiler to create variables named i, j, and k of type int.

Variables can be initialized (assigned an initial value) in their declaration. The type of variable is automatically judged by the compiler based on the value passed to it. The initializer consists of an equal sign followed by a constant expression as follows −

```go
variable_name = value;
```

For example,
```go
d = 3, f = 5;    // declaration of d and f. Here d and f are int 
```
For definition without an initializer: variables with static storage duration are implicitly initialized with nil (all bytes have the value 0); the initial value of all other variables is zero value of their data type.

### Static Type Declaration in Go
A static type variable declaration provides assurance to the compiler that there is one variable available with the given type and name so that the compiler can proceed for further compilation without requiring the complete detail of the variable. A variable declaration has its meaning at the time of compilation only, the compiler needs the actual variable declaration at the time of linking of the program.

**Example**

Try the following example, where the variable has been declared with a type and initialized inside the main function −

```go
package main

import "fmt"

func main() {
   var x float64
   x = 20.0
   fmt.Println(x)
   fmt.Printf("x is of type %T\n", x)
}
```

When the above code is compiled and executed, it produces the following result −

```go
20
x is of type float64
```

### Dynamic Type Declaration / Type Inference in Go

A dynamic type variable declaration requires the compiler to interpret the type of the variable based on the value passed to it. The compiler does not require a variable to have type statically as a necessary requirement.

**Example**

Try the following example, where the variables have been declared without any type. Notice, in case of type inference, we initialized the variable y with := operator, whereas x is initialized using = operator.

```go
package main

import "fmt"

func main() {
   var x float64 = 20.0

   y := 42 
   fmt.Println(x)
   fmt.Println(y)
   fmt.Printf("x is of type %T\n", x)
   fmt.Printf("y is of type %T\n", y)	
}
```
When the above code is compiled and executed, it produces the following result −

```go
20
42
x is of type float64
y is of type int
```

### Mixed Variable Declaration in Go

Variables of different types can be declared in one go using type inference.

**Example**

```go
package main

import "fmt"

func main() {
   var a, b, c = 3, 4, "foo"  
	
   fmt.Println(a)
   fmt.Println(b)
   fmt.Println(c)
   fmt.Printf("a is of type %T\n", a)
   fmt.Printf("b is of type %T\n", b)
   fmt.Printf("c is of type %T\n", c)
}
```

When the above code is compiled and executed, it produces the following result −

```go
3
4
foo
a is of type int
b is of type int
c is of type string
```

### The lvalues and the rvalues in Go

There are two kinds of expressions in Go −
- **lvalue** − Expressions that refer to a memory location is called "lvalue" expression. An lvalue may appear as either the left-hand or right-hand side of an assignment.

- **rvalue** − The term rvalue refers to a data value that is stored at some address in memory. An rvalue is an expression that cannot have a value assigned to it which means an rvalue may appear on the right- but not left-hand side of an assignment.

Variables are lvalues and so may appear on the left-hand side of an assignment. Numeric literals are rvalues and so may not be assigned and can not appear on the left-hand side.

The following statement is valid −

```go
x = 20.0
```

The following statement is not valid. It would generate compile-time error −

```go
10 = 20
```

