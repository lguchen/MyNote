# 🐍 Python 30 天

| 日期   | 标题                                                         |
| ------ | ------------------------------------------------------------ |
| 第一天 | [介绍](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/readme.md) |
| 02     | [变量和内置方法](2_day.md)                                   |
| 03     | [运算符](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/03_Day_Operators/03_operators.md) |
| 04     | [字符串](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/04_Day_Strings/04_strings.md) |
| 05     | [列表](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/05_Day_Lists/05_lists.md) |
| 06     | [元组](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/06_Day_Tuples/06_tuples.md) |
| 07     | [集合](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/07_Day_Sets/07_sets.md) |
| 08     | [字典](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/08_Day_Dictionaries/08_dictionaries.md) |
| 09     | [条件](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/09_Day_Conditionals/09_conditionals.md) |
| 10     | [循环](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/10_Day_Loops/10_loops.md) |
| 11     | [方法](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/11_Day_Functions/11_functions.md) |
| 12     | [模块](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/12_Day_Modules/12_modules.md) |
| 13     | [列表推导式](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/13_Day_List_comprehension/13_list_comprehension.md) |
| 14     | [高阶函数](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/14_Day_Higher_order_functions/14_higher_order_functions.md) |
| 15     | [类型错误](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/15_Day_Python_type_errors/15_python_type_errors.md) |
| 16     | [日期时间](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/16_Day_Python_date_time/16_python_datetime.md) |
| 17     | [异常处理](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/17_Day_Exception_handling/17_exception_handling.md) |
| 18     | [正则表达式](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/18_Day_Regular_expressions/18_regular_expressions.md) |
| 19     | [文件处理](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/19_Day_File_handling/19_file_handling.md) |
| 20     | [包管理](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/20_Day_Python_package_manager/20_python_package_manager.md) |
| 21     | [类和对象](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/21_Day_Classes_and_objects/21_classes_and_objects.md) |
| 22     | [爬虫](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/22_Day_Web_scraping/22_web_scraping.md) |
| 23     | [虚拟环境](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/23_Day_Virtual_environment/23_virtual_environment.md) |
| 24     | [统计学](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/24_Day_Statistics/24_statistics.md) |
| 25     | [Pandas](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/25_Day_Pandas/25_pandas.md) |
| 26     | [网络编程](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/26_Day_Python_web/26_python_web.md) |
| 27     | [MongoDB](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/27_Day_Python_with_mongodb/27_python_with_mongodb.md) |
| 28     | [接口](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/28_Day_API/28_API.md) |
| 29     | [构建接口](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/29_Day_Building_API/29_building_API.md) |
| 30     | [结论](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/blob/master/30_Day_Conclusions/30_conclusions.md) |

# Python30天: 第一天 - 介绍

- 📘 第1天
  - 基础 Python
    - [Python 语法](#Python-语法)
    - [Python 缩进](#Python-缩进)
    - [备注](#备注)
    - 数据类型
      - [数字](#数字)
      - [字符串](#字符串)
      - [布尔](#布尔)
      - [列表](#列表)
      - [字典](#字典)
      - [元组](#元组)
      - [集合](#集合)
    - [检查数据类型](#检查数据类型)
    - [Python文件](#Python-文件)
  - 💻习题 - 第1天
    - [习题 1](#习题:1)
    - [习题 2](#习题:2)
    - [习题 3](#习题:3)

## 基础 Python

### Python 语法

一个python脚本可以在python终端中写，也可以在代码编辑器里面写。Python文件的扩展名是 .py。

### Python 缩进

一个缩进是一个空格。在和努懂开发语言中缩进是为了提高可读性，但是Python用缩进创建代码块。在其他语言里面，花括号用来创建代码块，而不是缩进。缩进错误是一个常见的python代码bug。

### 备注

备注对于让代码可读性非常重要。Python不执行备注部分的代码。 Python中任何以 #开头的代码都是备注。

**示例: 单行备注**

```
    # This is the first comment
    # This is the second comment
    # Python is eating the world
```

**示例: 多行备注**

当不赋值给变量时，3个双引号可以用于多行备注。

```
"""This is multiline comment
multiline comment takes multiple lines.
python is eating the world
"""
```

### 数据类型

Python有很多数据类型，我们从最常用的几个开始。不同的数据类型的详细介绍在其他章节会介绍道。在一开始，我们先熟悉一下数据类型，不需要非常清晰的去理解。

#### 数字

- Integer: 整型(负数，零 和 正数) 示例: ... -3, -2, -1, 0, 1, 2, 3 ...
- Float: 小数 示例 ... -3.5, -2.25, -1.0, 0.0, 1.1, 2.2, 3.5 ...
- 复数 示例 1 + j, 2 + 4j

#### 字符串

通过单括号或者双括号括起来的一个或者多个字母集合。如果字符串超过一句话，我们用三括号括起来。

**示例:**

```
'Asabeneh'
'Finland'
'Python'
'I love teaching'
'I hope you are enjoying the first day of 30DaysOfPython Challenge'
```

#### 布尔

布尔型boolean是 True 或者 False，T 和 F 必须是大写。

**示例:**

```
    True  #  Is the light on? If it is on, then the value is True
    False # Is the light on? If it is off, then the value is False
```

#### 列表

Python List 是有序的，可以包含不同数据类型的元素的集合。List和JavaScript的 array类似。

**示例:**

```
[0, 1, 2, 3, 4, 5]  # all are the same data types - a list of numbers
['Banana', 'Orange', 'Mango', 'Avocado'] # all the same data types - a list of strings (fruits)
['Finland','Estonia', 'Sweden','Norway'] # all the same data types - a list of strings (countries)
['Banana', 10, False, 9.81] # different data types in the list - string, integer, boolean and float
```

#### 字典

Python字典dictionary对象是无需的键值对合适的数据集合。

**示例:**

```
{
'first_name':'Asabeneh',
'last_name':'Yetayeh',
'country':'Finland', 
'age':250, 
'is_married':True,
'skills':['JS', 'React', 'Node', 'Python']
}
```

#### 元组

元组tuple是与列表list相似的有序的数据集合，一旦创建无法修改。

**示例:**

```
('Asabeneh', 'Pawel', 'Brook', 'Abraham', 'Lidiya') # Names
('Earth', 'Jupiter', 'Neptune', 'Mars', 'Venus', 'Saturn', 'Uranus', 'Mercury') # planets
```

#### 集合

集合set与列表list和元组tuple类似。但是与列表和元组不同的是，集合是无序的的数据集合。跟数学中的很像，Python的集合只存储不重复的元素。

在后面的部分，我们会更深入的了解Python的数据类型。

**示例:**

```
{2, 4, 3, 5}
{3.14, 9.81, 2.7} # order is not important in set
```

### 检查数据类型

通过 **type** 方法查看一个数据或者变量的数据类型。在下面的终端中你会看到不同的数据类型

### Python 文件

首先打开你的项目文件夹30DaysOfPython。如果你没有这个文件夹,创建一个文件夹命名为30DaysOfPython。在这个文件夹里,创建一个文件命名为helloworld.py。现在我们用visual studio code去做之前在python终端中做的事情。

Python终端不用 **print** 就可以打印,但是在visual studio code中要看到输出内容需要使用内置方法 **print()** 。内置方法**print()** 可以接受一个或者多个参数 *print(‘arument1', 'argument2', 'argument3’)*。看一下下面的示例。

**示例:**

文件名是 helloworld.py

```
# 第1天 - 30DaysOfPython Challenge

print(2 + 3)             # addition(+)
print(3 - 1)             # subtraction(-)
print(2 * 3)             # multiplication(*)
print(3 / 2)             # division(/)
print(3 ** 2)            # exponential(**)
print(3 % 2)             # modulus(%)
print(3 // 2)            # Floor division operator(//)

# Checking data types
print(type(10))          # Int
print(type(3.14))        # Float
print(type(1 + 3j))      # Complex number
print(type('Asabeneh'))  # String
print(type([1, 2, 3]))   # List
print(type({'name':'Asabeneh'})) # Dictionary
print(type({9.8, 3.14, 2.7}))    # Set
print(type((9.8, 3.14, 2.7)))    # Tuple
```

## 💻 习题-第1天

### 习题:1

1. 查看你使用的python版本
2. 打开python终端然后执行下面的操作习题,执行的对象是3和4。
   - 加法(+)
   - 减法(-)
   - 乘法(*)
   - 取余数(%)
   - 除法(/)
   - 幂运算(**)
   - 向下去整除(//)
3. 在python终端中写以下字符串:
   - 你的名字
   - 你的姓
   - 你的国家
   - 我很喜欢python30天
4. 检查以下数据的数据类型:
   - 10
   - 9.8
   - 3.14
   - 4 - 4j
   - ['Asabeneh', 'Python', 'Finland']
   - 你的名字
   - 你的姓
   - 你的国家

### 习题:2

1. 在30DaysOfPython文件夹中创建一个文件夹命名为day_1。在day_1文件夹中创建文件helloworld.py。然后重复上面的习题1,2,3,4。在python文件上工作时记得使用 *print()* 。定位到你保存文件的目录,然后去执行它。

### 习题:3

1. 写个使用不同数据类型的例子 例如 Number(Integer, Float, Complex), String, Boolean, List, Tuple, Set , Dictionary.
2. 计算2个点(2, 3) 和 (10, 8)之间的 [欧氏距离](https://gitee.com/link?target=https%3A%2F%2Fbaike.baidu.com%2Fitem%2F%E6%AC%A7%E5%87%A0%E9%87%8C%E5%BE%97%E5%BA%A6%E9%87%8F%2F1274107%3Ffromtitle%3D%E6%AC%A7%E6%B0%8F%E8%B7%9D%E7%A6%BB%26fromid%3D1798948%26fr%3Daladdin)