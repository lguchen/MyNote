- 第六天：
  - 元组
    - [创建元组](#创建元组)
    - [元组长度](#元组长度)
    - [访问元组项](#访问元组项)
    - [切片元组](#切片元组)
    - [将元组更改为列表](#将元组更改为列表)
    - [检查元组中的项目](#检查元组中的项目)
    - [加入元组](#加入元组)
    - [删除元组](#删除元组)
  - 💻 练习：第6天
    - [练习：1级](#练习：1级)
    - [练习：2级](#练习：2级)

# 第六天：

## 元组

元组是不同数据类型的集合，它们是有序且不可更改（不可变的）。元组用圆括号 （） 编写。创建元组后，我们无法更改其值。我们不能在元组中使用添加、插入、删除方法，因为它是不可修改的（可变的）。与列表不同，元组的方法很少。元组相关方法：

- tuple（）：创建一个空元组
- count（）：计算元组中指定项的数量
- index（）：查找元组中指定项的索引
- - 运算符：连接两个或多个元组并创建新元组

### 创建元组

- 空元组：创建空元组

  ```
  # syntax
  empty_tuple = ()
  # or using the tuple constructor
  empty_tuple = tuple()
  ```

- 具有初始值的元组

  ```
  # syntax
  tpl = ('item1', 'item2','item3')
  ```

  ```
  fruits = ('banana', 'orange', 'mango', 'lemon')
  ```

### 元组长度

我们使用 *len（）* 方法来获取元组的长度。

```
# syntax
tpl = ('item1', 'item2', 'item3')
len(tpl)
```

### 访问元组项

- 正索引 与列表数据类型类似，我们使用正索引或负索引来访问元组项。![访问元组项](img\6.png)

  ```
  # Syntax
  tpl = ('item1', 'item2', 'item3')
  first_item = tpl[0]
  second_item = tpl[1]
  ```

  ```
  fruits = ('banana', 'orange', 'mango', 'lemon')
  first_fruit = fruits[0]
  second_fruit = fruits[1]
  last_index =len(fruits) - 1
  last_fruit = fruits[las_index]
  ```

- 负索引 负索引表示从末尾开始，-1 表示最后一项，-2 表示倒数第二项，列表/元组长度的负数表示第一项。![元组负索引](img\6.0.png)

  ```
  # Syntax
  tpl = ('item1', 'item2', 'item3','item4')
  first_item = tpl[-4]
  second_item = tpl[-3]
  ```

  ```
  fruits = ('banana', 'orange', 'mango', 'lemon')
  first_fruit = fruits[-4]
  second_fruit = fruits[-3]
  last_fruit = fruits[-1]
  ```

### 切片元组

我们可以通过指定元组中开始和结束的索引范围来切出子元组，返回值将是具有指定项的新元组。

- 正指数范围

  ```
  # Syntax
  tpl = ('item1', 'item2', 'item3','item4')
  all_items = tpl[0:4]         # all items
  all_items = tpl[0:]         # all items
  middle_two_items = tpl[1:3]  # does not include item at index 3
  ```

  ```
  fruits = ('banana', 'orange', 'mango', 'lemon')
  all_fruits = fruits[0:4]    # all items
  all_fruits= fruits[0:]      # all items
  orange_mango = fruits[1:3]  # doesn't include item at index 3
  orange_to_the_rest = fruits[1:]
  ```

- 负指数范围

  ```
  # Syntax
  tpl = ('item1', 'item2', 'item3','item4')
  all_items = tpl[-4:]         # all items
  middle_two_items = tpl[-3:-1]  # does not include item at index 3 (-1)
  ```

  ```
  fruits = ('banana', 'orange', 'mango', 'lemon')
  all_fruits = fruits[-4:]    # all items
  orange_mango = fruits[-3:-1]  # doesn't include item at index 3
  orange_to_the_rest = fruits[-3:]
  ```

### 将元组更改为列表

我们可以将元组更改为列表，将列表更改为元组。元组是不可变的，如果我们想修改一个元组，我们应该把它改成一个列表。

```
# Syntax
tpl = ('item1', 'item2', 'item3','item4')
lst = list(tpl)
fruits = ('banana', 'orange', 'mango', 'lemon')
fruits = list(fruits)
fruits[0] = 'apple'
print(fruits)     # ['apple', 'orange', 'mango', 'lemon']
fruits = tuple(fruits)
print(fruits)     # ('apple', 'orange', 'mango', 'lemon')
```

### 检查元组中的项目

我们可以使用 *in* 检查元组中是否存在一个项目，它返回一个布尔值。

```
# Syntax
tpl = ('item1', 'item2', 'item3','item4')
'item2' in tpl # True
fruits = ('banana', 'orange', 'mango', 'lemon')
print('orange' in fruits) # True
print('apple' in fruits) # False
fruits[0] = 'apple' # TypeError: 'tuple' object does not support item assignment
```

### 加入元组

我们可以使用 + 运算符连接两个或多个元组

```
# syntax
tpl1 = ('item1', 'item2', 'item3')
tpl2 = ('item4', 'item5','item6')
tpl3 = tpl1 + tpl2
fruits = ('banana', 'orange', 'mango', 'lemon')
vegetables = ('Tomato', 'Potato', 'Cabbage','Onion', 'Carrot')
fruits_and_vegetables = fruits + vegetables
```

### 删除元组

无法删除元组中的单个项目，但可以使用 *del* 删除元组本身。

```
# syntax
tpl1 = ('item1', 'item2', 'item3')
del tpl1
fruits = ('banana', 'orange', 'mango', 'lemon')
del fruits
```

🌕 你太勇敢了，你走到了这一步。你刚刚完成了第6天的挑战，你已经走上了6步，走向伟大。现在为你的大脑和肌肉做一些运动。

## 💻 练习：第6天

### 练习：1级

1. 创建空元组
2. 创建一个包含您的姐妹和兄弟名字的元组（虚构的兄弟姐妹很好）
3. 加入兄弟姐妹元组并将其分配给兄弟姐妹
4. 你有几个兄弟姐妹？
5. 修改兄弟姐妹元组并添加您的父亲和母亲的名字并将其分配给family_members

### 练习：2级

1. 从family_members中解开兄弟姐妹和父母的包装
2. 创建水果、蔬菜和动物产品元组。联接三个元组并将其分配给名为 food_stuff_tp 的变量。
3. 将关于food_stuff_tp元组更改为food_stuff_lt列表
4. 从food_stuff_tp元组或food_stuff_lt列表中切出中间项或项。
5. 从列表中切出前三项和后三项food_staff_lt
6. 完全删除food_staff_tp元组
7. 检查元组中是否存在项目：

- 检查“爱沙尼亚”是否是北欧国家

- 检查“冰岛”是否是北欧国家

  ```
  nordic_countries = ('Denmark', 'Finland','Iceland', 'Norway', 'Sweden')
  ```