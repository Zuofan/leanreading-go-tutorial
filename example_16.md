##  实例 - 法定开车年龄

### 描述

创建一个程序：让用户输入年龄,将其与法定驾驶年龄 18 比较。如果用户是 18 岁,或者更大,程序应该显示“You are old enough to legally drive.”。如果用户不到 18 岁,则显示“You are not old enough to legally drive.”

### 难度

**简单**

### 输入输出(_加粗的是需要用户输入的内容_)

**输入输出：**
What is your age? **17**
You are not old enough to legally drive.

**或者输入输出：**
What is your age? **19**
You are old enough to legally drive.

### 目的

    - 考察Go的条件结构的用法

### 实现 - default


```go
package main

import (
	"fmt"
)

func main() {
	var age int

    //(1)
	fmt.Printf("What is your age? ")
	fmt.Scanf("%d", &age)

	if age >= 18 {
		fmt.Printf("You are old enough to legally drive.\n")
	} else {
		fmt.Printf("You are not old enough to legally drive.\n")
	}

}
```

**解释**

`line (1):` 此处除了使用整型读入数据，没有太多的知识点

### 挑战

**version01 要求**

如果用户输入的是小于 0 的数,或者不是数字,显示错误消息,让用户输入一个合法的年龄。

**version01 实现**

```go
package main

import (
	"fmt"
)

func main() {
	var age int

	fmt.Printf("What is your age? ")
    //(1)
	_, err := fmt.Scanf("%d", &age)
	if err != nil {
		fmt.Printf("error: %s\n", err)
		return
	}

    if age < 0 {
        fmt.Printf("Age should be great zero: age = %d\n", age)
		return
    }

	if age >= 18 {
		fmt.Printf("You are old enough to legally drive.\n")
	} else {
		fmt.Printf("You are not old enough to legally drive.\n")
	}

}
```

**解释**

`line (1):` fmt.Scanf如果在读取数据后，返回读取数据的个数，并返回是否有错误的信息的二元组，这里如果输入字符串，会返回错误信息

```go
What is your age? aaa
error: expected integer
```

**version02 要求**

不再将法定驾驶年龄硬编码到程序逻辑中,而是研究不同国家的规定,创建一个驾驶年龄和国家的查询表。提示用户输入年龄,显示该用户在哪个国家可以合法驾驶。


**version02 实现**

```go
package main

import (
	"fmt"
	"strings"
)

func main() {
	var age int

	//(1)
	db := map[string]int{
		"中国" : 18,
		"美国" : 16,
		"法国" : 15,
		"英国" : 16,
		"日本" : 19,
	}
	
	fmt.Printf("What is your age? ")
	_, err := fmt.Scanf("%d", &age)
	if err != nil {
		fmt.Printf("error: %s\n", err)
		return
	}

	if age < 0 {
		fmt.Printf("Age should be great zero: age = %d\n", age)
		return
	}

    //(2)
	var countries []string

	for k, v := range db {
		if v >= age {
         //(3)
		 countries = append(countries, k)
		}
	}

    //(4)
	fmt.Printf("You could drive in %s\n", strings.Join(countries, ","))
}
```

**解释**

`line (1):` 使用了字面量来初始化`map`键值对，也可以使用以下的方式，先建立，后存储值：

```go
db := make(map[string]int)
db["中国"] = 18
db["美国"] = 16
```

在`line (1)`处使用的字面量初始化map，如果此时有相同的key，会包编译错误，故而这里没有使用`map[int]string`的map类型，因为有些国家的法定驾车年龄是相同的；
如果在`line (1)`后面，执行下面的语句：

```go
db["美国"] = 12
```
那么`db`中键为`美国`的值是12，原来的16被覆盖了。


`line (2):` 定义一个`slice`数组，和固定数组不同的点在于其空间是自动增长的。

`line (3):`是`slice`数组的固定使用模式，这里主要是因为：如果在使用过程中，`countries`的空间不够用了，Go内部需要重新申请新的空间，那么此时`append`操作返回的数组就不是原来的`countries`，故而需要重新赋值到`countries`上。

`line (4):`主要使用了strings.Join方法：第一个参数是数组，第二个是连接数组中各元素的分隔符。 可以参考文档`go doc strings.Join`：

```go
package strings // import "strings"

func Join(elems []string, sep string) string
    Join concatenates the elements of its first argument to create a single
    string. The separator string sep is placed between elements in the resulting
    string.
```