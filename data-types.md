
## Go - 数据类型

在 Go 编程语言中，数据类型是涉及到声明不同类型的变量或函数。变量的数据类型关系到占有多少空间，这些空间中的比特位是如何解释的。[^1]

数据类型可以被分为以下几种 - 

序号 | 类型及描述
-------| -------------
1      | **Boolean types** <br/>布尔类型，包括两个预定义的常量：`true`和`false`
2      | **Numeric types** <br/>数值类型，包括整数类型和浮点类型
3      | **String types** <br/> 字符串数据类型。字符串数据类型由字节序列组成。字符串一旦创建，其内容就不可更改。预定义的字符串类型是——`string`
4      | **Derived types** <br/> 包括 (a) 指针类型（`Pointer types`）、(b) 数组类型（`Array types`）、(c) 结构体类型（`Structure types`）、(d) 联合体类型（`Union types`）、(e)函数类型（`Function types`）、f) 切片类型（`Slice types`）、 g) 接口类型（`Interface types`）、 h) 键值对类型（`Map types`）、 i) 管道类型（`Channel Types`）


数组类型和结构类型统称为复合数据类型。函数类型是由参数和返回类型共同决定的一种数据类型。下面讨论基本数据类型，其它数据类型在接下来的章节讨论。

### 整数类型

下面是预先定义的，平台独立的整数类型 - 

序号 | 类型及描述
-------| -------------
1      | **uint8** <br/>无符号的8位整数，范围为(0 to 255)
2      | **uint16** <br/>无符号的16位整数，范围为(0 to 65535)
3      | **uint32** <br/> 无符号的32位整数，范围为(0 to 4294967295)
4      | **uint64** <br/> 无符号的64位整数，范围为(0 to 18446744073709551615)
5      | **int8** <br/> 有符号的8位整数，范围为 (-128 to 127)
6      | **int16** <br/>有符号的16位整数，范围为 (-32768 to 32767)
7      | **int32** <br/>有符号的32位整数，范围为 (-2147483648 to 2147483647)
8      | **int64** <br/>有符号的64位整数，范围为 (-9223372036854775808 to 9223372036854775807)

### 浮点类型

下面是预先定义的，平台独立的浮点类型 - 

序号 | 类型及描述
-------| -------------
1      | **float32** <br/> 遵循IEEE-754标准， 32位浮点类型
2      | **float64** <br/> 遵循IEEE-754标准， 64位浮点类型
3      | **complex64** <br/> 以`float32`做为实部和虚部的复数类型
4      | **complex128** <br/> 以`float64`做为实部和虚部的复数类型


### 其它整型

其它特定实现相关的数值类型 - 

序号 | 类型及描述
-------| -------------
1      | **byte** <br/> 长度同于`uint8`类型
2      | **rune** <br/> 长度同于`int32`类型
3      | **uint** <br/> 依赖具体平台，长度为32位或64位
4      | **int** <br/> 长度同于`uint`
5     | **uintptr** <br/> 用于存放一个指针值的无符号整数类型

[^1]: 比如整数类型——`int`和浮点类型，比如`float`，他们在`C语言`中，虽然都是32位，但系统如何对这个数据的解释，是不一样。

## 原文 [Go - Data Types](https://www.tutorialspoint.com/go/go_data_types.htm) 
In the Go programming language, data types refer to an extensive system used for declaring variables or functions of different types. The type of a variable determines how much space it occupies in storage and how the bit pattern stored is interpreted.

The types in Go can be classified as follows −

Sr.No. | Types and Description
-------| -------------
1      | **Boolean types** <br/>They are boolean types and consists of the two predefined constants: (a) true (b) false
2      | **Numeric types** <br/> They are again arithmetic types and they represents a) integer types or b) floating point values throughout the program.
3      | **String types** <br/> A string type represents the set of string values. Its value is a sequence of bytes. Strings are immutable types that is once created, it is not possible to change the contents of a string. The predeclared string type is string.
4      | **Derived types** <br/> They include (a) Pointer types, (b) Array types, (c) Structure types, (d) Union types and (e) Function types f) Slice types g) Interface types h) Map types i) Channel Types


Array types and structure types are collectively referred to as aggregate types. The type of a function specifies the set of all functions with the same parameter and result types. We will discuss the basic types in the following section, whereas other types will be covered in the upcoming chapters.

### Integer Types

The predefined architecture-independent integer types are −

Sr.No. | Types and Description
-------| -------------
1      | **uint8** <br/>Unsigned 8-bit integers (0 to 255)
2      | **uint16** <br/> Unsigned 16-bit integers (0 to 65535)
3      | **uint32** <br/> Unsigned 32-bit integers (0 to 4294967295)
4      | **uint64** <br/> Unsigned 64-bit integers (0 to 18446744073709551615)
5      | **int8** <br/> Signed 8-bit integers (-128 to 127)
6      | **int16** <br/>Signed 16-bit integers (-32768 to 32767)
7      | **int32** <br/>Signed 32-bit integers (-2147483648 to 2147483647)
8      | **int64** <br/>Signed 64-bit integers (-9223372036854775808 to 9223372036854775807)



### Floating Types

The predefined architecture-independent float types are −

Sr.No. | Types and Description
-------| -------------
1      | **float32** <br/> IEEE-754 32-bit floating-point numbers
2      | **float64** <br/> IEEE-754 64-bit floating-point numbers
3      | **complex64** <br/> Complex numbers with float32 real and imaginary parts
4      | **complex128** <br/> Complex numbers with float64 real and imaginary parts


The value of an n-bit integer is n bits and is represented using two's complement arithmetic operations.

### Other Numeric Types

There is also a set of numeric types with implementation-specific sizes −


Sr.No. | Types and Description
-------| -------------
1      | **byte** <br/> same as uint8
2      | **rune** <br/> same as int32
3      | **uint** <br/> 32 or 64 bits
4      | **int** <br/> same size as uint
5     | **uintptr** <br/> an unsigned integer to store the uninterpreted bits of a pointer value
