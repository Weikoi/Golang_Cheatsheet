# Golang_Cheatsheet
Go语言新手入门

## 一.基础语法
### 1-1  hello,world
    package main
    
    import "fmt"
    
    func main() {
        fmt.Println("Hello, 世界")
    }
    
    // golang 运行必须要有main package 和 main function 作为程序启动的入口



### 1-2  声明

    //Golang有四种类型的声明 var变量, const常量, type类型, func函数
    
    // Golang使用双斜杠开始行注释，多行注释使用/* */



1-2-1 变量声明

    var s string  // 声明一个变量
    var a,b,c int  // 声明一组变量
    var a,b,c = true, 2.3, "Hello"  // 赋值自动声明一组变量
    
    //Golang特色声明方式
    i := 10  // 省略var,赋值时自动声明
    i,j := 2,"Hello"  // 可用于声明一组变量
    file, err := os.open(path) // 也可用于打开文件的赋值声明

1-2-2 类型声明
    
    //一个类型声明语句创建了一个新的类型名称或者结构体，和现有类型具有相同的底层结构。
    type Celsius float64 // 创建一种摄氏度类型
    type Employee struct {  // 创建一种employee类型（Golang没有类，可以使用类型来替代类的功能）
    	Name string
    	Sex string
    	Age int
    }

1-2-3 常量声明
    
    //常量的值不可修改,常用于赋给类似于pi的数学常数
    const pi = 3.1415
    
    const(
    	pi = 3.1415
    	e = 2.7182
    )



1-2-4 函数声明

    //函数声明包括函数名、形式参数列表、返回值列表（可省略）以及函数体。
    //样板
    func name(parameter-list) (result-list) {
        body
    }
    //自定义一个add函数
    func add(x int, y int) int {
        return x + y
    }



1- 基本运算    

    //使用赋值语句可以更新一个变量的值
    x = 1   // 将 1 赋给x
    i, j = j, i // 交换 i 和 j 的值
    
    // 加法
    a := 1+2 
    x := "hello," + "world"  // 加法可用于字符串拼接
    
    // 减法
    b := 4-2
    
    // 乘法
    c := 3*4
    
    // 除法
    a := 1/2  // Golang 整数相除是假除法，只保留整数位，所以这里结果为0
    a := 1.0/2  // 结果为0.5



1-3 基本数据类型

    //整数类型
    //Golang分为有符号和无符号两种类型的整数。有int8、int16、int32和int64四种不同大小的有符号整数类型，与此对应的是uint8、uint16、uint32和uint64四种无符号整数类型。
    //byte // uint8 的别名,表示一个字节
    //rune // int32 的别名,表示一个 Unicode 码点
    var a uint8 = 255
    b := 100
    
    //浮点数
    // Golang提供了两种精度的浮点数，float32和float64
    var a float32 = 1.13
    b := 2.24
    
    //复数
    // Golang 提供两种精度的复数类型：complex64和complex128, 此类型很少被使用
    var x complex128 = complex(1, 2)  //  1 + 2i
    y := complex(2, 4)  // 2 + 4i
    
    //布尔值
    // if 与 for循环的条件部分是布尔类型，==或者<, >会产生布尔值结果
    var a bool = true
    if (2>1){
    	a=false
    } // 运行结果a为false
    
    //字符串
    // Golang的字符串为一个不可更改的字符序列
    var a String = "Hello"
    b := "Golang"

    
1-3 复合数据类型

    //数组
    //数组是一个由固定长度的特定类型元素组成的序列，一个数组可以由零个或多个元素组成。因为数组的长度是固定的，因此在Go语言中很少使用数组。
    //数组的每个元素可以通过索引下标来访问，索引下标的范围是从0开始到数组长度减1的位置。内置的len函数将返回数组中元素的个数。
    var q [3]int = [3]int{1, 2, 3}  // 长度为3的整型数组，初始值为1,2,3
    q := [3]int{1, 2, 3}   // 快速声明
    q := [...]int{1,2,3}  //如果在数组的长度位置出现的是“...”省略号，则表示数组的长度是根据初始化值的个数来计算
    
    
    //切片
    //切片代表变长的序列，序列中每个元素都有相同的类型, 一个slice由三个部分构成：指针、长度和容量。。
    //切片不可使用==来比较，只能用for循环展开，逐个比较
    months := [...]string{1: "January",/* ... */, 12: "December"}
    
    //Map
    无序的key/value对的集合
    创建
    ages := make(map[string]int)
    ages["alice"] = 31
    ages["charlie"] = 34
    或者
    ages := map[string]int{
    "alice": 31,
    "charlie": 34,
    }
    ages["bob"] = 18  # 增加值
    ages["alice"] = 32  # 改值
    fmt.Println(ages["alice"]) # 取值
    delete(ages, "alice")  # 删值
    
    
    //结构体
    //结构体是一种聚合的数据类型，是由零个或多个任意类型的值聚合成的实体。每个值称为结构体的成员。
    type Employee struct {
    	ID int
    	Name string
    	Address string
    	Birthday time.Time
    	Salary int
    
    }
    var alfred Employee
    
    //
    
    
    
    
    
    




输入



printf 格式化打印


指针

golang模拟队列，模拟栈


===============================================================

为什么说Golang是一门傻逼语言？

1. 没有类，面向对象设计写得很难受

2. 反人类的错误处理机制，写if err != nil写到想骂街

3. 没有原生set，这么常用的collection都没有？

4. map取不存在的key返回0，什么智障设计？？？


