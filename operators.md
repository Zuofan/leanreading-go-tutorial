
## Go - 操作符

操作符告诉编译器，执行特定的数学计算或逻辑运算。Go语言内置丰富的操作符，如下所示 - 

- 算术操作符
- 关系操作符
- 按位操作符
- 赋值操作符
- 其它杂项运算符

下面按顺序进行说明：

### 算术操作符


下面的表项中包括了Go支持的所有的算术操作符。下面假定变量A的值为10，B的值为20 - 


操作符  |	示例说明
-------| -------------
+	| 两个操作数相加：A + B 结果： 30
-	| 第一个操作数减去第二个操作数：A - B 结果： -10
*	| 两个操作数相乘：A * B 结果： 200
/	| 被除数除以除数：  B / A 结果： 2
%	| 模操作符，结果为两数相除后的余数：	B % A 结果： 0
++	| 自增操作符，原操作数增加1：	A++ 结果： 11
--	| 自减操作符，原操作数减少1：	A-- 结果：  9

**实例**

```go
package main

import "fmt"

func main() {

   var a int = 21
   var b int = 10
   var c int

   c = a + b
   fmt.Printf("Line 1 - Value of c is %d\n", c )
   
   c = a - b
   fmt.Printf("Line 2 - Value of c is %d\n", c )
   
   c = a * b
   fmt.Printf("Line 3 - Value of c is %d\n", c )
   
   c = a / b
   fmt.Printf("Line 4 - Value of c is %d\n", c )
   
   c = a % b
   fmt.Printf("Line 5 - Value of c is %d\n", c )
   
   a++
   fmt.Printf("Line 6 - Value of a is %d\n", a )
   
   a--
   fmt.Printf("Line 7 - Value of a is %d\n", a )
}
```
编译执行后，输出如下 - 

```go
Line 1 - Value of c is 31
Line 2 - Value of c is 11
Line 3 - Value of c is 210
Line 4 - Value of c is 2
Line 5 - Value of c is 1
Line 6 - Value of a is 22
Line 7 - Value of a is 21
```

### 关系操作符

Go语言支持的逻辑操作符如下所示，示例假定A的值为10，B的值为20 -

操作符|	示例说明
-------| -------------
==	| 如果两个操作数相等，条件为真：(A == B) 结果为假
!=	| 如果两个操作数不相等，条件为真：(A ！= B) 结果为真
>	| 如果左边操作符大于右边操作符，条件为真：(A > B) 结果为假
<	| 如果左边操作符小于右边操作符，条件为真：(A < B) 结果为真
>=	| 如果左边操作符大于等于右边操作符，条件为真：(A >= B) 结果为假
<=	| 如果左边操作符小于等于右边操作符，条件为真：(A <= B) 结果为真

**实例**

```go
package main

import "fmt"

func main() {
   var a int = 21
   var b int = 10

   if( a == b ) {
      fmt.Printf("Line 1 - a is equal to b\n" )
   } else {
      fmt.Printf("Line 1 - a is not equal to b\n" )
   }
   if ( a < b ) {
      fmt.Printf("Line 2 - a is less than b\n" )
   } else {
      fmt.Printf("Line 2 - a is not less than b\n" )
   } 
   if ( a > b ) {
      fmt.Printf("Line 3 - a is greater than b\n" )
   } else {
      fmt.Printf("Line 3 - a is not greater than b\n" )
   }
   
   /* Lets change value of a and b */
   a = 5
   b = 20
   if ( a <= b ) {
      fmt.Printf("Line 4 - a is either less than or equal to  b\n" )
   }
   if ( b >= a ) {
      fmt.Printf("Line 5 - b is either greater than  or equal to b\n" )
   }
}
```

编译并执行，输出如下 -

```go
Line 1 - a is not equal to b
Line 2 - a is not less than b
Line 3 - a is greater than b
Line 4 - a is either less than or equal to  b
Line 5 - b is either greater than  or equal to b
```

### 逻辑操作符

Go语言支持的逻辑操作符如下所示，示例假定A的值为true，B的值为false -

操作符   | 	示例说明
------- | -------------
&&	    | 逻辑与操作，如果两个操作数非零，条件为真：(A && B) 结果为假
\|\|	| 逻辑或操作，如果两个操作数至少有一个非零，条件为真：(A || B) 结果为真
!	    | 逻辑非操作，原操作数值取反：!(A && B) 结果为真

**实例**

```go
package main

import "fmt"

func main() {
   var a bool = true
   var b bool = false
   if ( a && b ) {
      fmt.Printf("Line 1 - Condition is true\n" )
   }
   if ( a || b ) {
      fmt.Printf("Line 2 - Condition is true\n" )
   }
   
   /* lets change the value of  a and b */
   a = false
   b = true
   if ( a && b ) {
      fmt.Printf("Line 3 - Condition is true\n" )
   } else {
      fmt.Printf("Line 3 - Condition is not true\n" )
   }
   if ( !(a && b) ) {
      fmt.Printf("Line 4 - Condition is true\n" )
   }
}
```

编译并执行，输出如下 -

```go
Line 2 - Condition is true
Line 3 - Condition is not true
Line 4 - Condition is true
```


### 按位操作符

按位操作符表示对每一bit位执行对应的操作，下面是按位操作的真值表 - 
p	| q	| p & q	| p \| q| 	p ^ q
----|---| ------| ------|-------
0	|0	|0|	0	|0
0	|1|	0	|1|	1
1	|1	|1|	1	|0
1	|0|	0	|1|	1

假设 A = 60， B = 13，二进制表示如下所示 −

A = 0011 1100

B = 0000 1101

-----------------

A`&`B = 0000 1100

A`|`B = 0011 1101

A`^`B = 0011 0001

`~`A  = 1100 0011

支持的按位操作符如下所示，示例假定A的值为60，B的值为13 -


操作符 | 	示例说明
-------| -------------
&	| 二进制按位与操作符：(A & B) 结果为： 12，二进制表示为： 0000 1100
\|	| 二进制按位或操作符：(A | B) 结果为： 61，二进制表示为： 0011 1101
^	| 二进制按位异或操作符：(A ^ B) 结果为： 49，二进制表示为： 0011 0001 
<<	| 左移操作符：(A << 2) 结果为： 240，二进制表示为： 1111 0000
>>	| 右移操作符：(A >> 2) 结果为： 15， 二进制表示为： 0000 1111

**实例**

```go
package main

import "fmt"

func main() {
   var a uint = 60	/* 60 = 0011 1100 */  
   var b uint = 13	/* 13 = 0000 1101 */
   var c uint = 0          

   c = a & b       /* 12 = 0000 1100 */ 
   fmt.Printf("Line 1 - Value of c is %d\n", c )

   c = a | b       /* 61 = 0011 1101 */
   fmt.Printf("Line 2 - Value of c is %d\n", c )

   c = a ^ b       /* 49 = 0011 0001 */
   fmt.Printf("Line 3 - Value of c is %d\n", c )

   c = a << 2     /* 240 = 1111 0000 */
   fmt.Printf("Line 4 - Value of c is %d\n", c )

   c = a >> 2     /* 15 = 0000 1111 */
   fmt.Printf("Line 5 - Value of c is %d\n", c )
}
```

编译并执行，输出如下 -

```go
Line 1 - Value of c is 12
Line 2 - Value of c is 61
Line 3 - Value of c is 49
Line 4 - Value of c is 240
Line 5 - Value of c is 15
```


### 赋值运算符

下面列出的是Go语言支持的所有赋值运算符 −

操作符 | 	示例说明
-------| -------------
=	 |  赋值运算符，表示右边的操作数的值赋给左边的操作数：	C = A + B 表示将 A + B 的和赋值给 C
+=	 | 加并且赋值运算符，表示首先将左边的操作数加上右边的操作数，然后将结果赋值到左边的操作数上：	C += A 效果等同于 C = C + A
-=	 | 减并且赋值运算符，表示首先将左边的操作数减去右边的操作数，然后将结果赋值到左边的操作数上： C -= A 效果等同于 C = C - A
*=	 | 乘并且赋值运算符，表示首先将左边的操作数乘以右边的操作数，然后将结果赋值到左边的操作数上： C *= A 效果等同于 C = C * A
/=	 | 除并且赋值运算符，表示首先将左边的操作数除以右边的操作数，然后将结果赋值到左边的操作数上： C /= A 效果等同于 C = C / A
%=	 | 模运算并且赋值运算符，表示首先将左边的操作数和右边的操作数进行模运算，然后将结果赋值到左边的操作数上：C %= A  效果等同于 C = C % A
<<=	 | 左移并且赋值运算符，表示首先将左边的操作数左移相应右边操作数的位数，然后将结果赋值到左边的操作数上：	C <<= 2 效果等同于 C = C << 2
>>=	 | 右移并且赋值运算符，表示首先将左边的操作数右移相应右边操作数的位数，然后将结果赋值到左边的操作数上：	C >>= 2 效果等同于 C = C >> 2
&=	 | 按位与，并执行赋值运算符，表示首先将左边的操作数和右边操作数进行按位并操作，然后将结果赋值到左边的操作数上：	C &= 2 效果等同于 C = C & 2
^=	 | 按位异或，并执行赋值运算符，表示首先将左边的操作数和右边操作数进行按位异或操作，然后将结果赋值到左边的操作数上：	C ^= 2 效果等同于 C = C ^ 2
\|=	 | 按位或，并执行赋值运算符，表示首先将左边的操作数和右边操作数进行按位或操作，然后将结果赋值到左边的操作数上：		C |= 2 效果等同于 C = C | 2


**实例**
```go
package main

import "fmt"

func main() {
   var a int = 21
   var c int

   c =  a
   fmt.Printf("Line 1 - =  Operator Example, Value of c = %d\n", c )

   c +=  a
   fmt.Printf("Line 2 - += Operator Example, Value of c = %d\n", c )

   c -=  a
   fmt.Printf("Line 3 - -= Operator Example, Value of c = %d\n", c )

   c *=  a
   fmt.Printf("Line 4 - *= Operator Example, Value of c = %d\n", c )

   c /=  a
   fmt.Printf("Line 5 - /= Operator Example, Value of c = %d\n", c )

   c  = 200; 

   c <<=  2
   fmt.Printf("Line 6 - <<= Operator Example, Value of c = %d\n", c )

   c >>=  2
   fmt.Printf("Line 7 - >>= Operator Example, Value of c = %d\n", c )

   c &=  2
   fmt.Printf("Line 8 - &= Operator Example, Value of c = %d\n", c )

   c ^=  2
   fmt.Printf("Line 9 - ^= Operator Example, Value of c = %d\n", c )

   c |=  2
   fmt.Printf("Line 10 - |= Operator Example, Value of c = %d\n", c )
}
```

编译并执行，输出如下 -

```go
Line 1 - =  Operator Example, Value of c = 21
Line 2 - += Operator Example, Value of c = 42
Line 3 - -= Operator Example, Value of c = 21
Line 4 - *= Operator Example, Value of c = 441
Line 5 - /= Operator Example, Value of c = 21
Line 6 - <<= Operator Example, Value of c = 800
Line 7 - >>= Operator Example, Value of c = 200
Line 8 - &= Operator Example, Value of c = 0
Line 9 - ^= Operator Example, Value of c = 2
Line 10 - |= Operator Example, Value of c = 2
```

### 其它操作符

下面是一些其它Go语言支持的重要操作符 - 

操作符 | 	示例说明
-------| -------------
&	 | 返回一个变量的地址：	&a 表明返回变量a的实际存储地址
*	 | 指向一个变量的指针： *a 反引用，代表一个指针所指向的值

**实例**

```go
package main

import "fmt"

func main() {
   var a int = 4
   var b int32
   var c float32
   var ptr *int

   /* example of type operator */
   fmt.Printf("Line 1 - Type of variable a = %T\n", a );
   fmt.Printf("Line 2 - Type of variable b = %T\n", b );
   fmt.Printf("Line 3 - Type of variable c= %T\n", c );

   /* example of & and * operators */
   ptr = &a	/* 'ptr' now contains the address of 'a'*/
   fmt.Printf("value of a is  %d\n", a);
   fmt.Printf("*ptr is %d.\n", *ptr);
}
```

编译并执行，输出如下 -

```go
Line 1 - Type of variable a = int
Line 2 - Type of variable b = int32
Line 3 - Type of variable c= float32
value of a is  4
*ptr is 4.
```

### 操作符优先级

操作符优先级决定了一个表达式如何被分组执行，一些操作符高于另外一些操作符，比如乘操作符高于加操作符。

在`x = 7 + 3 * 2`例子中，x被赋值为13，而非20。因为`*`操作符的优先级高于`+`操作符，所以先执行`3*2`，然后和7，执行了加法操作。

在下表中，优先级越高的操作符被放在表的前列，越低的优先级，放在底部。在一个表达式中，优先级越高的运算符首先被执行。



分类           | 	操作符               | 	结合性
--------------| -----------------------|-------------
后缀  	       | () [] -> . ++ - -	   | 由左到右
一元运算	    | + - ! ~ ++ - - (type)* & sizeof	 | 由右到左
倍乘类         | 	* / %	           | 由左到右
加法类         | 	+ -	               | 由左到右
移位          | 	<< >>	           | 由左到右
关系          | 	< <= > >=	       | 由左到右
相同          | 	== !=	           | 由左到右
按位与        | 	&	               | 由左到右
按位异或      | 	^	               | 由左到右
按位或        | 	\|	               | 由左到右
逻辑与        | 	&&	               | 由左到右
逻辑或        | 	\|\|	            | 由左到右
赋值          | 	= += -= *= /= %=>>= <<= &= ^= \|=	 | 由右到左
逗号          | 	,	                | 由左到右

**实例**

```go
package main

import "fmt"

func main() {
   var a int = 20
   var b int = 10
   var c int = 15
   var d int = 5
   var e int;

   e = (a + b) * c / d;      // ( 30 * 15 ) / 5
   fmt.Printf("Value of (a + b) * c / d is : %d\n",  e );

   e = ((a + b) * c) / d;    // (30 * 15 ) / 5
   fmt.Printf("Value of ((a + b) * c) / d is  : %d\n" ,  e );

   e = (a + b) * (c / d);   // (30) * (15/5)
   fmt.Printf("Value of (a + b) * (c / d) is  : %d\n",  e );

   e = a + (b * c) / d;     //  20 + (150/5)
   fmt.Printf("Value of a + (b * c) / d is  : %d\n" ,  e );  
}
```

编译并执行，输出如下 -

```go
Value of (a + b) * c / d is : 90
Value of ((a + b) * c) / d is  : 90
Value of (a + b) * (c / d) is  : 90
Value of a + (b * c) / d is  : 50
```

## 原文 [Go - Operators](https://www.tutorialspoint.com/go/go_operators.htm)

An operator is a symbol that tells the compiler to perform specific mathematical or logical manipulations. Go language is rich in built-in operators and provides the following types of operators −

- Arithmetic Operators
- Relational Operators
- Logical Operators
- Bitwise Operators
- Assignment Operators
- Miscellaneous Operators

This tutorial explains arithmetic, relational, logical, bitwise, assignment, and other operators one by one.

### Arithmetic Operators

Following table shows all the arithmetic operators supported by Go language. Assume variable A holds 10 and variable B holds 20 then −



Operator|	Description	Example
-------| -------------
+	| Adds two operands	A + B gives 30
-	| Subtracts second operand from the first	A - B gives -10
*	| Multiplies both operands	A * B gives 200
/	| Divides the numerator by the denominator.	B / A gives 2
%	| Modulus operator; gives the remainder after an integer division.	B % A gives 0
++	| Increment operator. It increases the integer value by one.	A++ gives 11
--	| Decrement operator. It decreases the integer value by one.	A-- gives 9

**Examples**

### Relational Operators

The following table lists all the relational operators supported by Go language. Assume variable A holds 10 and variable B holds 20, then −

**Examples**

Operator|	Description	Example
-------| -------------
==	| It checks if the values of two operands are equal or not; if yes, the condition becomes true.	(A == B) is not true.
!=	| It checks if the values of two operands are equal or not; if the values are not equal, then the condition becomes true.	(A != B) is true.
>	| It checks if the value of left operand is greater than the value of right operand; if yes, the condition becomes true.	(A > B) is not true.
<	| It checks if the value of left operand is less than the value of the right operand; if yes, the condition becomes true.	(A < B) is true.
>=	| It checks if the value of the left operand is greater than or equal to the value of the right operand; if yes, the condition becomes true.	(A >= B) is not true.
<=	| It checks if the value of left operand is less than or equal to the value of right operand; if yes, the condition becomes true.	(A <= B) is true.


### Logical Operators

The following table lists all the logical operators supported by Go language. Assume variable A holds 1 and variable B holds 0, then −

**Examples**

Operator| 	Description	Example
-------| -------------
&&	| Called Logical AND operator. If both the operands are non-zero, then condition becomes true.	(A && B) is false.
\|\|	| Called Logical OR Operator. If any of the two operands is non-zero, then condition becomes true.	(A || B) is true.
!	| Called Logical NOT Operator. Use to reverses the logical state of its operand. If a condition is true then Logical NOT operator will make false.	!(A && B) is true.

The following table shows all the logical operators supported by Go language. Assume variable A holds true and variable B holds false, then −

Operator| 	Description	Example
-------| -------------
&& | 	Called Logical AND operator. If both the operands are false, then the condition becomes false.	(A && B) is false.
\|\|	| Called Logical OR Operator. If any of the two operands is true, then the condition becomes true.	(A || B) is true.
!	| Called Logical NOT Operator. Use to reverses the logical state of its operand. If a condition is true, then Logical NOT operator will make it false.	!(A && B) is true.

### Bitwise Operators

Bitwise operators work on bits and perform bit-by-bit operation. The truth tables for &, |, and ^ are as follows −

p	| q	| p & q	| p \| q| 	p ^ q
----|---| ------| ------|-------
0	|0	|0|	0	|0
0	|1|	0	|1|	1
1	|1	|1|	1	|0
1	|0|	0	|1|	1

Assume A = 60; and B = 13. In binary format, they will be as follows −

A = 0011 1100

B = 0000 1101

-----------------

A&B = 0000 1100

A|B = 0011 1101

A^B = 0011 0001

~A  = 1100 0011

The Bitwise operators supported by C language are listed in the following table. Assume variable A holds 60 and variable B holds 13, then −

**Examples**

Operator| 	Description	Example
-------| -------------
&	| Binary AND Operator copies a bit to the result if it exists in both operands.	(A & B) will give 12, which is 0000 1100
\|	| Binary OR Operator copies a bit if it exists in either operand.	(A | B) will give 61, which is 0011 1101
^	| Binary XOR Operator copies the bit if it is set in one operand but not both.	(A ^ B) will give 49, which is 0011 0001
<<	| Binary Left Shift Operator. The left operands value is moved left by the number of bits specified by the right operand.	A << 2 will give 240 which is 1111 0000
>>	| Binary Right Shift Operator. The left operands value is moved right by the number of bits specified by the right operand.	A >> 2 will give 15 which is 0000 1111

### Assignment Operators

The following table lists all the assignment operators supported by Go language −

**Examples**

Operator | 	Description	Example
-------| -------------
=	 | Simple assignment operator, Assigns values from right side operands to left side operand	C = A + B will assign value of A + B into C
+=	 | Add AND assignment operator, It adds right operand to the left operand and assign the result to left operand	C += A is equivalent to C = C + A
-=	 | Subtract AND assignment operator, It subtracts right operand from the left operand and assign the result to left operand	C -= A is equivalent to C = C - A
*=	 | Multiply AND assignment operator, It multiplies right operand with the left operand and assign the result to left operand	C *= A is equivalent to C = C * A
/=	 | Divide AND assignment operator, It divides left operand with the right operand and assign the result to left operand	C /= A is equivalent to C = C / A
%=	 | Modulus AND assignment operator, It takes modulus using two operands and assign the result to left operand	C %= A is equivalent to C = C % A
<<=	 | Left shift AND assignment operator	C <<= 2 is same as C = C << 2
>>=	 | Right shift AND assignment operator	C >>= 2 is same as C = C >> 2
&=	 | Bitwise AND assignment operator	C &= 2 is same as C = C & 2
^=	 | bitwise exclusive OR and assignment operator	C ^= 2 is same as C = C ^ 2
\|=	 | bitwise inclusive OR and assignment operator	C |= 2 is same as C = C | 2

### Miscellaneous Operators

There are a few other important operators supported by Go Language including sizeof and ?:.

**Examples**

Operator | 	Description	Example
-------| -------------
&	 | Returns the address of a variable.	&a; provides actual address of the variable.
*	 | Pointer to a variable.	*a; provides pointer to a variable.

### Operators Precedence in Go

Operator precedence determines the grouping of terms in an expression. This affects how an expression is evaluated. Certain operators have higher precedence than others; for example, the multiplication operator has higher precedence than the addition operator.

For example x = 7 + 3 * 2; here, x is assigned 13, not 20 because operator * has higher precedence than +, so it first gets multiplied with 3*2 and then adds into 7.

Here, operators with the highest precedence appear at the top of the table, those with the lowest appear at the bottom. Within an expression, higher precedence operators will be evaluated first.

**Examples**

Category | 	Operator | 	Associativity
-------| -----------|-------------
Postfix	 | () [] -> . ++ - -	 | Left to right
Unary	 | + - ! ~ ++ - - (type)* & sizeof	 | Right to left
Multiplicative | 	* / %	 | Left to right
Additive | 	+ -	 | Left to right
Shift | 	<< >>	 | Left to right
Relational | 	< <= > >=	 | Left to right
Equality | 	== !=	 | Left to right
Bitwise AND | 	&	 | Left to right
Bitwise XOR | 	^	 | Left to right
Bitwise OR | 	\|	 | Left to right
Logical AND | 	&&	 | Left to right
Logical OR | 	\|\|	 | Left to right
Assignment | 	= += -= *= /= %=>>= <<= &= ^= \|=	 | Right to left
Comma | 	,	 | Left to right