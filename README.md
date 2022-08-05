# R 学习手册

## 1. 认识 R和 RStudio

### 1.1 R和 RStudio 简介

R是使用广泛的统计计算和绘图分析软件，基于S语言编写，20世纪90年代初，由Ross Ihaka 和 Robert Gentleman 共同编写，2000年发行1.0.0版本。

RStudio是R语言的集成开发环境(IDE)，RStudio之于R，相当于Pycharm之于python。RStudio是开源项目。

**为什么要使用R :**

- 强大的绘图功能，能轻松绘制你想要的任何图像

- 免费，开源

- 强大的技术社区支持

R Markdown用来从 R 中创建文档和网页，Shiny 则是使用 R 创建交互式应用程序。

[Style guide · Advanced R.](http://adv-r.had.co.nz/Style.html)

### 1.2 RStudio 界面介绍

左上：代码编辑栏。用于编辑代码，点击 run 即可运行。

左下：命令控制台，代码运行后，实时显示结果，如果出错，会进行报错。

右上：显示自定义的对象。

右下：查看文件、显示图像、获取包、获取帮助。

四个界面的大小可以自由拖动。

![img](https://jxinuhe8ml.feishu.cn/space/api/box/stream/download/asynccode/?code=ZDA5MzUzNTY4ZmQ0ZTA3YzU5YjQzMWVhNWJlZGRhMTRfUHBaZjhmQkZrdGdWTmlkQzRZcUdGTmh1UnhMVTVOS0dfVG9rZW46Ym94Y252YlF2UzhKZTRqSG1lNmxOQ3hPYVliXzE2NTk2OTgyNDA6MTY1OTcwMTg0MF9WNA)

R具有庞大的生态，你在学习和使用R中遇到的问题，都可以通过help获取帮助。你可以点击上方的R help，跳转到右下角搜索想要的答案。

![img](https://jxinuhe8ml.feishu.cn/space/api/box/stream/download/asynccode/?code=NzY0MDA4Y2RlOWI4YWNlNDgwOWIzZjQ4MDg4YzU4YzhfdWVTWDdseThMakpleGRRV3VaMHNLdTJLNFpWZ0xGOUxfVG9rZW46Ym94Y25Pa05QQWJSdHZGMFhURklZM3RSd1FkXzE2NTk2OTgyNDA6MTY1OTcwMTg0MF9WNA)

### 1.3 基本操作介绍

**赋值**

R 有一个最基本的概念——赋值，即把数据、表格等，赋予给一个新的变量，在R中赋值符号为 `<-`。比如：

```Plain
x <- 2+3*6
y <- x
x = 56
y
```

输出结果为：

```Plain
[1] 20
```

**创建和保存文件**

@todo

**代码执行**

使用`Ctrl`+`Enter` (`command`+`return`)执行本句代码，`Ctrl`+`Shift`+`Enter` (`command`+`shift`+`return`)执行文件中所有代码。

**分隔符**

当代码很长时，可以通过`Ctrl` (`command`) + `shift` + `R`插入像上面`foo`, `bar`风格符，增加代码可读性。

## 2. 向量（vector）

### 2.1 向量使用

对变量赋值，是R中的基本操作。赋值用符号`<-`,多个元素赋值可以使用`c()`  (concatenate)函数.

```Plain
x <- 5
num <- c(1, 4, 6, 19)
```

输出结果：

```Plain
> nums
[1]  1  4  6 19
```

查看向量长度：

```Plain
num <- c(1, 4, 6, 19)
length(num)
```

输出结果：

```Plain
[1] 4
```

多个向量合并：

```PowerShell
fruit_1 <- c("Apple","Banana","Carambola')
fruit_2 <- c("Durian","Haw","Lemon") 

fruits <- c(fruit_1, fruit_2, c("Papaya","Persimmon","Strawberry"))

fruits
```

输出结果为：

```Plain
> fruits
[1] "Apple"      "Banana"     "Carambola"  "Durian"     "Haw"       
[6] "Lemon"      "Papaya"     "Persimmon"  "Strawberry"
```

### 2.2 从列表中提取需要的元素

和python一样，R也可以提取需要的元素，但和python不一样的是，R从第一个开始：

看下面一个列表

```Plain
fruits <- c("Apple", "Banana", "Carambola", "Durian", "Haw", "Lemon" , "Papaya" ,  "Persimmon", "Strawberry")

fruits[3] # 提取第三个

fruits[c(2,5,7)] # 提取第2、5、7个

fruits[-c(2,5,7)] # 提取除了第2、5、7个的元素

fruits[c(2,5,7)] <- c("ON", "UP", "DOWN") # 第2，5，7个重新赋值

fruits[c(2:6)] # 提取第2，3，4，5，6个，包含第2个

fruits[2:6] # 提取第2，3，4，5，6个，包含第2个

fruits
```

运行结果分别是（注：上面代码必须单独运行，才能得到下面的结果，否则只会显示最后一个）

```Plain
> fruits[3] # 提取第三个
[1] "Carambola"

> fruits[c(2,5,7)] # 提取第2、5、7个
[1] "Banana" "Haw"    "Papaya"

> fruits[-c(2,5,7)] # 提取除了第2、5、7个的元素
[1] "Apple"      "Carambola"  "Durian"     "Lemon"      "Persimmon" 
[6] "Strawberry"

fruits[c(2,5,7)] <- c("ON", "UP", "DOWN") # 第2，5，7个重新赋值
[1] "Apple"      "ON"         "Carambola"  "Durian"     "UP"        
[6] "Lemon"      "DOWN"       "Persimmon"  "Strawberry"

> fruits[c(2:6)] # 提取第2，3，4，5，6个，包含第2个
[1] "Banana"    "Carambola" "Durian"    "Haw"       "Lemon"    

> fruits[2:6] # 提取第2，3，4，5，6个
[1] "Banana"    "Carambola" "Durian"    "Haw"       "Lemon" 
```

### 2.3 生成器

#### 2.3.1 元素重复

重复某个元素，基本格式如下：

（以下代码，上面是输入，下方为输出结果)

```Plain
> rep(2, 3) # 把2重复3次；或rep(2, times = 3)
 [1] 2 2 2
```

在此基础上，可以延展很多变体：

```Plain
> rep(c(1,2,3,4), 4) # 把1，2，3，4重复4次
 [1] 1 2 3 4 1 2 3 4 1 2 3 4 1 2 3 4
> rep(c(1:10), 2) # 1-10重复10次
 [1]  1  2  3  4  5  6  7  8  9 10  1  2  3  4  5  6  7  8  9 10
> rep(c(1, 2, 3), each = 3) # 把1, 2，3各重复4遍
 [1] 1 1 1 2 2 2 3 3 3
> rep(c(1, 2, 3), c(3, 2, 0)) # 把1, 2, 3分别重复3, 2, 0遍
 [1] 1 1 1 2 2
rep(8:15, rep(1:5, rep(1:2, 2:3))) # 把8（含）-15（含）分别重复1、2、3、3、4、4、5、5遍。注意每个元素与重复次数要对应，如8-15有8个元素，rep(1:5, rep(1:2, 2:3))也必须是8个原色
 [1]  8  9  9 10 10 10 11 11 11 12 12 12 12 13 13 13 13 14 14 14 14 14 15 15 15
[26] 15 15
```

#### 2.3.2 等差数列

```Plain
> seq(0, 15, 2) # 其实是`seq(from = 0, to = 15, by = 2)`的简写，表示0-15中，等差序列为2
 [1]  0  2  4  6  8 10 12 14
> seq(0, 20, length.out = 11) # 其实是`seq(from = 0, to = 20, length.out = 10`的简写。表示0-20中，按等差分成10个元素
 [1]  0  2  4  6  8 10 12 14 16 18 20
```

#### 2.3.3 随机数

`常见的随机数用runif(n, min, max)`，n表示生成的随机数数量，min是最小值，max是最大值。默认min=0，max=1。

```Plain
nums_1 <- runif(100000,1,100) # 随机生成10万个，1-100之间的随机数

hist(nums_1) # 画直方图
```

![img](https://jxinuhe8ml.feishu.cn/space/api/box/stream/download/asynccode/?code=MmM5Y2RhN2U2ZGNiMDA5NDBhMTA4ZjlhNDAwNTg0NjFfOUJVS0tSU0V4ZVlyRTFwQlRlRjBCRno0djllYmVqUnFfVG9rZW46Ym94Y253Sm1oa21ucVF6dzZxYzBvRDk3bmdjXzE2NTk2OTgyNDA6MTY1OTcwMTg0MF9WNA)

**正态分布的随机数：**

`使用rnorm(n, mean, sd)`, 三个参数分别代表数量，平均值，标准差。默认mean为0，sd为1。

```Plain
nums_1 <- rnorm(100000, 250, 20) # 生成10万个随机数，按照平均值为250，标准差为20，进行正态分布
hist(nums_1) # 画直方图
```

![img](https://jxinuhe8ml.feishu.cn/space/api/box/stream/download/asynccode/?code=MDU3Y2ZmOGM4N2ViMWY0ZmE5OWY1NjE0NjIzZmM0YzZfNG1hRmRaZUVTVjVVd3p4UUNsVkZQekU3b2RIcDc1ZW9fVG9rZW46Ym94Y251S0FnUzk3cEpiTXY1UngyT0NLWTZjXzE2NTk2OTgyNDA6MTY1OTcwMTg0MF9WNA)

#### 2.3.4 简单随机抽样

代码格式如下：

```Plain
sample(balls, 20, replace = TRUE) # ball表示总体，20表示抽取的数量， replace = TRUE表示抽取后放回，FALSE表示抽取后不放回(可不写）
```

从10个球中随机抽取8个，每次抽取放回：

```Plain
> balls <- letters[1:10]
> sample(balls, 8, replace = TRUE)

[1] "i" "g" "d" "c" "g" "i" "b" "c"
```

### 2.4 向量的排序

```Plain
> x <- c(10, 45, 2, 8, 12)

> sort(x) # 从小到大排序
[1]  2  8 10 12 45

> x[order(x)] # 从小到大排序
[1]  2  8 10 12 45

> order(x) # 返回每个元素从小到大对应的排序，如10是第三小的元素，返回值为3
[1] 3 4 1 5 2

> rev(sort(x)) # 从大到小排序
[1] 45 12 10  8  2

> rank(x) # 返回值为每个数值对应的排名
[1] 3 5 1 2 4

> rev(x) # 表示向量翻转
[1] 12  8  2 45 10
```

### 2.5 向量的集合运算

交集用intersect(x, y)，并集用union(x, y)，补集用setdiff(x, y)。作为集合是否相等，用setequal(x, y)，确定元素是否是集合的某个元素用is.element(x, y)，等价于x %in% y.

```Plain
> x <- c(1:15)
> y <- c(10:25, 5)

> intersect(x,y) # 求交集
[1]  5 10 11 12 13 14 15

> union(x, y) #求并集
 [1]  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20
[21] 21 22 23 24 25

> setdiff(x, y) #求补集，即不在集合y中的元素
[1] 1 2 3 4 6 7 8 9

> setequal(x, y) # 是否相等
[1] FALSE

> is.element(x, y) #确定x是否是y中的元素
 [1] FALSE FALSE FALSE FALSE  TRUE FALSE FALSE FALSE FALSE  TRUE
[11]  TRUE  TRUE  TRUE  TRUE  TRUE
```

## 3. 数据和列表

### 3.1 数据类型及基本运算

#### 3.1.1 数据类型

**常见数据类型如下**

| 类型      | 含义与说明             | 例子              |
| --------- | ---------------------- | ----------------- |
| numeric   | 浮点数向量             | 2, 3.14, sqrt(5)  |
| integer   | 整数向量               | 1L，3L，5L        |
| character | 字符向量；需被引号包围 | "@", "34", "文本" |
| logical   | 逻辑向量               | TRUE, FALSE, NA   |
| complex   | 复数向量               | 3+5i, i, 4+i      |

数据基本操作如下：

```Plain
> class(3) # 查询数据类型
 [1] "numeric"

> is.numeric(6) # 判断属于哪一种数据类型，TRUE则为正确
[1] TRUE

> as.numeric(6) # 强制转换为另一种数据类型
[1] 6
```

#### 3.1.2 数据运算

| 符号  | 描述                    |
| ----- | ----------------------- |
| +     | 加                      |
| -     | 减                      |
| *     | 乘                      |
| /     | 除以                    |
| ^或** | 乘幂                    |
| %/%   | 求整数商，比如7%/%3=2=2 |
| %%    | 求余数，比如7%%3=1      |

#### 3.1.3 常见的数据运算

**e^x和logx(y)函数**

```Plain
exp(1) # e^x函数
log(100,10) # log(x,y)，以y为底x的函数
```

**保留数字位数**

```Plain
> signif(12.3456789, 4) # 保留4位数，注意是总共保留4位数，不是保留小数点后面4位
 [1] 12.35
 
> round(12.3456789, 3) # 保留3位小数
 [1] 12.346
```

#### 3.1.4 R 中自带的常见函数

![img](https://jxinuhe8ml.feishu.cn/space/api/box/stream/download/asynccode/?code=NWYzODFjNzc4OTUwOTZmMTczYmFiNzg3MjhhYjIzZThfYXhzYXFjRHBKZHpucFpFODNPRGpBaXdkTjVFWkRETmJfVG9rZW46Ym94Y25NR2tDd0trSVhjb1U0QUdCeXhhd0JkXzE2NTk2OTgyNDA6MTY1OTcwMTg0MF9WNA)

*资料来源：**[2.3 数学表达和运算 | R与tidyverse——数据分析入门](https://tshi.page/r-and-tidyverse-book/math.html)*

### 3.2 列表

#### 3.2.1 列表基本操作

```Plain
> list(1, 2, 4, NA, 3L, "de")

[[1]]
[1] 1

[[2]]
[1] 2

[[3]]
[1] 4

[[4]]
[1] NA

[[5]]
[1] 3

[[6]]
[1] "de"
```

#### 3.2.2 合并与拆开

```Plain
> c(list(1, 2), list(3, 4, list(5,6))) # 使用c来合并列表
[[1]]
[1] 1

[[2]]
[1] 2

[[3]]
[1] 3

[[4]]
[1] 4

[[5]]
[[5]][[1]]
[1] 5

[[5]][[2]]
[1] 6
> unlist(list(1, list(2, list(3, 4)), list(5, 6), 7, 8, 9)) # 一直拆解到无列表
[1] 1 2 3 4 5 6 7 8 9

> unlist(list(1, list(2, list("a", 4)), list(5, TRUE), 7L, 8, 9+0i))
[1] "1"    "2"    "a"    "4"    "5"    "TRUE" "7"    "8"    "9+0i"

# unlist(list(A, B)等同于c(A, B)
```

### 3.3 矩阵(matrix)和数组(array)

**创建5行8列的数组：**

```Plain
A <- 1:40
dim(A) <- c(5,8) 
A
```

输出结果：

```Plain
  [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8]
[1,]    1    6   11   16   21   26   31   36
[2,]    2    7   12   17   22   27   32   37
[3,]    3    8   13   18   23   28   33   38
[4,]    4    9   14   19   24   29   34   39
[5,]    5   10   15   20   25   30   35   40
```

索引行列数据

```Plain
> A[5,3] # 第5行第3列数据
 [1] 15

> A[5, ] # 第5行全部数据
 [1]  5 10 15 20 25 30 35 40

> A[, 7] # 第7列全部数据
 [1] 31 32 33 34 35
```

**创建2行8列的3个数组：**

```Plain
A <- 1:48
dim(A) <- c(2, 8, 3) 
A
```

**结果如下：**

```Plain
, , 1

     [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8]
[1,]    1    3    5    7    9   11   13   15
[2,]    2    4    6    8   10   12   14   16

, , 2

     [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8]
[1,]   17   19   21   23   25   27   29   31
[2,]   18   20   22   24   26   28   30   32

, , 3

     [,1] [,2] [,3] [,4] [,5] [,6] [,7] [,8]
[1,]   33   35   37   39   41   43   45   47
[2,]   34   36   38   40   42   44   46   48
```

**接下来使用****`dimnames()`****为每个行、列和每个列表命名**

```Plain
A <- 1:48
dim(A) <- c(2, 8, 3)

dimnames(A) <- list(paste("行数.", 1:2), # 行命名
                    c("列1", "列2", "列3", "列4", "列5", "列6", "列7", "列8"), # 列命名
                    c("表1", "表2", "表3")) # 表头命名
    
A
```

结果如下：

```Plain
, , 表1

        列1 列2 列3 列4 列5 列6 列7 列8
行数. 1   1   3   5   7   9  11  13  15
行数. 2   2   4   6   8  10  12  14  16

, , 表2

        列1 列2 列3 列4 列5 列6 列7 列8
行数. 1  17  19  21  23  25  27  29  31
行数. 2  18  20  22  24  26  28  30  32

, , 表3

        列1 列2 列3 列4 列5 列6 列7 列8
行数. 1  33  35  37  39  41  43  45  47
行数. 2  34  36  38  40  42  44  46  48
```

### 3.4 循环

循环语句的基本用法：

```Plain
for(var in seq) {
  expr
}
m <- 1:100 # 产生一个[1,2,3,...,99,100] # 从1-100依次产生整数

n <- vector("numeric")
for (i in m) {
  if (i %% 2 == 0) {   # 如果i是偶数
    n <- append(n, i^2) # 那么n为i的平方
  } else if (i == 51) { # 当i等于51，则结束
    break
  }
}

n
```

**输出结果：**

```Plain
 [1]    4   16   36   64  100  144  196  256  324  400  484  576  676  784  900
[16] 1024 1156 1296 1444 1600 1764 1936 2116 2304 2500
```

**while循环：**

当条件满足cond，重复循环expr。

```Plain
while (cond) {
  expr
}
```

重复执行使用repeat，直到使用break打断

```Plain
repeat {
  expr
}
i < 1
repeat {
  print(i)
  i = i + 1
  if (i == 100) {
    break
    }
   }
```

for  和 while 区别：

-  while 适用于不知道要运行多少次

-  知道结束循环的条件

## 4. 函数

### 4.1 函数基本操作

```Plaintext
FuncName <- function (arglist) {
  expr
  return(value)
}
```

**举例**

```Plain
grade <- function(i, k){
  if(k <= 100) {
    k = i^2
    return(k)
  }
  else {
    break
  }
}

grade(i<-1:100, 10)
```

输出结果：

```Plain
> grade(i<-1:100, 10)
  [1]     1     4     9    16    25    36    49    64    81   100   121   144
 [13]   169   196   225   256   289   324   361   400   441   484   529   576
 [25]   625   676   729   784   841   900   961  1024  1089  1156  1225  1296
 [37]  1369  1444  1521  1600  1681  1764  1849  1936  2025  2116  2209  2304
 [49]  2401  2500  2601  2704  2809  2916  3025  3136  3249  3364  3481  3600
 [61]  3721  3844  3969  4096  4225  4356  4489  4624  4761  4900  5041  5184
 [73]  5329  5476  5625  5776  5929  6084  6241  6400  6561  6724  6889  7056
 [85]  7225  7396  7569  7744  7921  8100  8281  8464  8649  8836  9025  9216
 [97]  9409  9604  9801 10000
```

遇到层层函数嵌套的情况**`h`**`(`**`g`**`(`**`f`**`(x)))`，借助`% > % `:

```Plaintext
x %>% 
  f() %>% 
  g() %>% 
  h()
```

## 5. tibble 

tibble用来替换data.frame的表格型数据结构，tibble是tidyverse的一部分，读写速度更快。

```Plain
library(didyverse)
mpg # 默认显示前10行
```

![img](https://jxinuhe8ml.feishu.cn/space/api/box/stream/download/asynccode/?code=NjQ3ZjMxMTA1NTNkY2Q5MTBjMzI5ZWJiNGU3NmNlOWJfaWRybXNFeWh1M2g0bDRETmNiRXlPQ1duTXJtWHhXSURfVG9rZW46Ym94Y25hbko1enFwRWI3WllJSzE1alhqa0lmXzE2NTk2OTgyNDA6MTY1OTcwMTg0MF9WNA)

(图片来源：https://tshi.page/r-and-tidyverse-book/tibble-view.html）

基本操作：

```Plain
view(mpg) # 查看所有数据
head(mpg, 8)  # 开头前8行
tail(mpg) # 最后8行
```

### 5.1 创建

#### 5.1.1 创建

**直接在向量中赋值：**

```Plain
library(tibble)

my_tibble_1 <- tibble(
  nums = c("one", "two", "three"), # 列1
  chars_1 = c("数1", "数2", "数3"), # 列2
  chaars_2 = c("数4", "数5", "数6") # 列3
                )
my_tibble_1
```

输出结果为：

```Plain
# A tibble: 3 × 3
  nums  chars_1 chaars_2
  <chr> <chr>   <chr>   
1 one   数1     数4
2 two   数2     数5    
3 three 数3     数6  
```

**也可以通过向量创建：**

```Plain
x <- c("one", "two", "three")
y <- c("数1", "数2", "数3")
z <- c("数4", "数5", "数6")

my_tibble_1 <- tibble(nums = x, chars_1 = y, chars_2 = z)

my_tibble_1
```

输出结果如下，与第一种方法一样：

```Plain
# A tibble: 3 × 3
  nums  chars_1 chars_2
  <chr> <chr>   <chr>  
1 one   数1     数4    
2 two   数2     数5    
3 three 数3     数6   
```

#### 5.1.2 新增

```Plain
chars_2 <- mutate(my_tibble_1, 
    chars_3 = c("数7", "数8", "数9")
    
 my_tibble_1
```

### 5.2 抓取行列

#### **5.2.1 抓取列**

从整个列表中抓取需要所需的列，可以使用下面三种方法：

```Plain
# 方法1:通过变量名称抓取
my_tibble_1[["chars_1"]]

# 方法2:使用$
my_tibble_1$chars_1 

# 方法3:使用索引
my_tibble_1[[2]]
```

如果要抓取多列，则可以使用`select`:

```Plain
library(dplyr)

x <- c("one", "two", "three")
y <- c("数1", "数2", "数3")
z <- c("数4", "数5", "数6")

my_tibble_1 <- tibble(nums = x, chars_1 = y, chars_2 = z)

shuju <- select(my_tibble_1, 1, 3) # 提取第一列，第三列，也可以使用select(my_tibble_1, -2)

shuju
```

运行结果如下：

```Plain
# A tibble: 3 × 2
  nums  chars_2
  <chr> <chr>  
1 one   数4    
2 two   数5    
3 three 数6  
```

#### 5.2.2 抓取行

抓取行的方法和抓取列的方法一样，把`select`函数换成`slice()`函数.

```Plain
library(dplyr)

x <- c("one", "two", "three")
y <- c("数1", "数2", "数3")
z <- c("数4", "数5", "数6")

my_tibble_1 <- tibble(nums = x, chars_1 = y, chars_2 = z)

shuju <- slice(my_tibble_1, 1, 3) # 提取第一行，第三行，也可以使用slice(my_tibble_1, -2)

shuju
```

结果如下：

```Plain
# A tibble: 2 × 3
  nums  chars_1 chars_2
  <chr> <chr>   <chr>  
1 one   数1     数4    
2 three 数3     数6    
```

抓取满足某些特定条件的行，使用`filter()`:

```Plain
library(dplyr)

x <- 1:6
y <- 4:9
z <- 5:10

my_tibble_1 <- tibble(nums = x, chars_1 = y, chars_2 = z)

shuju <- filter(my_tibble_1, chars_2>=3 & chars_2 <= 6) # 提取chars_2列 满足数字大于等于3小于等于6的元素

shuju
```

结果如下：

```Plain
# A tibble: 2 × 3
   nums chars_1 chars_2
  <int>   <int>   <int>
1     1       4       5
2     2       5       6
```

#### 5.2.3 排序

使用`arrange`

排序：

```Plain
arrange(my_tibble_1, chars_2) # 从小到大排列
arrange(my_tibble_1, -chars_2) # 从大到小排列
```

重命名变量

```Plain
my_tibble <- dplyr::rename(my_tibble_1, 列2 = chars_2) # 把chars_2命名为 列2
```

#### 5.2.4 汇总统计

使用`summarize`

```Plain
summary_temp <- summarize(my_tibble_1, mean(chars_1), sd(chars_1))
```

- `mean()`: 平均值

- `sd()`: 标准差，它是价差的衡量标准

- `min()`和`max()`：分别为最小值和最大值

- `IQR()`: 四分位距

- `sum()`: 多个数字相加的总数

- `n()`: 每组中的行数

#### 5.2.5 分组

使用`groub_by`

```Plain
summary_monthly_temp <- weather %>% 
  group_by(month) %>% 
  summarize(mean = mean(temp, na.rm = TRUE), 
            std_dev = sd(temp, na.rm = TRUE))
summary_monthly_temp
```

## 6. R 包

### 6.1 包的安装和卸载

R 包是什么？我们可以把RStudio理解为一部手机，R 包则是一个个的APP，把能实现特定功能的程序“打包”在一起，当你调用包时，就可以实现想要的功能。

包的安装有两种方法。

第一种：找到顶部菜单栏Tools--->Install Packages--->输入包的名称，完成安装

第二种：在代码运行区输入

```Plain
install.packages('包的名称')
```

安装成功后，显示如下：

![img](https://jxinuhe8ml.feishu.cn/space/api/box/stream/download/asynccode/?code=MmViNWExMTBjMzU5MGNiZjI5MDhjYTE3ZWZlYTM1ZmZfWFc1aHFjcml2V2l1amN1SzQ2V1N2cHhrUGVVQTNLY0hfVG9rZW46Ym94Y25rSlp4RkVNNGtKQ2xCRDVVYk5lMkNlXzE2NTk2OTgyNDA6MTY1OTcwMTg0MF9WNA)

**包的更新：**

更新：`update.packages()`；

包的卸载：`remove.packages()`

### 6.2 包的使用

在使用包时，需要使用如下代码加载包:

```Plain
library('包的名称')
```

如果有多个包，每一个包的加载都输入上面的加载语法麻烦的话，可以使用下面语法，加载多个包，读取成功，会返回TRUE。

```Plain
library(c('包1', '包2', '包3'), require, c = T)
```

当载入`dplyr`时，我们发现：

```Plain
载入程辑包：‘dplyr’

The following objects are masked from ‘package:stats’:

    filter, lag

The following objects are masked from ‘package:base’:

    intersect, setdiff, setequal, union
```

为什么会这样？因为R自带了`stats、base`的包，现在使用的`dplyr`有同名的 filter(), lag()，intersect()，setdiff()，setequal()， union()，把自带的覆盖了。此时，程序会以最后（近）的包为对象读取。当然，你也可以使用`packageName::object`调取，先把包名称写出来。不过这种方法，应该不常用。

**在R包中，最常用的包有下面四个：**

```Plaintext
library(ggplot2)
library(dplyr)
library(readr)
library(tidyr)
```

`ggplot2`用于数据可视化，`dplyr`用于数据整理，`readr`用于将电子表格数据导入 R，`tidyr`用于转置数据。

而这四个R包，可以通过`tidyvers`包一并加载出来。

```Plain
> library(tidyverse)
── Attaching packages ────────────────────────────────────── tidyverse 1.3.1 ──
✔ tibble  3.1.7     ✔ dplyr   1.0.9
✔ tidyr   1.2.0     ✔ stringr 1.4.0
✔ purrr   0.3.4     ✔ forcats 0.5.1
── Conflicts ───────────────────────────────────────── tidyverse_conflicts() ──
✖ dplyr::filter() masks stats::filter()
✖ dplyr::lag()    masks stats::lag()
```

## 7. 数据导入和整理

### 7.1 数据导入

```Plain
library(readr)
dem_score <- read_csv("https://moderndive.com/data/dem_score.csv")
dem_score
```

结果如下：

```Plain
# A tibble: 96 × 10
   country    `1952` `1957` `1962` `1967` `1972` `1977` `1982` `1987` `1992`
   <chr>       <dbl>  <dbl>  <dbl>  <dbl>  <dbl>  <dbl>  <dbl>  <dbl>  <dbl>
 1 Albania        -9     -9     -9     -9     -9     -9     -9     -9      5
 2 Argentina      -9     -1     -1     -9     -9     -9     -8      8      7
 3 Armenia        -9     -7     -7     -7     -7     -7     -7     -7      7
 4 Australia      10     10     10     10     10     10     10     10     10
 5 Austria        10     10     10     10     10     10     10     10     10
 6 Azerbaijan     -9     -7     -7     -7     -7     -7     -7     -7      1
 7 Belarus        -9     -7     -7     -7     -7     -7     -7     -7      7
 8 Belgium        10     10     10     10     10     10     10     10     10
 9 Bhutan        -10    -10    -10    -10    -10    -10    -10    -10    -10
10 Bolivia        -4     -3     -3     -4     -7     -7      8      9      9
# … with 86 more rows
```

可以看到，变量名两侧加上了引号，那是因为默认情况下，R 中的变量名不允许以数字开头，也不允许包含空格。

导入excel文件方法类似，可以使用路径`File--> Import Dateset --> From Excel`操作界面如下，观察右下角的代码，也可以使用代码导入。

![img](https://jxinuhe8ml.feishu.cn/space/api/box/stream/download/asynccode/?code=NzAzYzljNjVkY2IyODBmZTdlNTI0N2Q1NTk2OTRjMTdfUVJFSU40dkM0RDNCTllaQ25QcHVTZEhIQ0NrWVZabWJfVG9rZW46Ym94Y25VcFlpOEhDaWN5ZmZsUGlvRllrN2RjXzE2NTk2OTgyNDA6MTY1OTcwMTg0MF9WNA)

### 7.2 数据清理

每一个变量为一列，每一个观察为一行，每种类型的数据形成一个单独的表格。

观察***7.1中的数据，****country* 是变量，应该变成列，时间应该变成行，可以使用下面的代码实现：

```Plain
guat_dem_tidy <- guat_dem %>% 
  pivot_longer(names_to = "year",  # names_to 为把原来数据框中的行变为列
               values_to = "democracy_score", # values_to 字符串，创建新的列名称
               cols = -country, # 为不想整理的
               names_transform = list(year = as.integer))  # 设置变量的数值类型
guat_dem_tidy
```

实际运用中，拿到的数据往往存在缺失值、数据出错等情况，我们称之为脏数据，包括：

- 缺失值：R中有NA表示，可以使用is.na()判断是否存在缺失值。处理方法
  - 删除法：na.omit()，移除所有含有缺失行等列
  - 替换法：使用中位数和众数替换
  - 

- 异常值

- 重复值

### 7.3 数据挖掘相关包

![img](https://jxinuhe8ml.feishu.cn/space/api/box/stream/download/asynccode/?code=NjdlMDQzYmJlMjJjNTYxMTNkNjYxYzFiY2Q2ZjA4NjRfQllQRjhSYW5CYlAwMlpGWjBYU0UwbGZTM00yTkFiZFZfVG9rZW46Ym94Y25ONU0wUzE0cWlIbXhsSzd3SktPSEloXzE2NTk2OTgyNDA6MTY1OTcwMTg0MF9WNA)

## 8. 回归分析

### 8.1 描述性数据分析

数据分析有三种类别：描述性数据分析、预测性数据分析、规范性数据分析。

- 描述性数据分析：描述数据是什么。常见指标包括平均数、中位数、众数、四分位数等。

- 预测性数据分析：从数据中预测。

- 规范性数据分析：从数据中得到判断。

```Plain
library(tidyverse)

library(readr)
dem_score <- read_csv("https://moderndive.com/data/dem_score.csv")

guat_dem_tidy <- dem_score %>% 
  pivot_longer(names_to = "year",  # names_to 为把原来数据框中的行变为列
               values_to = "democracy_score", # values_to 字符串，创建新的列名称
               cols = -country, # 为不想整理的
               names_transform = list(year = as.integer))  # 设置变量的数值类型

guat_dem_tidy %>% summarize(
    year_mean = mean(year), democracy_score_mean = mean(democracy_score),
    year_median = median(year)
)
```

结果如下：

```Plain
 year_mean democracy_score_mean year_median
      <dbl>                <dbl>       <dbl>
1      1972               -0.826        1972
```

次数可以使用`skim`()，一次性计算：

- `missing`：缺失值的数量

- `complete`：非缺失值或完整值的数量

- `n`：值的总数

- `mean`: 平均值

- `sd`: 标准差

- `p0`：最小值

- `p25`：1/4分位数

- `p50`：1/2分位数

- `p75`：3/4分位数

- `p100`：最大值

计算相关系数：

```Plain
evals_ch5 %>% 
  get_correlation(formula = score ~ bty_avg)
```

### 8.2 一元线性回归

描述一个自变量和一个因变量之间的关系。

```Plain
x <- c(1, 12, 89, 28, 13, 93, 92, 9, 34)
y <- c(34, 12, 13, 56, 89, 1, 9, 23, 20)

relation <- lm(y ~ x)
relation
```

得出x y 的相关系数：

```Plain
Coefficients:
(Intercept)            x  
    44.6890      -0.3914
```

### 8.3 多元线性回归

### 8.4 R语言分类及预测算法函数

使用R进行数据挖掘时，分类和预测占很大比重，涵盖多个算法模块。主要的算法模型包含神经

## 9. 抽样

例1:从一个碗中随机抽取50个小球，计算抽取到红色小球的概率。

```Plain
library(tidyverse)
library(moderndive)

tactile_prop_red

ggplot(tactile_prop_red, aes(x = prop_red)) +
  geom_histogram(binwidth = 0.05, boundary = 0.4, color = "white") +
  labs(x = "Proportion of 50 balls that were red", 
       title = "Distribution of 33 proportions red") 
```

![img](https://jxinuhe8ml.feishu.cn/space/api/box/stream/download/asynccode/?code=YzhkZTljNmYwZjc1NWM1ZmUxYjgyMDM5NGUyMjhiZTFfR0IyVWswQ2Fubm9lZEx2VzdsbDM1RDlsaEs0RjRTUEdfVG9rZW46Ym94Y24zQ3dFVVNubERzMTBxUU1LYkpUSmJoXzE2NTk2OTgyNDA6MTY1OTcwMTg0MF9WNA)

例2:从1000个球中随机抽取25个，计算是红色球的概率，并且绘制成条形图。

```Plain
library(tidyverse)
library(moderndive)

bowl 

# 1.a) Virtually use shovel 1000 times
virtual_samples_25 <- bowl %>% 
  rep_sample_n(size = 25, reps = 1000)

# 1.b) Compute resulting 1000 replicates of proportion red
virtual_prop_red_25 <- virtual_samples_25 %>% 
  group_by(replicate) %>% 
  summarize(red = sum(color == "red")) %>%
  mutate(prop_red = red / 25)

# 1.c) Plot distribution via a histogram
ggplot(virtual_prop_red_25, aes(x = prop_red)) +
  geom_histogram(binwidth = 0.05, boundary = 0.4, color = "white") +
  labs(x = "Proportion of 25 balls that were red", title = "25") 
```

## 10. 假设检验、置信区间

@todo

## 11. 数据可视化

### `11.1 ggplot`介绍

`ggplot`是用于数据可视化的包。

基本操作语法为：

```Plain
ggplot(data = NULL, mapping = aes(), ..., environment = parent.frame())
```

有3个部分组成：

- `data`：数据集。

- `geom`: 几何对象，可以在图中观察到的对象类型。例如：点、线和条。

- `aes`：描述几何对象，如x/y 位置、颜色、形状和大小。

**基本图形**

- 散点图`geom_point()`

- 折线图`geom_line()`

- 箱线图通过`geom_boxplot()`

- 直方图通过`gom_histogram()`

- 通过条形图`geom_bar()`或`geom_col()`

示例：

```Plain
library(nycflights13)
library(ggplot2)

ggplot(data = alaska_flights, mapping = aes(x = dep_delay, y = arr_delay)) + 
  geom_point() # 散点图
```

![img](https://jxinuhe8ml.feishu.cn/space/api/box/stream/download/asynccode/?code=YTcyNzQ1YWFhNzEzYjJlODhjOWRiYTg5YWYwOTVkMzRfelRTbElDRlM2a2xMTWtWVXZ2VElqb3RTeHBhWDUzUXdfVG9rZW46Ym94Y25QSWJKS1ZDWlBJOEFOeHVIaG15MkJkXzE2NTk2OTgyNDA6MTY1OTcwMTg0MF9WNA)

## 12. 实战案例：西雅图房价预测

@todo

## 感谢

在学习过程中，除了参考官方文档，主要参考了[R与tidyverse——数据分析入门](https://tshi.page/r-and-tidyverse-book/index.html#intro) 内容，非常感谢！

## ChangeLog

20220805 优化案例

20220618 完成初稿
