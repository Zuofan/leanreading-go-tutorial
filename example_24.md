##  实例 - 数字到名字

### 描述

创建一个程序：比较用户输入的两个字符串是否为字母异位词（ anagram），也就是说两个词包含的字母是相同的，只是顺序不同。


### 难度

- **简单+**

### 输入输出(_加粗的是需要用户输入的内容_)

**输入输出：**
Enter two strings and I'll tell you if they are anagrams:
Enter the first string: note
Enter the second string: tone
"note" and "tone" are anagrams.


### 约束

- 使用一个名为 isAnagram 的函数来实现该程序，接收两个词作为参数，返回 true 或 false。在主程序中调用该函数。
- 检查这两个词的长度是否相同。

### 目的

- 考察字符串的使用
- 考察函数的使用

### 实现 - default


```go
package main

import (
	"fmt"
	"sort"
	"strconv"
	"strings"
)

func isAnagram(first, second string) bool {
	//(1)
	if len(first) != len(second) {
		fmt.Printf("%s and %s are not anagrams.\n", strconv.Quote(first), strconv.Quote(second))
		return
	}

	//(2)
	f := strings.Split(first, "")
	sort.Strings(f)
	firstNew := strings.Join(f, "")

	s := strings.Split(second, "")
	sort.Strings(s)
	secondNew := strings.Join(s, "")

	return strings.Compare(firstNew, secondNew) == 0
}

func main() {
	var first, second string

	fmt.Printf("Enter two strings and I'll tell you if they are anagrams:\n ")
	fmt.Printf("Enter the first string: ")
	fmt.Scanf("%s", &first)
	fmt.Printf("Enter the second string: ")
	fmt.Scanf("%s", &second)

	//(3)
	if isAnagram(first, second) {
		fmt.Printf("%s and %s are anagrams.\n", strconv.Quote(first), strconv.Quote(second))
	} else {
		fmt.Printf("%s and %s are not anagrams.\n", strconv.Quote(first), strconv.Quote(second))
	}
}
```

**解释**

- `func isAnagram(first, second string) bool`定义了函数：关键字——`func`指明了定义函数，参数是两个字符串，返回值类型是布尔类型

- `isAnagram`思路在于对字符串进行排序后进行比较

- `line (1):`使用内置的函数检查字符串的长度

- `line (2):`使用`strings.Split`函数分拆了字符串，并且进行排序后，合并成新的字符串。在Go中只有对针对`int`和`string`的排序，其余的需要实现`sort.Interface`接口。由于字符串可以很方便的转换为byte数组，也可以使用byte数组的方式来进行比较，但是由于Go内置的排序并没有内置对byte数组的支持，故而需要针对byte数组，实现sort.Interface接口，这里可以看一下实现方式：

	```go
	type Interface interface {
		// 获取数据集合元素个数
		Len() int
		// 如果i索引的数据⼩于j所以的数据， 返回true， 不会调⽤
		// 下⾯的Swap()， 即数据升序排序。
		Less(i, j int) bool
		// 交换i和j索引的两个元素的位置
		Swap(i, j int)
	}
	```
	
	上述接口函数，即为sort.Interface接口需要实现的函数，需要为byte数组实现上述接口中的函数。

	```go
	type sortBytes []byte

	func (s sortBytes) Less(i, j int) bool {
		return s[i] < s[j]
	}

	func (s sortBytes) Swap(i, j int) {
		s[i], s[j] = s[j], s[i]
	}

	func (s sortBytes) Len() int {
		return len(s)
	}

	func isAnagramV2(first, second string) bool {
		//(4)
		f := []byte(first)     
		s := []byte(second)
		//(5)
		sort.Sort(sortBytes(f))  
		sort.Sort(sortBytes(s))

		//(6)
		return bytes.Compare(f, s) == 0  
	}

	```
- `line (4):`将字符串转换为字节数组
- `line (5):`此处需要使用sortBytes转换一下
- `line (6):`调用bytes.Compare内置的函数，执行比较