##  实例 - 身高体质指数（Body Mass Index, BMI）

### 描述

创建一个程序：用一个人的身高(以厘米为单位)和体重(以公斤为单位)计算其体质指数(Body Mass Index,BMI)[^1]。该程序应提示用户输入身高和体重。

BMI = 体重(国际单位kg) / 身高的平方（国际单位㎡）


### 难度

- **简单+**

### 输入输出(_加粗的是需要用户输入的内容_)

**输入：**
What is your weight? **63.5**
What is the height? **168**

**输出：**
Your BMI is 19.5.
You are within the ideal weight range.

**或者输出：**
Your BMI is 32.5.
You are overweight. You should see your doctor.

### 目的

- 考察浮点计算
- 浮点的输入
- 注意浮点的等于比较，本例中不涉及此问题，相等比较需要有一个相差范围，在此范围内，就认定两数是相等的

### 实现 - default


```go
package main

import (
	"fmt"
)

func main() {
	//(1)
	var weight, height, bmi float32

	fmt.Printf("What is your weight? ")
	fmt.Scanf("%f", &weight)
	fmt.Printf("What is the height? ")
	fmt.Scanf("%f", &height)

	bmi = weight / (height * height) * 100 * 100

	fmt.Printf("Your BMI is %f.\n", bmi)
	if weight < 18.5 {
		fmt.Printf("You are underweight.")
	} else if (weight < 23.9) {
		fmt.Printf("You are within the ideal weight range.")
	} else if (weight < 27.9) {
		fmt.Printf("You are overweight. You should see your doctor.")
	} else {
		fmt.Printf("You are fat. You should see your doctor.")
	}
}

```

**解释**

`line (1):`定义浮点类型的变量，此处依据实际情况，只要定义精度为`float32`类型即可




### 挑战

**version01 要求**

请对结果保留两位小数精度即可

**version01 实现**

```go
package main

import (
	"fmt"
	"strconv"
)

func main() {

	var weight, height, bmi float32

	fmt.Printf("What is your weight? ")
	fmt.Scanf("%f", &weight)
	fmt.Printf("What is the height? ")
	fmt.Scanf("%f", &height)

	bmi = weight / (height * height) * 100 * 100

	//(1)
	bmi2, _ := strconv.ParseFloat(fmt.Sprintf("%.2f", bmi), 32)
	fmt.Printf("Your BMI is %.2f.\n", bmi2)

	if weight < 18.5 {
		fmt.Printf("You are underweight.")
	} else if (weight < 23.9) {
		fmt.Printf("You are within the ideal weight range.")
	} else if (weight < 27.9) {
		fmt.Printf("You are overweight. You should see your doctor.")
	} else {
		fmt.Printf("You are fat. You should see your doctor.")
	}
}
```

`line (1):`此处使用的方式和直接利用`fmt.Printf("%.2f", bmi)`的机理一样，可以不使用`strconv.ParseFloat`进行转换

此处是直接省略了其它小数位，如果需要依据四舍五入，需要利用加一个半数的形式，比如需要保留两位小数，对第三位小数采用四舍五入的方式，那么可以加一个半数，如下所示 -

```go
bmi = bmi + 0.005
bmi2, _ := strconv.ParseFloat(fmt.Sprintf("%.2f", bmi), 32)
```


[^1]: 根据世界卫生组织定下的标准，亚洲人的BMI(体重指标Body Mass Index)范围：(1) BMI < 18.5，体重偏轻；(2) 18.5 <= BMI <= 23.9，体重健康；(3) 24 <= BMI <= 27.9，体重超标；(4) 28 <= BMI，肥胖