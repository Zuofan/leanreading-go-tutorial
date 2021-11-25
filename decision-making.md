
## Go - 选择结构

选择结构是由一个或多个需要被求真值的条件，和在条件为真的情况下需要执行的语句；另外，还有一个可选的，当条件为假的时候需要执行的语句。

下图是一个通常我们在大多数编程语言中看到的选择结构 - 

![decision_making](/assets/decision_making.jpg)

Go 编程语言支持下列选择结构，如下表所示 - 

序号	 | 语句 & 说明
--------|-------------------
1	    | if statement<br />`if`语句由一个布尔表达式，以及一个或多个语句所组成
2	    | if...else statement<br />`if`语句跟着一个可选的`else`语句，如果条件表达式为假，`else`语句将会执行
3	| 嵌套的 if statements<br />可以将`if`或者`else if`语句嵌套在`if` 或`else if`语句中
4	| switch statement<br />`switch`语句可以将要比较的变量，和一系列值进行比较
5	| select statement<br />`select`语句和`switch`语句类似，不过待比较的项和管道操作相关


### `if statement`

`if`语句由一个布尔表达式后跟一个或多个语句组成。

**语法**

`if statement`语法如下 −
```go
if boolean_expression  {
   /* statement(s) will execute if the boolean expression is true */
}
```
如果布尔表达式为真，`if`语句块将被执行；如果为假，将会跳过`if`语句块，转而直接执行`if`语句块后的代码。

**流程图**

![if_statement](/assets/if_statement.jpg)

**实例**

```go
package main

import "fmt"

func main() {
   /* local variable definition */
   var a int = 10
 
   /* check the boolean condition using if statement */
   if a < 20  {
      /* if condition is true then print the following */
      fmt.Printf("a is less than 20\n" )
   }
   fmt.Printf("value of a is : %d\n", a)
}
```

编译并执行，输出如下所示 −

```go
a is less than 20;
value of a is : 10
```

### `if...else statement`

`if`语句后可接一个可选的`else`语句，如果布尔表达式为假时，`else`语句将被执行。

**语法**

`if...else`语句语法如下所示 −

```go
if boolean_expression {
   /* statement(s) will execute if the boolean expression is true */
} else {
   /* statement(s) will execute if the boolean expression is false */
}
```
布尔表达式为真，`if`语句块将被执行，否则`else`语句块将被执行。

**流程图**

![if_else_statement](/assets/if_else_statement.jpg)

**实例**

```go
package main

import "fmt"

func main() {
   /* local variable definition */
   var a int = 100;
 
   /* check the boolean condition */
   if a < 20  {
      /* if condition is true then print the following */
      fmt.Printf("a is less than 20\n" );
   } else {
      /* if condition is false then print the following */
      fmt.Printf("a is not less than 20\n" );
   }
   fmt.Printf("value of a is : %d\n", a);
}
```

编译并执行，输出如下所示 −

```go
a is not less than 20;
value of a is : 100
```

**The if...else if...else Statement**

`if`语句可以后接一个可选的`else if...else`语句，这种类型的结构可以很方便的用来对多个条件进行测试。

使用此结构，需要注意以下几个方面 −

`if`语句后可以不接`else`语句，或者接一个`else`语句，并且`else`语句只能跟在`else if`语句后面。

`if`语句可以接零个，或多个`else if`语句，`else if`语句必须在`else`语句前面。

一旦匹配上`else if`语句，剩余的条件将不会验证。

**语法**

此类语法的结构如下 - 

```go
if(boolean_expression 1) {
   /* Executes when the boolean expression 1 is true */
} else if( boolean_expression 2) {
   /* Executes when the boolean expression 2 is true */
} else if( boolean_expression 3) {
   /* Executes when the boolean expression 3 is true */
} else {
   /* executes when the none of the above condition is true */
}
```

**实例**

```go
package main

import "fmt"

func main() {
   /* local variable definition */
   var a int = 100
 
   /* check the boolean condition */
   if( a == 10 ) {
      /* if condition is true then print the following */
      fmt.Printf("Value of a is 10\n" )
   } else if( a == 20 ) {
      /* if else if condition is true */
      fmt.Printf("Value of a is 20\n" )
   } else if( a == 30 ) {
      /* if else if condition is true  */
      fmt.Printf("Value of a is 30\n" )
   } else {
      /* if none of the conditions is true */
      fmt.Printf("None of the values is matching\n" )
   }
   fmt.Printf("Exact value of a is: %d\n", a )
}
```

编译并执行，输出如下所示 −

```go
None of the values is matching
Exact value of a is: 100
```

### 嵌套的`if statements`

`if...else`语句可以进行嵌套——将`if`语句或`else`语句嵌套放在其它`if`语句或者`else if`语句中。

**语法**

语法结构如下 −

if( boolean_expression 1) {
   /* Executes when the boolean expression 1 is true */
   if(boolean_expression 2) {
      /* Executes when the boolean expression 2 is true */
   }
}

也可以仿效`if`语句，进行嵌套`else if...else`语句。

**实例**

```go
package main

import "fmt"

func main() {
   /* local variable definition */
   var a int = 100
   var b int = 200
 
   /* check the boolean condition */
   if( a == 100 ) {
      /* if condition is true then check the following */
      if( b == 200 )  {
         /* if condition is true then print the following */
         fmt.Printf("Value of a is 100 and b is 200\n" );
      }
   }
   fmt.Printf("Exact value of a is : %d\n", a );
   fmt.Printf("Exact value of b is : %d\n", b );
}
```

编译并执行，输出如下所示 −

```go
Value of a is 100 and b is 200
Exact value of a is : 100
Exact value of b is : 200
```

### `switch statement`

`switch`语句可以将一个变量值和一系列的`case`值进行相等比较。
在Go中，`switch`语句有两种类型 - 

In Go programming, switch statements are of two types −

- **Expression Switch** − 在此类型中，`case`包含表达式，此表达式的值和`switch`的表达式值进行比较。

- **Type Switch** − 在此类型中，`case`包含类型，此类型和`switch`的类型进行比较。

**Expression Switch**

语法结构如下 −

```go
switch(boolean-expression or integral type){
   case boolean-expression or integral type :
      statement(s);      
   case boolean-expression or integral type :
      statement(s); 
   
   /* you can have any number of case statements */
   default : /* Optional */
      statement(s);
}
```

`switch`语句遵循如下规则 - 

- `switch`语句包含的表达式包含整型值，或者一个布尔表达式，或者是一个具备转换为整型值或布尔值函数的类类型。如果`switch`语句的表达式为空时，取默认值为真。

- 可以包含任意数目的`case`语句，每一`case`语句都包含待比较的值以及一个分号。

- `case`是一个常量表达式，其数据类型需要和switch待比较的变量一致：或者为常量或字面量。

- 当比较匹配成果时，`case`接的语句会被执行，`case`语句中无需任何`break`语句。

- `switch`语句包含一个可选的——`default case`，它在所有的`case`语句之后。`default case`可以用于执行没有任何`case`语句为真的情况。`default case`无需任何`break`语句。

**流程图**


![switch_statement](/assets/switch_statement.jpg)


**实例**

```go
package main

import "fmt"

func main() {
   /* local variable definition */
   var grade string = "B"
   var marks int = 90

   switch marks {
      case 90: grade = "A"
      case 80: grade = "B"
      case 50,60,70 : grade = "C"
      default: grade = "D"  
   }
   switch {
      case grade == "A" :
         fmt.Printf("Excellent!\n" )     
      case grade == "B", grade == "C" :
         fmt.Printf("Well done\n" )      
      case grade == "D" :
         fmt.Printf("You passed\n" )      
      case grade == "F":
         fmt.Printf("Better try again\n" )
      default:
         fmt.Printf("Invalid grade\n" );
   }
   fmt.Printf("Your grade is  %s\n", grade );      
}
```

编译并执行，输出如下所示 −

```go
Excellent!
Your grade is  A
```

**Type Switch**

语法结构如下 −

```go
switch x.(type){
   case type:
      statement(s);      
   case type:
      statement(s); 
   /* you can have any number of case statements */
   default: /* Optional */
      statement(s);
}
```

此类型的应用规则如下 −

- 待比较的`switch`语句的表达式必须具备接口类型的变量。

- 可以包含任意数目的`case`语句，每一`case`语句都包含待比较的值以及一个分号。

- `case`包含的类型需要和待比较的变量类型一致，且是一个有效类型。

- 当比较匹配成果时，`case`接的语句会被执行，`case`语句中无需任何`break`语句。

- `switch`语句包含一个可选的——`default case`，它在所有的`case`语句之后。`default case`可以用于执行没有任何`case`语句为真的情况。`default case`无需任何`break`语句。


**实例**

```go
package main

import "fmt"

func main() {
   var x interface{}
     
   switch i := x.(type) {
      case nil:	  
         fmt.Printf("type of x :%T",i)                
      case int:	  
         fmt.Printf("x is int")                       
      case float64:
         fmt.Printf("x is float64")           
      case func(int) float64:
         fmt.Printf("x is func(int)")                      
      case bool, string:
         fmt.Printf("x is bool or string")       
      default:
         fmt.Printf("don't know the type")     
   }   
}
```

编译并执行，输出如下所示 −

```go
type of x :<nil>
```

### select statement

`select`语法结构如下 −

```go
select {
   case communication clause  :
      statement(s);      
   case communication clause  :
      statement(s); 
   /* you can have any number of case statements */
   default : /* Optional */
      statement(s);
}
```

`select`语句的使用规则如下 −

- `select`语句可以包含任意数目的`case`语句，每一`case`语句都包含待比较的值以及一个分号。

- `case`的类型必须是通信管道操作类型。

- 当管道操作的`case`语句发生，后接的语句会被执行，`case`语句中无需任何`break`语句。

- `select`语句包含一个可选的——`default case`，它在所有的`case`语句之后。`default case`可以用于执行没有任何`case`语句为真的情况。`default case`无需任何`break`语句。

**实例**

```go
package main

import "fmt"

func main() {
   var c1, c2, c3 chan int
   var i1, i2 int
   select {
      case i1 = <-c1:
         fmt.Printf("received ", i1, " from c1\n")
      case c2 <- i2:
         fmt.Printf("sent ", i2, " to c2\n")
      case i3, ok := (<-c3):  // same as: i3, ok := <-c3
         if ok {
            fmt.Printf("received ", i3, " from c3\n")
         } else {
            fmt.Printf("c3 is closed\n")
         }
      default:
         fmt.Printf("no communication\n")
   }    
}   
```

编译并执行，输出如下所示 −

```go
no communication
```

## 原文 [Go - Decision Making](https://www.tutorialspoint.com/go/go_decision_making.htm)


Decision making structures require that the programmer specify one or more conditions to be evaluated or tested by the program, along with a statement or statements to be executed if the condition is determined to be true, and optionally, other statements to be executed if the condition is determined to be false.

Following is the general form of a typical decision making structure found in most of the programming languages −

![decision_making](/assets/decision_making.jpg)

Go programming language provides the following types of decision making statements. Click the following links to check their detail.

Sr.No	| Statement & Description
--------|-------------------
1	| if statement<br />An if statement consists of a boolean expression followed by one or more statements.
2	| if...else statement<br />An if statement can be followed by an optional else statement, which executes when the boolean expression is false.
3	| nested if statements<br />You can use one if or else if statement inside another if or else if statement(s).
4	| switch statement<br />A switch statement allows a variable to be tested for equality against a list of values.
5	| select statement<br />A select statement is similar to switch statement with difference that case statements refers to channel communications.


### if statement

An if statement consists of a boolean expression followed by one or more statements.

**Syntax**

The syntax of an if statement in Go programming language is −
```go
if(boolean_expression) {
   /* statement(s) will execute if the boolean expression is true */
}
```
If the boolean expression evaluates to true, then the block of code inside the if statement is executed. If boolean expression evaluates to false, then the first set of code after the end of the if statement (after the closing curly brace) is executed.

**Flow Diagram**

![if_statement](/assets/if_statement.jpg)

```go
package main

import "fmt"

func main() {
   /* local variable definition */
   var a int = 10
 
   /* check the boolean condition using if statement */
   if( a < 20 ) {
      /* if condition is true then print the following */
      fmt.Printf("a is less than 20\n" )
   }
   fmt.Printf("value of a is : %d\n", a)
}
```

When the above code is compiled and executed, it produces the following result −

```go
a is less than 20;
value of a is : 10
```

### if...else statement

An if statement can be followed by an optional else statement, which executes when the boolean expression is false.

**Syntax**

The syntax of an if...else statement in Go programming language is −

```go
if(boolean_expression) {
   /* statement(s) will execute if the boolean expression is true */
} else {
   /* statement(s) will execute if the boolean expression is false */
}
```
If the boolean expression evaluates to true, then the if block of code will be executed, otherwise else block of code is executed.

**Flow Diagram**

![if_else_statement](/assets/if_else_statement.jpg)

```go
package main

import "fmt"

func main() {
   /* local variable definition */
   var a int = 100;
 
   /* check the boolean condition */
   if( a < 20 ) {
      /* if condition is true then print the following */
      fmt.Printf("a is less than 20\n" );
   } else {
      /* if condition is false then print the following */
      fmt.Printf("a is not less than 20\n" );
   }
   fmt.Printf("value of a is : %d\n", a);
}
```

When the above code is compiled and executed, it produces the following result −

```go
a is not less than 20;
value of a is : 100
```

**The if...else if...else Statement**

An if statement can be followed by an optional else if...else statement, which is very useful to test various conditions using single if...else if statement.

When using if , else if , else statements there are few points to keep in mind −

An if can have zero or one else's and it must come after any else if's.

An if can have zero to many else if's and they must come before the else.

Once an else if succeeds, none of the remaining else if's or else's will be tested.

**Syntax**

The syntax of an if...else if...else statement in Go programming language is −

```go
if(boolean_expression 1) {
   /* Executes when the boolean expression 1 is true */
} else if( boolean_expression 2) {
   /* Executes when the boolean expression 2 is true */
} else if( boolean_expression 3) {
   /* Executes when the boolean expression 3 is true */
} else {
   /* executes when the none of the above condition is true */
}
```

**Example**

```go
package main

import "fmt"

func main() {
   /* local variable definition */
   var a int = 100
 
   /* check the boolean condition */
   if( a == 10 ) {
      /* if condition is true then print the following */
      fmt.Printf("Value of a is 10\n" )
   } else if( a == 20 ) {
      /* if else if condition is true */
      fmt.Printf("Value of a is 20\n" )
   } else if( a == 30 ) {
      /* if else if condition is true  */
      fmt.Printf("Value of a is 30\n" )
   } else {
      /* if none of the conditions is true */
      fmt.Printf("None of the values is matching\n" )
   }
   fmt.Printf("Exact value of a is: %d\n", a )
}
```

When the above code is compiled and executed, it produces the following result −

```go
None of the values is matching
Exact value of a is: 100
```

### nested if statements

It is always legal in Go programming to nest if-else statements, which means you can use one if or else if statement inside another if or else if statement(s).

**Syntax**

The syntax for a nested if statement is as follows −

if( boolean_expression 1) {
   /* Executes when the boolean expression 1 is true */
   if(boolean_expression 2) {
      /* Executes when the boolean expression 2 is true */
   }
}
You can nest else if...else in the similar way as you have nested if statement.

**Example**

```go
package main

import "fmt"

func main() {
   /* local variable definition */
   var a int = 100
   var b int = 200
 
   /* check the boolean condition */
   if( a == 100 ) {
      /* if condition is true then check the following */
      if( b == 200 )  {
         /* if condition is true then print the following */
         fmt.Printf("Value of a is 100 and b is 200\n" );
      }
   }
   fmt.Printf("Exact value of a is : %d\n", a );
   fmt.Printf("Exact value of b is : %d\n", b );
}
```

When the above code is compiled and executed, it produces the following result −

```go
Value of a is 100 and b is 200
Exact value of a is : 100
Exact value of b is : 200
```

### switch statement

A switch statement allows a variable to be tested for equality against a list of values. Each value is called a case, and the variable being switched on is checked for each **switch case**.

In Go programming, switch statements are of two types −

- **Expression Switch** − In expression switch, a case contains expressions, which is compared against the value of the switch expression.

- **Type Switch** − In type switch, a case contain type which is compared against the type of a specially annotated switch expression.

**Expression Switch**

The syntax for expression switch statement in Go programming language is as follows −

```go
switch(boolean-expression or integral type){
   case boolean-expression or integral type :
      statement(s);      
   case boolean-expression or integral type :
      statement(s); 
   
   /* you can have any number of case statements */
   default : /* Optional */
      statement(s);
}
```

The following rules apply to a **switch** statement −

- The **expression** used in a **switch** statement must have an integral or boolean expression, or be of a class type in which the class has a single conversion function to an integral or boolean value. If the expression is not passed then the default value is true.

- You can have any number of case statements within a switch. Each case is followed by the value to be compared to and a colon.

- The **constant-expression** for a case must be the same data type as the variable in the switch, and it must be a constant or a literal.

- When the variable being switched on is equal to a case, the statements following that case will execute. No **break** is needed in the case statement.

- A **switch** statement can have an optional **default** case, which must appear at the end of the switch. The default case can be used for performing a task when none of the cases is true. No **break** is needed in the default case.

**Flow Diagram**


![switch_statement](/assets/switch_statement.jpg)


**Example**

```go
package main

import "fmt"

func main() {
   /* local variable definition */
   var grade string = "B"
   var marks int = 90

   switch marks {
      case 90: grade = "A"
      case 80: grade = "B"
      case 50,60,70 : grade = "C"
      default: grade = "D"  
   }
   switch {
      case grade == "A" :
         fmt.Printf("Excellent!\n" )     
      case grade == "B", grade == "C" :
         fmt.Printf("Well done\n" )      
      case grade == "D" :
         fmt.Printf("You passed\n" )      
      case grade == "F":
         fmt.Printf("Better try again\n" )
      default:
         fmt.Printf("Invalid grade\n" );
   }
   fmt.Printf("Your grade is  %s\n", grade );      
}
```

When the above code is compiled and executed, it produces the following result −

```go
Excellent!
Your grade is  A
```

**Type Switch**

The syntax for a **type switch** statement in Go programming is as follows −

```go
switch x.(type){
   case type:
      statement(s);      
   case type:
      statement(s); 
   /* you can have any number of case statements */
   default: /* Optional */
      statement(s);
}
```

The following rules apply to a **switch** statement −

- The **expression** used in a **switch** statement must have an variable of interface{} type.

- You can have any number of case statements within a switch. Each case is followed by the value to be compared to and a colon.

- The type for a case must be the same data type as the variable in the switch, and it must be a valid data type.

- When the variable being switched on is equal to a case, the statements following that case will execute. No break is needed in the case statement.

- A switch statement can have an optional default case, which must appear at the end of the switch. The default case can be used for performing a task when none of the cases is true. No break is needed in the default case.

**Example**

```go
package main

import "fmt"

func main() {
   var x interface{}
     
   switch i := x.(type) {
      case nil:	  
         fmt.Printf("type of x :%T",i)                
      case int:	  
         fmt.Printf("x is int")                       
      case float64:
         fmt.Printf("x is float64")           
      case func(int) float64:
         fmt.Printf("x is func(int)")                      
      case bool, string:
         fmt.Printf("x is bool or string")       
      default:
         fmt.Printf("don't know the type")     
   }   
}
```
When the above code is compiled and executed, it produces the following result −

```go
type of x :<nil>
```

### select statement

The syntax for a **select** statement in Go programming language is as follows −

```go
select {
   case communication clause  :
      statement(s);      
   case communication clause  :
      statement(s); 
   /* you can have any number of case statements */
   default : /* Optional */
      statement(s);
}
```

The following rules apply to a **select** statement −

- You can have any number of case statements within a select. Each case is followed by the value to be compared to and a colon.

- The **type** for a case must be the a communication channel operation.

- When the channel operation occured the statements following that case will execute. No **break** is needed in the case statement.

- A **select** statement can have an optional **default** case, which must appear at the end of the select. The default case can be used for performing a task when none of the cases is true. No **break** is needed in the default case.

**Example**

```go
package main

import "fmt"

func main() {
   var c1, c2, c3 chan int
   var i1, i2 int
   select {
      case i1 = <-c1:
         fmt.Printf("received ", i1, " from c1\n")
      case c2 <- i2:
         fmt.Printf("sent ", i2, " to c2\n")
      case i3, ok := (<-c3):  // same as: i3, ok := <-c3
         if ok {
            fmt.Printf("received ", i3, " from c3\n")
         } else {
            fmt.Printf("c3 is closed\n")
         }
      default:
         fmt.Printf("no communication\n")
   }    
}   
```

When the above code is compiled and executed, it produces the following result −

```go
no communication
```