- 第四天
  - 字符串
    - [创建字符串](#创建字符串)
    - [字符串串联](#字符串串联)
    - [字符串中的转义序列](#字符串中的转义序列)
    - 字符串格式
      - [旧式字符串格式（% 运算符）](#旧式字符串格式（% 运算符）)
      - [新样式字符串格式（str.format）](#新样式字符串格式（str.format）)
      - [字符串插值 / f 字符串 （Python 3.6+）](#字符串插值 / f 字符串 （Python 3.6+）)
    - 作为字符序列的 Python 字符串
      - [解压缩角色](#解压缩角色)
      - [按索引访问字符串中的字符](#按索引访问字符串中的字符)
      - [切片 Python 字符串](#切片 Python 字符串)
      - [反转字符串](#反转字符串)
      - [切片时跳过字符](#切片时跳过字符)
    - [字符串方法](#字符串方法)
  - [💻 练习 - 第 4 天](#💻 练习 - 第 4 天)

# 第四天

## 字符串

文本是字符串数据类型。任何写为文本的数据类型都是字符串。单引号、双引号或三引号下的任何数据都是字符串。有不同的字符串方法和内置函数来处理字符串数据类型。若要检查字符串的长度，请使用 len（） 方法。

### 创建字符串

```
letter = 'P'                # A string could be a single character or a bunch of texts
print(letter)               # P
print(len(letter))          # 1
greeting = 'Hello, World!'  # String could be made using a single or double quote,"Hello, World!"
print(greeting)             # Hello, World!
print(len(greeting))        # 13
sentence = "I hope you are enjoying 30 days of Python Challenge"
print(sentence)
```

多行字符串是使用三重单引号 （''） 或三重双引号 （“”“） 创建的。请参阅下面的示例。

```
multiline_string = '''I am a teacher and enjoy teaching.
I didn't find anything as rewarding as empowering people.
That is why I created 30 days of python.'''
print(multiline_string)

# Another way of doing the same thing
multiline_string = """I am a teacher and enjoy teaching.
I didn't find anything as rewarding as empowering people.
That is why I created 30 days of python."""
print(multiline_string)
```

### 字符串串联

我们可以将字符串连接在一起。合并或连接字符串称为串联。请参阅以下示例：

```
first_name = 'Asabeneh'
last_name = 'Yetayeh'
space = ' '
full_name = first_name  +  space + last_name
print(full_name) # Asabeneh Yetayeh
# Checking the length of a string using len() built-in function
print(len(first_name))  # 8
print(len(last_name))   # 7
print(len(first_name) > len(last_name)) # True
print(len(full_name)) # 16
```

### 字符串中的转义序列

在Python和其他编程语言中，\后跟一个字符是一个转义序列。让我们看看最常见的转义字符：

- \n：换行符
- \t：制表符表示（8 个空格）
- \\：反斜杠
- \'：单引号 （'）
- \“：双引号 （”）

现在，让我们通过示例查看上述转义序列的用法。

```
print('I hope everyone is enjoying the Python Challenge.\nAre you ?') # line break
print('Days\tTopics\tExercises') # adding tab space or 4 spaces 
print('Day 1\t3\t5')
print('Day 2\t3\t5')
print('Day 3\t3\t5')
print('Day 4\t3\t5')
print('This is a backslash  symbol (\\)') # To write a backslash
print('In every programming language it starts with \"Hello, World!\"') # to write a double quote inside a single quote

# output
I hope every one is enjoying the Python Challenge.
Are you ?
Days	Topics	Exercises
Day 1	5	    5
Day 2	6	    20
Day 3	5	    23
Day 4	1	    35
This is a backslash  symbol (\)
In every programming language it starts with "Hello, World!"
```

### 字符串格式

#### 旧式字符串格式（% 运算符）

在 Python 中，有很多格式化字符串的方法。在本节中，我们将介绍其中的一些。 “%”运算符用于格式化包含在“元组”（固定大小列表）中的一组变量，以及格式字符串，其中包含普通文本和“参数说明符”，特殊符号，如“%s”，“%d”，“%f”，“%。位数f”。

- %s - 字符串（或任何具有字符串表示形式的对象，如数字）
- %d - 整数
- %f - 浮点数
- "%.位数f“ - 具有固定精度的浮点数

```
# Strings only
first_name = 'Asabeneh'
last_name = 'Yetayeh'
language = 'Python'
formated_string = 'I am %s %s. I teach %s' %(first_name, last_name, language)
print(formated_string)

# Strings  and numbers
radius = 10
pi = 3.14
area = pi * radius ** 2
formated_string = 'The area of circle with a radius %d is %.2f.' %(radius, area) # 2 refers the 2 significant digits after the point

python_libraries = ['Django', 'Flask', 'NumPy', 'Matplotlib','Pandas']
formated_string = 'The following are python libraries:%s' % (python_libraries)
print(formated_string) # "The following are python libraries:['Django', 'Flask', 'NumPy', 'Matplotlib','Pandas']"
```

#### 新样式字符串格式（str.format）

这种格式在 Python 版本 3 中引入。

```
first_name = 'Asabeneh'
last_name = 'Yetayeh'
language = 'Python'
formated_string = 'I am {} {}. I teach {}'.format(first_name, last_name, language)
print(formated_string)
a = 4
b = 3

print('{} + {} = {}'.format(a, b, a + b))
print('{} - {} = {}'.format(a, b, a - b))
print('{} * {} = {}'.format(a, b, a * b))
print('{} / {} = {:.2f}'.format(a, b, a / b)) # limits it to two digits after decimal
print('{} % {} = {}'.format(a, b, a % b))
print('{} // {} = {}'.format(a, b, a // b))
print('{} ** {} = {}'.format(a, b, a ** b))

# output
4 + 3 = 7
4 - 3 = 1
4 * 3 = 12
4 / 3 = 1.33
4 % 3 = 1
4 // 3 = 1
4 ** 3 = 64

# Strings  and numbers
radius = 10
pi = 3.14
area = pi * radius ** 2
formated_string = 'The area of a circle with a radius {} is {:.2f}.'.format(radius, area) # 2 digits after decimal
print(formated_string)
```

#### 字符串插值 / f 字符串 （Python 3.6+）

另一种新的字符串格式是字符串插值，f 字符串。字符串以 f 开头，我们可以将数据注入到相应的位置。

```
a = 4
b = 3
print(f'{a} + {b} = {a +b}')
print(f'{a} - {b} = {a - b}')
print(f'{a} * {b} = {a * b}')
print(f'{a} / {b} = {a / b:.2f}')
print(f'{a} % {b} = {a % b}')
print(f'{a} // {b} = {a // b}')
print(f'{a} ** {b} = {a ** b}')
```

### 作为字符序列的 Python 字符串

Python 字符串是字符序列，与其他 Python 有序对象序列（列表和元组）共享其基本访问方法。从字符串中提取单个字符（以及从任何序列中提取单个成员）的最简单方法是将它们解压缩到相应的变量中。

#### 解压缩角色

```
language = 'Python'
a,b,c,d,e,f = language # unpacking sequence characters into variables
print(a) # P
print(b) # y
print(c) # t
print(d) # h
print(e) # o
print(f) # n
```

#### 按索引访问字符串中的字符

在编程中，计数从零开始。因此，字符串的第一个字母位于零索引处，字符串的最后一个字母是字符串的长度减去 1。

![String index](https://gitee.com/tonybearpan/Thirty-Days-Of-Python/raw/master/images/string_index.png)

```
language = 'Python'
first_letter = language[0]
print(first_letter) # P
second_letter = language[1]
print(second_letter) # y
last_index = len(language) - 1
last_letter = language[last_index]
print(last_letter) # n
```

如果我们想从右端开始，我们可以使用负索引。-1 是最后一个索引。

```
language = 'Python'
last_letter = language[-1]
print(last_letter) # n
second_last = language[-2]
print(second_last) # o
```

#### 切片 Python 字符串

在python中，我们可以将字符串切成子字符串。

```
language = 'Python'
first_three = language[0:3] # starts at zero index and up to 3 but not include 3
print(first_three) #Pyt
last_three = language[3:6]
print(last_three) # hon
# Another way
last_three = language[-3:]
print(last_three)   # hon
last_three = language[3:]
print(last_three)   # hon
```

#### 反转字符串

我们可以轻松地在 python 中反转字符串。

```
greeting = 'Hello, World!'
print(greeting[::-1]) # !dlroW ,olleH
```

#### 切片时跳过字符

通过将step参数传递给slice方法，可以在切片时跳过字符。

```
language = 'Python'
pto = language[0:6:2] #
print(pto) # Pto
```

### 字符串方法

有许多字符串方法允许我们格式化字符串。请参阅以下示例中的一些字符串方法：

- capitalize（）：将字符串的第一个字符转换为大写字母

```
challenge = 'thirty days of python'
print(challenge.capitalize()) # 'Thirty days of python'
```

- count（）：返回字符串中子字符串的出现次数，count（子字符串，开始=..，结束=..）。开始是计数的起始索引，结束是最后一个要计数的索引。

```
challenge = 'thirty days of python'
print(challenge.count('y')) # 3
print(challenge.count('y', 7, 14)) # 1, 
print(challenge.count('th')) # 2`
```

- endswith（）：检查字符串是否以指定的结尾结尾

```
challenge = 'thirty days of python'
print(challenge.endswith('on'))   # True
print(challenge.endswith('tion')) # False
```

- expandtabs（）：将制表符替换为空格，默认制表符大小为 8。它需要选项卡大小参数

```
challenge = 'thirty\tdays\tof\tpython'
print(challenge.expandtabs())   # 'thirty  days    of      python'
print(challenge.expandtabs(10)) # 'thirty    days      of        python'
```

- find（）：返回子字符串第一次出现的索引，如果未找到则返回 -1

```
challenge = 'thirty days of python'
print(challenge.find('y'))  # 16
print(challenge.find('th')) # 17
```

- rfind（）：返回子字符串最后一次出现的索引，如果未找到则返回 -1

```
challenge = 'thirty days of python'
print(challenge.rfind('y'))  # 5
print(challenge.rfind('th')) # 1
```

- format（）：将字符串格式化为更好的输出
  有关字符串格式的更多信息，请查看此[链接](https://gitee.com/link?target=https%3A%2F%2Fwww.programiz.com%2Fpython-programming%2Fmethods%2Fstring%2Fformat)

```
first_name = 'Asabeneh'
last_name = 'Yetayeh'
age = 250
job = 'teacher'
country = 'Finland'
sentence = 'I am {} {}. I am a {}. I am {} years old. I live in {}.'.format(first_name, last_name, age, job, country)
print(sentence) # I am Asabeneh Yetayeh. I am 250 years old. I am a teacher. I live in Finland.

radius = 10
pi = 3.14
area = pi * radius ** 2
result = 'The area of a circle with radius {} is {}'.format(str(radius), str(area))
print(result) # The area of a circle with radius 10 is 314
```

- index（）：返回子字符串的最低索引，其他参数指示起始和结束索引（默认值为 0，字符串长度为 - 1）。如果未找到子字符串，则会引发 valueError。

```
challenge = 'thirty days of python'
sub_string = 'da'
print(challenge.index(sub_string))  # 7
print(challenge.index(sub_string, 9)) # error
```

- rindex（）：返回子字符串的最高索引，其他参数指示起始和结束索引（默认值为 0，字符串长度为 - 1）

```
challenge = 'thirty days of python'
sub_string = 'da'
print(challenge.rindex(sub_string))  # 8
print(challenge.rindex(sub_string, 9)) # error
```

- isalnum（）：检查字母数字字符

```
challenge = 'ThirtyDaysPython'
print(challenge.isalnum()) # True

challenge = '30DaysPython'
print(challenge.isalnum()) # True

challenge = 'thirty days of python'
print(challenge.isalnum()) # False, space is not an alphanumeric character

challenge = 'thirty days of python 2019'
print(challenge.isalnum()) # False
```

- isalpha（）：检查是否所有字符串元素都是字母字符（a-z 和 A-Z）

```
challenge = 'thirty days of python'
print(challenge.isalpha()) # False, space is once again excluded
challenge = 'ThirtyDaysPython'
print(challenge.isalpha()) # True
num = '123'
print(num.isalpha())      # False
```

- isdecimal（）：检查字符串中的所有字符是否都是十进制 （0-9）

```
challenge = 'thirty days of python'
print(challenge.isdecimal())  # False
challenge = '123'
print(challenge.isdecimal())  # True
challenge = '\u00B2'
print(challenge.isdigit())   # False
challenge = '12 3'
print(challenge.isdecimal())  # False, space not allowed
```

- isdigit（）：检查字符串中的所有字符是否都是数字（0-9 和其他一些 unicode 字符表示数字）

```
challenge = 'Thirty'
print(challenge.isdigit()) # False
challenge = '30'
print(challenge.isdigit())   # True
challenge = '\u00B2'
print(challenge.isdigit())   # True
```

- isnumeric（）：检查字符串中的所有字符是否与数字或数字相关（就像isdigit（），只接受更多的符号，如1/2）

```
num = '10'
print(num.isnumeric()) # True
num = '\u00BD' # ½
print(num.isnumeric()) # True
num = '10.5'
print(num.isnumeric()) # False
```

- isidentifier（）：检查有效的标识符 - 它检查字符串是否是有效的变量名

```
challenge = '30DaysOfPython'
print(challenge.isidentifier()) # False, because it starts with a number
challenge = 'thirty_days_of_python'
print(challenge.isidentifier()) # True
```

- islower（）：检查字符串中的所有字母字符是否都是小写的

```
challenge = 'thirty days of python'
print(challenge.islower()) # True
challenge = 'Thirty days of python'
print(challenge.islower()) # False
```

- isupper（）：检查字符串中的所有字母字符是否都是大写的

```
challenge = 'thirty days of python'
print(challenge.isupper()) #  False
challenge = 'THIRTY DAYS OF PYTHON'
print(challenge.isupper()) # True
```

- join（）：返回一个串联字符串

```
web_tech = ['HTML', 'CSS', 'JavaScript', 'React']
result = ' '.join(web_tech)
print(result) # 'HTML CSS JavaScript React'
web_tech = ['HTML', 'CSS', 'JavaScript', 'React']
result = '# '.join(web_tech)
print(result) # 'HTML# CSS# JavaScript# React'
```

- strip（）：删除从字符串开头和结尾开始的所有给定字符

```
challenge = 'thirty days of pythoonnn'
print(challenge.strip('noth')) # 'irty days of py'
```

- replace（）：用给定的字符串替换子字符串

```
challenge = 'thirty days of python'
print(challenge.replace('python', 'coding')) # 'thirty days of coding'
```

- split（）：拆分字符串，使用给定的字符串或空格作为分隔符

```
challenge = 'thirty days of python'
print(challenge.split()) # ['thirty', 'days', 'of', 'python']
challenge = 'thirty, days, of, python'
print(challenge.split(', ')) # ['thirty', 'days', 'of', 'python']
```

- title（）：返回一个标题大小写字符串

```
challenge = 'thirty days of python'
print(challenge.title()) # Thirty Days Of Python
```

- swapcase（）：将所有大写字符转换为小写，将所有小写字符转换为大写字符

```
challenge = 'thirty days of python'
print(challenge.swapcase())   # THIRTY DAYS OF PYTHON
challenge = 'Thirty Days Of Python'
print(challenge.swapcase())  # tHIRTY dAYS oF pYTHON
```

- startswith（）：检查字符串是否以指定的字符串开头

```
challenge = 'thirty days of python'
print(challenge.startswith('thirty')) # True

challenge = '30 days of python'
print(challenge.startswith('thirty')) # False
```

🌕 你是一个非凡的人，你有一个非凡的潜力。你刚刚完成了第 4 天的挑战，你已经四步一步地走向伟大。现在做一些关于你的大脑和肌肉的运动。

## 💻 练习 - 第 4 天

1. 将字符串“Thirty”、“Days”、“Of”、“Python”连接到单个字符串“Thirty Days of Python”。

2. 将字符串“编码”、“为”、“全部”连接成一个字符串“为所有人编码”。

3. 声明一个名为 company 的变量，并将其分配给初始值“Coding For All”。

4. 使用 *print（）* 打印变量公司。

5. 使用 *len*（） 方法和 *print（）* 打印公司字符串的长度。

6. 使用 *upper（）* 方法将所有字符更改为大写字母。

7. 使用 *lower（）* 方法将所有字符更改为小写字母。

8. 使用 capitalize（）， title（）， swapcase（） 方法来格式化字符串 *Coding For All* 的值。

9. 剪切（切片）出*“编码为所有人”*字符串的第一个单词。

10. 检查编码为全部字符串是否包含单词*编码*使用方法索引，查找或其他方法。

11. 将字符串“Coding For All”中的单词 coding 替换为 Python。

12. 使用 replace 方法或其他方法将 Python for Everyone 更改为 Python for All。

13. 使用空格作为分隔符（split（））拆分字符串“Coding For All”。

14. “Facebook，Google，Microsoft，Apple，IBM，Oracle，Amazon”将字符串拆分为逗号。

15. 字符串*“全民编码”*中索引 0 处的字符是什么。

16. 字符串的最后一个索引是什么 *编码*所有人.

17. “全民编码”字符串中索引 10 处的字符是什么。

18. 为名称“Python For Everyone”创建一个首字母缩略词或缩写。

19. 为名称“全民编码”创建一个首字母缩略词或缩写。

20. 使用索引确定 C 在“全民编码”中首次出现的位置。

21. 使用索引确定 F 在“全民编码”中首次出现的位置。

22. 使用 rfind 确定 l 在“为所有人编码”中最后一次出现的位置。

23. 使用索引或查找来查找以下句子中单词“因为”第一次出现的位置：“你不能以 因为 因为 因为是连词结束句子”

24. 使用 rindex 查找单词最后一个出现的位置，因为在以下句子中：“你不能以 因为 因为 因为是连词结束句子”

25. 在下面的句子中切掉短语“因为因为”：“你不能用因为结束一个句子，因为因为是一个连词”

26. 在下面的句子中找到单词“因为”第一次出现的位置：“你不能用 因为因为 因为是连词结束句子”

27. 在下面的句子中切掉短语“因为因为”：“你不能用因为结束一个句子，因为因为是一个连词”

28. “全民编码”是否以子字符串*编码*开头？

29. “全民编码”是否以子字符串*编码*结尾？

30. ' 编码所有人 ' ，删除给定字符串中的左右尾随空格。

31. 当我们使用方法 isidentifier（） 时，以下哪一个变量返回 True：

    - 30天蟒蛇
    - thirty_days_of_python

32. 以下列表包含一些 python 库的名称：['Django'， 'Flask'， 'Bottle'， 'Pyramid'， 'Falcon']。使用带有空格字符串的哈希加入列表。

33. 使用新的行转义序列分隔以下句子。

    ```
    I am enjoying this challenge.
    I just wonder what is next.
    ```

34. 使用制表符转义序列编写以下行。

    ```
    Name      Age     Country   City
    Asabeneh  250     Finland   Helsinki
    ```

35. 使用字符串格式设置方法显示以下内容：

```
radius = 10
area = 3.14 * radius ** 2
The area of a circle with radius 10 is 314 meters square.
```

1. 使用字符串格式设置方法执行以下操作：

```
8 + 6 = 14
8 - 6 = 2
8 * 6 = 48
8 / 6 = 1.33
8 % 6 = 2
8 // 6 = 1
8 ** 6 = 262144
```