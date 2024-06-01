- 第五天
  - 列表
    - [如何创建列表](#如何创建列表)
    - [使用正索引访问列表项](#使用正索引访问列表项)
    - [使用负索引访问列表项](#使用负索引访问列表项)
    - [拆包清单项](#拆包清单项)
    - [从列表中切片项目](#从列表中切片项目)
    - [修改列表](#修改列表)
    - [检查列表中的项目](#检查列表中的项目)
    - [向列表添加项目](#向列表添加项目)
    - [将项目插入列表](#将项目插入列表)
    - [从列表中删除项目](#从列表中删除项目)
    - [使用 pop 删除项目](#使用 pop 删除项目)
    - [使用 del 删除项目](#使用 del 删除项目)
    - [清除列表项](#清除列表项)
    - [复制列表](#复制列表)
    - [联接列表](#联接列表)
    - [对列表中的项目进行计数](#对列表中的项目进行计数)
    - [查找项的索引](#查找项的索引)
    - [反转列表](#反转列表)
    - [对列表项进行排序](#对列表项进行排序)
  - 💻 练习：第5天
    - [练习：1级](#练习：1级)
    - [练习：2级](#练习：2级)

# 第五天

## 列表

Python 中有四种集合数据类型：

- 列表：是一个有序且可更改（可修改）的集合。允许重复成员。
- 元组：是有序且不可更改或不可修改（不可变）的集合。允许重复成员。
- Set：是一个无序、未索引和不可修改的集合，但我们可以将新项目添加到集合中。不允许重复成员。
- 字典：是一个无序、可更改（可修改）和索引的集合。没有重复的成员。

列表是不同数据类型的集合，它是有序的和可修改的（可变的）。列表可以为空，也可以具有不同的数据类型项。

### 如何创建列表

在 Python 中，我们可以通过两种方式创建列表：

- 使用列表内置函数

```
# syntax
lst = list()
empty_list = list() # this is an empty list, no item in the list
print(len(empty_list)) # 0
```

- 使用方括号，[]

```
# syntax
lst = []
empty_list = [] # this is an empty list, no item in the list
print(len(empty_list)) # 0
```

包含初始值的列表。我们使用 *len（）* 来查找列表的长度。

```python
fruits = ['banana', 'orange', 'mango', 'lemon']                     # list of fruits
vegetables = ['Tomato', 'Potato', 'Cabbage','Onion', 'Carrot']      # list of vegetables
animal_products = ['milk', 'meat', 'butter', 'yoghurt']             # list of animal products
web_techs = ['HTML', 'CSS', 'JS', 'React','Redux', 'Node', 'MongDB'] # list of web technologies
countries = ['Finland', 'Estonia', 'Denmark', 'Sweden', 'Norway']

# Print the lists and its length
print('Fruits:', fruits)
print('Number of fruits:', len(fruits))
print('Vegetables:', vegetables)
print('Number of vegetables:', len(vegetables))
print('Animal products:',animal_products)
print('Number of animal products:', len(animal_products))
print('Web technologies:', web_techs)
print('Number of web technologies:', len(web_techs))
print('Countries:', countries)
print('Number of countries:', len(countries))
output
Fruits: ['banana', 'orange', 'mango', 'lemon']
Number of fruits: 4
Vegetables: ['Tomato', 'Potato', 'Cabbage', 'Onion', 'Carrot']
Number of vegetables: 5
Animal products: ['milk', 'meat', 'butter', 'yoghurt']
Number of animal products: 4
Web technologies: ['HTML', 'CSS', 'JS', 'React', 'Redux', 'Node', 'MongDB']
Number of web technologies: 7
Countries: ['Finland', 'Estonia', 'Denmark', 'Sweden', 'Norway']
Number of countries: 5
```

- 列表可以包含不同数据类型的项目

```
 lst = ['Asabeneh', 250, True, {'country':'Finland', 'city':'Helsinki'}] # list containing different data types
```

### 使用正索引访问列表项

我们使用索引访问列表中的每个项目。列表索引从 0 开始。下图清楚地显示了索引的开始位置![列表索引](img\5.0.png)

```
fruits = ['banana', 'orange', 'mango', 'lemon']
first_fruit = fruits[0] # we are accessing the first item using its index
print(first_fruit)      # banana
second_fruit = fruits[1]
print(second_fruit)     # orange
last_fruit = fruits[3]
print(last_fruit) # lemon
# Last index
last_index = len(fruits) - 1
last_fruit = fruits[last_index]
```

### 使用负索引访问列表项

负索引表示从末尾开始，-1 表示最后一项，-2 表示倒数第二项。

![列出负索引](img\5.png)

```
fruits = ['banana', 'orange', 'mango', 'lemon']
first_fruit = fruits[-4]
last_fruit = fruits[-1]
second_last = fruits[-2]
print(first_fruit)      # banana
print(last_fruit)       # lemon
print(second_last)      # mango
```

### 拆包清单项

```
lst = ['item','item2','item3', 'item4', 'item5']
first_item, second_item, third_item, *rest = lst
print(first_item)     # item1
print(second_item)    # item2
print(third_item)     # item3
print(rest)           # ['item4', 'item5']
# First Example
fruits = ['banana', 'orange', 'mango', 'lemon','lime','apple']
first_fruit, second_fruit, third_fruit, *rest = lst
print(first_fruit)     # banana
print(second_fruit)    # orange
print(third_fruit)     # mango
print(rest)           # ['lemon','lime','apple']
# Second Example about unpacking list
first, second, third,*rest, tenth = [1,2,3,4,5,6,7,8,9,10]
print(first)          # 1
print(second)         # 2
print(third)          # 3
print(rest)           # [4,5,6,7,8,9]
print(tenth)          # 10
# Third Example about unpacking list
countries = ['Germany', 'France','Belgium','Sweden','Denmark','Finland','Norway','Iceland','Estonia']
gr, fr, bg, sw, *scandic, es = countries
print(gr)
print(fr)
print(bg)
print(sw)
print(scandic)
print(es)
```

### 从列表中切片项目

- 正索引：我们可以通过指定开始、结束和步骤来指定一系列正索引，返回值将是一个新列表。（开始 = 0，结束 = len（lst） - 1（最后一项），步长 = 1 的默认值）

```
fruits = ['banana', 'orange', 'mango', 'lemon']
all_fruits = fruits[0:4] # it returns all the fruits
# this will also give the same result as the one above
all_fruits = fruits[0:] # if we don't set where to stop it takes all the rest
orange_and_mango = fruits[1:3] # it does not include the first index
orange_mango_lemon = fruits[1:]
orange_and_lemon = fruits[::2] # here we used a 3rd argument, step. It will take every 2cnd item - ['banana', 'mango']
```

- 负索引：我们可以通过指定开始、结束和步骤来指定一系列负索引，返回值将是一个新列表。

```
fruits = ['banana', 'orange', 'mango', 'lemon']
all_fruits = fruits[-4:] # it returns all the fruits
orange_and_mango = fruits[-3:-1] # it does not include the last index,['orange', 'mango']
orange_mango_lemon = fruits[-3:] # this will give starting from -3 to the end,['orange', 'mango', 'lemon']
reverse_fruits = fruits[::-1] # a negative step will take the list in reverse order,['lemon', 'mango', 'orange', 'banana']
```

### 修改列表

List 是可变或可修改的有序项集合。让我们修改水果列表。

```
fruits = ['banana', 'orange', 'mango', 'lemon']
fruits[0] = 'avocado'
print(fruits)       #  ['avocado', 'orange', 'mango', 'lemon']
fruits[1] = 'apple'
print(fruits)       #  ['avocado', 'apple', 'mango', 'lemon']
last_index = len(fruits) - 1
fruits[last_index] = 'lime'
print(fruits)        #  ['avocado', 'apple', 'mango', 'lime']
```

### 检查列表中的项目

使用 *in* 运算符检查项目是否为列表的成员。请参阅下面的示例。

```
fruits = ['banana', 'orange', 'mango', 'lemon']
does_exist = 'banana' in fruits
print(does_exist)  # True
does_exist = 'lime' in fruits
print(does_exist)  # False
```

### 向列表添加项目

要将项目添加到现有列表的末尾，我们使用方法*append（）。*

```
# syntax
lst = list()
lst.append(item)
fruits = ['banana', 'orange', 'mango', 'lemon']
fruits.append('apple')
print(fruits)           # ['banana', 'orange', 'mango', 'lemon', 'apple']
fruits.append('lime')   # ['banana', 'orange', 'mango', 'lemon', 'apple', 'lime']
print(fruits)
```

### 将项目插入列表

我们可以使用 *insert（）* 方法在列表中的指定索引处插入单个项目。请注意，其他项目将向右移动。*insert（）* 方法需要两个参数：index 和一个要插入的项。

```
# syntax
lst = ['item1', 'item2']
lst.insert(index, item)
fruits = ['banana', 'orange', 'mango', 'lemon']
fruits.insert(2, 'apple') # insert apple between orange and mango
print(fruits)           # ['banana', 'orange', 'apple', 'mango', 'lemon']
fruits.insert(3, 'lime')   # ['banana', 'orange', 'apple', 'lime', 'mango', 'lemon']
print(fruits)
```

### 从列表中删除项目

remove 方法从列表中删除指定的项

```
# syntax
lst = ['item1', 'item2']
lst.remove(item)
fruits = ['banana', 'orange', 'mango', 'lemon', 'banana']
fruits.remove('banana')
print(fruits)  # ['orange', 'mango', 'lemon', 'banana'] - this method removes the first occurrence of the item in the list
fruits.remove('lemon')
print(fruits)  # ['orange', 'mango', 'banana']
```

### 使用 pop 删除项目

*pop（）* 方法删除指定的索引（如果未指定索引，则删除最后一项）：

```
# syntax
lst = ['item1', 'item2']
lst.pop()       # last item
lst.pop(index)
fruits = ['banana', 'orange', 'mango', 'lemon']
fruits.pop()
print(fruits)       # ['banana', 'orange', 'mango']

fruits.pop(0)
print(fruits)       # ['orange', 'mango']
```

### 使用 del 删除项目

*del* 关键字删除指定的索引，它还可用于删除索引范围内的项目。它也可以完全删除列表

```
# syntax
lst = ['item1', 'item2']
del lst[index] # only a single item
del lst        # to delete the list completely
fruits = ['banana', 'orange', 'mango', 'lemon', 'kiwi', 'lime']
del fruits[0]
print(fruits)       # ['orange', 'mango', 'lemon', 'kiwi', 'lime']
del fruits[1]
print(fruits)       # ['orange', 'lemon', 'kiwi', 'lime']
del fruits[1:3]     # this deletes items between given indexes, so it does not delete the item with index 3!
print(fruits)       # ['orange', 'lime']
del fruits
print(fruits)       # This should give: NameError: name 'fruits' is not defined
```

### 清除列表项

*clear（）* 方法清空列表：

```
# syntax
lst = ['item1', 'item2']
lst.clear()
fruits = ['banana', 'orange', 'mango', 'lemon']
fruits.clear()
print(fruits)       # []
```

### 复制列表

可以通过通过以下方式将列表重新分配给新变量来复制列表：list2 = list1。现在，list2 是 list1 的引用，我们在 list2 中所做的任何更改也会修改原来的 list2。但是在很多情况下，我们不喜欢修改原件，而是喜欢拥有不同的副本。避免上述问题的一种方法是使用 *copy（）。*

```
# syntax
lst = ['item1', 'item2']
lst_copy = lst.copy()
fruits = ['banana', 'orange', 'mango', 'lemon']
fruits_copy = fruits.copy()
print(fruits_copy)       # ['banana', 'orange', 'mango', 'lemon']
```

### 联接列表

在 Python 中，有几种方法可以连接或连接两个或多个列表。

- 加号运算符 （+）

```
# syntax
list3 = list1 + list2
positive_numbers = [1, 2, 3, 4, 5]
zero = [0]
negative_numbers = [-5,-4,-3,-2,-1]
integers = negative_numbers + zero + positive_numbers
print(integers) # [-5, -4, -3, -2, -1, 0, 1, 2, 3, 4, 5]
fruits = ['banana', 'orange', 'mango', 'lemon']
vegetables = ['Tomato', 'Potato', 'Cabbage', 'Onion', 'Carrot']
fruits_and_vegetables = fruits + vegetables
print(fruits_and_vegetables ) # ['banana', 'orange', 'mango', 'lemon', 'Tomato', 'Potato', 'Cabbage', 'Onion', 'Carrot']
```

- 使用 extend（） 方法连接 *extend（）* 方法允许在列表中附加列表。请参阅下面的示例。

```
# syntax
list1 = ['item1', 'item2']
list2 = ['item3', 'item4', 'item5']
list1.extend(list2)
num1 = [0, 1, 2, 3]
num2= [4, 5, 6]
num1.extend(num2)
print('Numbers:', num1) # Numbers: [0, 1, 2, 3, 4, 5, 6]
negative_numbers = [-5,-4,-3,-2,-1]
positive_numbers = [1, 2, 3,4,5]
zero = [0]

negative_numbers.extend(zero)
negative_numbers.extend(positive_numbers)
print('Integers:', negative_numbers) # Integers: [-5, -4, -3, -2, -1, 0, 1, 2, 3, 4, 5]
fruits = ['banana', 'orange', 'mango', 'lemon']
vegetables = ['Tomato', 'Potato', 'Cabbage', 'Onion', 'Carrot']
fruits.extend(vegetables)
print('Fruits and vegetables:', fruits ) # Fruits and vegetables: ['banana', 'orange', 'mango', 'lemon', 'Tomato', 'Potato', 'Cabbage', 'Onion', 'Carrot']
```

### 对列表中的项目进行计数

*count（）* 方法返回项目在列表中出现的次数：

```
# syntax
lst = ['item1', 'item2']
lst.count(item)
fruits = ['banana', 'orange', 'mango', 'lemon']
print(fruits.count('orange'))   # 1
ages = [22, 19, 24, 25, 26, 24, 25, 24]
print(ages.count(24))           # 3
```

### 查找项的索引

*index（）* 方法返回列表中项的索引：

```
# syntax
lst = ['item1', 'item2']
lst.index(item)
fruits = ['banana', 'orange', 'mango', 'lemon']
print(fruits.index('orange'))   # 1
ages = [22, 19, 24, 25, 26, 24, 25, 24]
print(ages.index(24))           # 2, the first occurrence
```

### 反转列表

*reverse（）* 方法颠倒了列表的顺序。

```
# syntax
lst = ['item1', 'item2']
lst.reverse()
fruits = ['banana', 'orange', 'mango', 'lemon']
fruits.reverse()
print(fruits) # ['lemon', 'mango', 'orange', 'banana']
ages = [22, 19, 24, 25, 26, 24, 25, 24]
ages.reverse()
print(ages) # [24, 25, 24, 26, 25, 24, 19, 22]
```

### 对列表项进行排序

要对列表进行排序，我们可以使用 *sort*（） 方法或 *sorted（）* 内置函数。*sort（）* 方法按升序对列表项重新排序并修改原始列表。如果 *sort（）* 方法反向的参数等于 true，它将按降序排列列表。

- sort（）：此方法修改原始列表

  ```
  # syntax
  lst = ['item1', 'item2']
  lst.sort()                # ascending
  lst.sort(reverse=True)    # descending
  ```

  **例：**

  ```
  fruits = ['banana', 'orange', 'mango', 'lemon']
  fruits.sort()
  print(fruits)             # sorted in alphabetical order, ['banana', 'lemon', 'mango', 'orange']
  fruits.sort(reverse=True)
  print(fruits) # ['orange', 'mango', 'lemon', 'banana']
  ages = [22, 19, 24, 25, 26, 24, 25, 24]
  ages.sort()
  print(ages) #  [19, 22, 24, 24, 24, 25, 25, 26]
  
  ages.sort(reverse=True)
  print(ages) #  [26, 25, 25, 24, 24, 24, 22, 19]
  ```

  sorted（）： 返回有序列表而不修改原始列表 **示例：**

  ```
  fruits = ['banana', 'orange', 'mango', 'lemon']
  print(sorted(fruits))   # ['banana', 'lemon', 'mango', 'orange']
  # Reverse order
  fruits = ['banana', 'orange', 'mango', 'lemon']
  fruits = sorted(fruits,reverse=True)
  print(fruits)     # ['orange', 'mango', 'lemon', 'banana']
  ```

🌕 你很勤奋，你已经取得了很多成就。您刚刚完成了第 5 天的挑战，并且您距离通往伟大的道路只有 5 步之遥。现在做一些关于你的大脑和肌肉的运动。

## 💻 练习：第5天

### 练习：1级

1. 声明空列表

2. 声明包含 5 个以上项目的列表

3. 查找列表的长度

4. 获取列表的第一项、中间项和最后一项

5. 声明一个名为mixed_data_types的列表，输入您的（姓名，年龄，身高，婚姻状况，地址）

6. 声明一个名为 it_companies 的列表变量，并分配初始值 Facebook、Google、Microsoft、Apple、IBM、Oracle 和 Amazon。

7. 使用 *print（）* 打印列表

8. 打印列表中的公司数量

9. 打印第一个、中间和最后一个公司

10. 修改其中一家公司后打印列表

11. 将 IT 公司添加到it_companies

12. 在公司列表中间插入 IT 公司

13. 将其中一个it_companies名称更改为大写（IBM 除外！

14. 使用字符串 '#;it_companies'

15. 检查it_companies列表中是否存在某个公司。

16. 使用 sort（） 方法对列表进行排序

17. 使用 reverse（） 方法按降序反转列表

18. 从列表中剔除前 3 家公司

19. 从列表中切出最后 3 家公司

20. 从列表中切出中间的 IT 公司或公司

21. 从列表中删除第一家 IT 公司

22. 从列表中删除中间 IT 公司或公司

23. 从列表中删除最后一家 IT 公司

24. 从列表中删除所有 IT 公司

25. 销毁 IT 公司列表

26. 加入以下列表：

    ```
    front_end = ['HTML', 'CSS', 'JS', 'React', 'Redux']
    back_end = ['Node','Express', 'MongoDB']
    ```

27. 在加入问题 26 中的列表后。复制联接列表并将其分配给变量full_stack。然后在Redux之后插入Python和SQL。

### 练习：2级

1. 以下是10名学生年龄的列表：

```
ages = [19, 22, 19, 24, 20, 25, 26, 24, 25, 24]
```

- 对列表进行排序并查找最小和最大年龄
- 再次将最小年龄和最大年龄添加到列表中
- 求年龄中位数（一个中间项或两个中间项除以二）
- 求平均年龄（所有项目的总和除以其编号）
- 查找年龄范围（最大减去最小值）
- 比较（最小 - 平均值）和（最大值 - 平均值）的值，使用 *abs（）* 方法

1. 在国家/[地区列表中查找中间国家/](https://gitee.com/link?target=https%3A%2F%2Fgithub.com%2FAsabeneh%2F30-Days-Of-Python%2Ftree%2Fmaster%2Fdata%2Fcountries.py)地区
2. 将国家/地区列表分成两个相等的列表，如果上半年没有多一个国家。
3. ['China', 'Russia', 'USA', 'Finland', 'Sweden', 'Norway', 'Denmark'].解开前三个国家的包装，其余的作为scandic国家