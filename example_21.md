##  实例 - 数字到名字

### 描述

创建一个程序：将从 1 到 12 的数转换成相应的月份。提示用户输入数字,显示对应的英文月份:比如输入 1,显示 January;输入12,则显示 December。如果输入的值超出该范围,则显示相应的错误信息。


### 难度

- **简单**

### 输入输出(_加粗的是需要用户输入的内容_)

**输入输出：**
Please enter the number of the month: 3
The name of the month is March.

### 目的

- 考察switch/case

### 实现 - default


```go
package main

import (
	"fmt"
)

func main() {
	var month int

	fmt.Printf("Please enter the number of the month? ")
	fmt.Scanf("%d", &month)


	switch month {
		case 1:
			fmt.Printf("The name of the month is Jan.\n")
		case 2:
			fmt.Printf("The name of the month is Feb.\n")
		case 3:
			fmt.Printf("The name of the month is Mar.\n")
		case 4:
			fmt.Printf("The name of the month is Apr.\n")
		case 5:
			fmt.Printf("The name of the month is May.\n")
		case 6:
			fmt.Printf("The name of the month is Jun.\n")
		case 7:
			fmt.Printf("The name of the month is Jul.\n")
		case 8:
			fmt.Printf("The name of the month is Aug.\n")
		case 9:
			fmt.Printf("The name of the month is Sept.\n")
		case 10:
			fmt.Printf("The name of the month is Oct.\n")
		case 11:
			fmt.Printf("The name of the month is Nov.\n")
		case 12:
			fmt.Printf("The name of the month is Dec.\n")
		default:
			fmt.Printf("Your input out of range.\n")
	}
}

```


### 挑战

**version01 要求**

使用一个映射(map)或词典(dictionary)实现,去掉 switch 语句。

**version01 目的**

- 考察map的使用

**version01 实现**

```go
package main

import (
	"fmt"
)

func main() {
	var month int

	fmt.Printf("Please enter the number of the month? ")
	fmt.Scanf("%d", &month)

	//(1)
	months := map[int]string{
		1: "Jan",
		2: "Feb",
		3: "Mar",
		4: "Apr",
		5: "May",
		6: "Jun",
		7: "Jul",
		8: "Aug",
		9: "Sept",
		10: "Oct",
		11: "Nov",
		12: "Dec",
	}

	//(2)
	if elem, ok := months[month]; ok {
		fmt.Printf("The name of the month is %s.\n", elem)
	} else {
		fmt.Printf("Your input out of range.\n")
	}
}
```

`line (1):`定义了map，map不知道如何使用，可以参考之前的例子：定义map的两种方式

`line (2):`此处主要考察map的使用方式[Go 实例 - 密码验证](https://zhuanlan.zhihu.com/p/436402135)，当用户输入的值超出了键的范围，此时ok为false，利用此特性，我们可以判断出用户的输入是否合法。