- 📘 第七天
  - 集
    - [创建集](#创建集)
    - [获取设置的长度](#获取设置的长度)
    - [访问集合中的项目](#访问集合中的项目)
    - [检查项目](#检查项目)
    - [将项目添加到集合](#将项目添加到集合)
    - [从集合中删除项目](#从集合中删除项目)
    - [清除集合中的项目](#清除集合中的项目)
    - [删除集](#删除集)
    - [将列表转换为集](#将列表转换为集)
    - [连接集](#连接集)
    - [查找交集项](#查找交集项)
    - [检查子集和超集](#检查子集和超集)
    - [检查两组之间的差异](#检查两组之间的差异)
    - [查找两个集合之间的对称差异](#查找两个集合之间的对称差异)
    - [连接集](#连接集)
  - 💻 练习：第7天
    - [练习：1级](#练习：1级)
    - [练习：2级](#练习：2级)
    - [练习：3级](#练习：3级)

# 📘 第七天

## 集

集是项的集合。让我带你回到你的小学或高中数学课。集合的数学定义也可以应用于Python。Set 是无序和未编制索引的不同元素的集合。在Python中，set用于存储唯一的项，并且可以找到集合之间的*并*集，交集，差分，*对称差分*，子集，超集和*不相交**集*。

### 创建集

我们使用大括号 {} 来创建集合或 *set（）* 内置函数。

- 创建空集

```
# syntax
st = {}
# or
st = set()
```

- 创建包含初始项的集

```
# syntax
st = {'item1', 'item2', 'item3', 'item4'}
```

**例：**

```
# syntax
fruits = {'banana', 'orange', 'mango', 'lemon'}
```

### 获取设置的长度

我们使用 **len（）** 方法来查找集合的长度。

```
# syntax
st = {'item1', 'item2', 'item3', 'item4'}
len(set)
```

**例：**

```
fruits = {'banana', 'orange', 'mango', 'lemon'}
len(fruits)
```

### 访问集合中的项目

我们使用循环来访问项目。我们将在循环部分看到这一点

### 检查项目

检查我们在成员资格运算符*中使用的*列表中是否存在项目。

```
# syntax
st = {'item1', 'item2', 'item3', 'item4'}
print("Does set st contain item3? ", 'item3' in st) # Does set st contain item3? True
```

**例：**

```
fruits = {'banana', 'orange', 'mango', 'lemon'}
print('mango' in fruits ) # True
```

### 将项目添加到集合

创建集合后，我们无法更改任何项目，也可以添加其他项目。

- 使用 *add（）* 添加一个项目

```
# syntax
st = {'item1', 'item2', 'item3', 'item4'}
st.add('item5')
```

**例：**

```
fruits = {'banana', 'orange', 'mango', 'lemon'}
fruits.add('lime')
```

- 使用 update（） 添加多个项目 *update（）* 允许将多个项目添加到一个集合中。*update（）* 采用列表参数。

```
# syntax
st = {'item1', 'item2', 'item3', 'item4'}
st.update(['item5','item6','item7'])
```

**例：**

```
fruits = {'banana', 'orange', 'mango', 'lemon'}
vegetables = ('tomato', 'potato', 'cabbage','onion', 'carrot')
fruits.update(vegetables)
```

### 从集合中删除项目

我们可以使用 *remove（）* 方法从集合中删除一个项目。如果未找到该项，*remove（）* 方法将引发错误，因此最好检查该项是否存在于给定的集合中。但是，*discard（）* 方法不会引发任何错误。

```
# syntax
st = {'item1', 'item2', 'item3', 'item4'}
st.remove('item2')
```

pop（） 方法从列表中删除随机项，并返回已删除项。

**例：**

```
fruits = {'banana', 'orange', 'mango', 'lemon'}
fruits.pop()  # removes a random item from the set
```

如果我们对已删除的项目感兴趣。

```
fruits = {'banana', 'orange', 'mango', 'lemon'}
removed_item = fruits.pop() 
```

### 清除集合中的项目

如果我们想清除或清空集合，我们使用*清除*方法。

```
# syntax
st = {'item1', 'item2', 'item3', 'item4'}
st.clear()
```

**例：**

```
fruits = {'banana', 'orange', 'mango', 'lemon'}
fruits.clear()
print(fruits) # set()
```

### 删除集

如果我们想删除集合本身，我们使用 *del* 运算符。

```
# syntax
st = {'item1', 'item2', 'item3', 'item4'}
del st
```

**例：**

```
fruits = {'banana', 'orange', 'mango', 'lemon'}
del fruits
```

### 将列表转换为集

我们可以将列表转换为设置和设置为列表。将列表转换为集合会删除重复项，并且仅保留唯一项。

```
# syntax
lst = ['item1', 'item2', 'item3', 'item4', 'item1']
st = set(lst)  # {'item2', 'item4', 'item1', 'item3'} - the order is random, because sets in general are unordered
```

**例：**

```
fruits = ['banana', 'orange', 'mango', 'lemon','orange', 'banana']
fruits = set(fruits) # {'mango', 'lemon', 'banana', 'orange'}
```

### 连接集

我们可以使用 *union*（） 或 *update（）* 方法连接两个集合。

- 联盟 此方法返回一个新集合

```
# syntax
st1 = {'item1', 'item2', 'item3', 'item4'}
st2 = {'item5', 'item6', 'item7', 'item8'}
st3 = st1.union(st2)
```

**例：**

```
fruits = {'banana', 'orange', 'mango', 'lemon'}
vegetables = {'tomato', 'potato', 'cabbage','onion', 'carrot'}
print(fruits.union(vegetables)) # {'lemon', 'carrot', 'tomato', 'banana', 'mango', 'orange', 'cabbage', 'potato', 'onion'}
```

- 更新 此方法将集合插入到给定集合中

```
# syntax
st1 = {'item1', 'item2', 'item3', 'item4'}
st2 = {'item5', 'item6', 'item7', 'item8'}
st1.update(st2) # st2 contents are added to st1
```

**例：**

```
fruits = {'banana', 'orange', 'mango', 'lemon'}
vegetables = {'tomato', 'potato', 'cabbage','onion', 'carrot'}
fruits.update(vegetables)
print(fruits) # {'lemon', 'carrot', 'tomato', 'banana', 'mango', 'orange', 'cabbage', 'potato', 'onion'}
```

### 查找交集项

交集返回两个集合中的一组项。查看示例

```
# syntax
st1 = {'item1', 'item2', 'item3', 'item4'}
st2 = {'item3', 'item2'}
st1.intersection(st2) # {'item3', 'item2'}
```

**例：**

```
whole_numbers = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
even_numbers = {0, 2, 4, 6, 8, 10}
whole_numbers.intersection(even_numbers) # {0, 2, 4, 6, 8, 10}

python = {'p', 'y', 't', 'h', 'o','n'}
dragon = {'d', 'r', 'a', 'g', 'o','n'}
python.intersection(dragon)     # {'o', 'n'}
```

### 检查子集和超集

集合可以是其他集合的子集或超集：

- 子集：*issubset（）*
- 超级集：*是超集*

```
# syntax
st1 = {'item1', 'item2', 'item3', 'item4'}
st2 = {'item2', 'item3'}
st2.issubset(st1) # True
st1.issuperset(st2) # True
```

**例：**

```
whole_numbers = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
even_numbers = {0, 2, 4, 6, 8, 10}
whole_numbers.issubset(even_numbers) # False, because it is a super set
whole_numbers.issuperset(even_numbers) # True

python = {'p', 'y', 't', 'h', 'o','n'}
dragon = {'d', 'r', 'a', 'g', 'o','n'}
python.issubset(dragon)     # False
```

### 检查两组之间的差异

它返回两个集合之间的差值。

```
# syntax
st1 = {'item1', 'item2', 'item3', 'item4'}
st2 = {'item2', 'item3'}
st2.difference(st1) # set()
st1.difference(st2) # {'item1', 'item4'} => st1\st2
```

**例：**

```
whole_numbers = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
even_numbers = {0, 2, 4, 6, 8, 10}
whole_numbers.difference(even_numbers) # {1, 3, 5, 7, 9}

python = {'p', 'y', 't', 'o','n'}
dragon = {'d', 'r', 'a', 'g', 'o','n'}
python.difference(dragon)     # {'p', 'y', 't'}  - the result is unordered (characteristic of sets)
dragon.difference(python)     # {'d', 'r', 'a', 'g'}
```

### 查找两个集合之间的对称差异

它返回两个集合之间的对称差值。这意味着它返回一个集合，其中包含两个集合中的所有项，但两个集合中存在的项除外，数学方式为：（A\B） ∪ （B\A）

```
# syntax
st1 = {'item1', 'item2', 'item3', 'item4'}
st2 = {'item2', 'item3'}
# it means (A\B)∪(B\A)
st2.symmetric_difference(st1) # {'item1', 'item4'}
```

**例：**

```
whole_numbers = {0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10}
some_numbers = {1, 2, 3, 4, 5}
whole_numbers.symmetric_difference(some_numbers) # {0, 6, 7, 8, 9, 10}

python = {'p', 'y', 't', 'h', 'o','n'}
dragon = {'d', 'r', 'a', 'g', 'o','n'}
python.symmetric_difference(dragon)  # {'r', 't', 'p', 'y', 'g', 'a', 'd', 'h'}
```

### 连接集

如果两个集合没有一个或多个公共项目，我们称它们为不相交集合。我们可以使用 *isdisjoint（）* 方法检查两个集合是联合的还是不相交的。

```
# syntax
st1 = {'item1', 'item2', 'item3', 'item4'}
st2 = {'item2', 'item3'}
st2.isdisjoint(st1) # False
```

**例：**

```
even_numbers = {0, 2, 4 ,6, 8}
even_numbers = {1, 3, 5, 7, 9}
even_numbers.isdisjoint(odd_numbers) # True, because no common item

python = {'p', 'y', 't', 'h', 'o','n'}
dragon = {'d', 'r', 'a', 'g', 'o','n'}
python.isdisjoint(dragon)  # False, there are common items {'o', 'n'}
```

🌕 你是一颗冉冉升起的新星.您刚刚完成了第 7 天的挑战，并且您领先 7 步走向伟大。现在做一些关于你的大脑和肌肉的运动。

## 💻 练习：第7天

```
# sets
it_companies = {'Facebook', 'Google', 'Microsoft', 'Apple', 'IBM', 'Oracle', 'Amazon'}
A = {19, 22, 24, 20, 25, 26}
B = {19, 22, 20, 25, 26, 24, 28, 27}
age = [22, 19, 24, 25, 26, 24, 25, 24]
```

### 练习：1级

1. 求集合it_companies的长度
2. 将“推特”添加到it_companies
3. 一次将多个 IT 公司插入到设置it_companies
4. 从设置it_companies中删除其中一家公司
5. 删除和丢弃有什么区别

### 练习：2级

1. 加入 A 和 B
2. 查找 A 交叉路口 B
3. 是 B 的子集
4. 是 A 和 B 不相交集合
5. 将 A 与 B 连接，将 B 与 A 连接
6. A和B之间的对称区别是什么
7. 完全删除集

### 练习：3级

1. 将年龄转换为一组并比较列表和集合的长度，哪个更大？
2. 解释以下数据类型之间的区别：字符串、列表、元组和集合
3. *我是一名老师，我喜欢激励和教导人们。*句子中使用了多少个独特的单词？使用拆分方法并设置以获取唯一的单词。