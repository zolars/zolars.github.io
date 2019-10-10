---
title: Python Learning Note
date: 2016-07-13 17:16:48
categories: Study
tags:
- python
toc: true
mathjax: true
---

> 拥有一定C语言和编程基础，学习Python时的随手记。有一部分来自于[『Python入门指南』](http://www.pythondoc.com/pythontutorial3/)，有兴趣最好细致的阅读官方文档。  

<!--more-->

> 环境：Python3.6.1 of OS X 10.12.5(16F73)
> ※：指代这里和C语言有一些不容忽视的区别。

## 基本概念

### 如何加入中文注释？

在文件首加入：`#coding=utf-8`

### 句式

确保在每一行的开始字符前没有空格或者制表符。※

### 逻辑行

默认地，Python希望每行都只使用一个语句，这样使得代码更加易读。
事实上， 我从来没有 在Python程序中使用过或看到过分号。

### 缩进

我的缩进风格：行首四个空格。

## 基本对象

### 对象

记住，Python把在程序中用到的任何东西都称为对象 。这是从广义上说的，我们说“某个对象 ”。

### 数

分为整数、长整数、浮点数、复数，简单易懂。

### 字符串

可以用单引号或双引号指示字符串，在双引号中的字符串与单引号中的字符串的使用完全相同。

字符串是不可变的：这意味着一旦你创造了一个字符串，你就不能再改变它了。※

自然字符串：`r’This is nature\n’`其中的转义符不被处理。

字符串可以使用符号运算。

```python
>>> ’un' ’yes'
’unyes'
>>> 3 * ’un' + 'yes’
'unununyes’
```

简单的，字符串可以被截取（检索）。索引也可以是负数，这将导致从右边开始计算。

```python
>>> word = ‘Python’
>>> word[1]
‘p’
>>> word[5]
’o’
>>> word[-1]
'n'
>>> word[-6]
'P'
```

字符串可以被切片。

```python
>>> word = 'Python'
>>> word[0:2]
'Py'
>>> word[2:5]
'tho'
```

切片的索引有非常有用的默认值；省略的第一个索引默认为零，省略的第二个索引默认为切片的字符串的大小。

```python
>>> word[:2]  ## character from the beginning to position 2 (excluded)
'Py'
>>> word[4:]  ## characters from position 4 (included) to the end
'on'
>>> word[-2:] ## characters from the second-last (included) to the end
'on'
```

-   在Python中没有专门的char数据类型。确实没有需要有这个类型，我相信你不会为此而烦恼。※

-   一定要用自然字符串处理正则表达式。否则会需要使用很多的反斜杠。例如，后向引用符可以 写成'\\1'或r'\\1'。


-   内置函数`len()`返回字符串长度。
    **内置函数`list()`可将字符串转换为列表。**

### 列表

形如：

```python
>>> squares = [1, 4, 9, 16, 25]
>>> print(squares)
[1, 4, 9, 16, 25]
```

列表是可变的，它允许修改元素。也可以对切片赋值，此操作可以改变列表的尺寸，或清空它。

```python
>>> a = [1,2,3,4,5]
>>> a[1:] = a[0:]
>>> print(a)
[1,1,2,3,4,5]
```

-   `list[::-1]`指代的是将list这个列表倒序。

-   允许嵌套列表(创建一个包含其它列表的列表)。

-   对两个列表名直接使用赋值号，仅仅传递地址而不传递数据。※
    例如：

```python
>>> a = [1, 2, 44, 33, 23, 45]
>>> b = a
>>> b[2] = 3
>>> print(a)
[1, 2, 3, 33, 23, 45]
```

需要传递数据时，要赋值列表的一个浅拷贝，如`a[:]`。

### 变量

使用变量时只需要给它们赋一个值，不需要声明或定义数据类型。※

## 表达式

### 运算符

![pic](http://p1o3cbsc1.bkt.clouddn.com/2017-12-28-114217.jpg)

### 额外记住

-   \*\* ：幂乘方。2 \*\* 7得到128。

-   \\ ：取整除。例如4 \\ 3得到1，但是4 \\ 3.0得到1.0。

-   & ：按位与
    0 & 0 = 0
    1 & 0 = 0
    0 & 1 = 0
    1 & 1 = 1
    例如5 & 3即为00000101 & 00000011得到00000001，即为1。

-   | ：按位或
    0 | 0 = 0
    1 | 0 = 1
    0 | 1 = 1
    1 | 1 = 1
    例如5 & 3即为00000101 & 00000011得到00000111，即为7。

-   ^ ：按位异或
    0 ^ 0 = 0
    1 ^ 0 = 1
    0 ^ 1 = 1
    1 ^ 1 = 0

-   ~ ：按位翻转。二进制按位翻转，0 = 1， 1 = 0。

-   `and`，`or`，`not`：布尔“与”，“或”，“非”。※

## 控制流

### `if`语句

```python
if sth. :
    pass
elif sth. :
    pass
else :
    pass
```

-   `elif` ※

### `while`语句

```python
while sth. :
    pass
else :
    pass
```

-   这个可选择的`else`语句的作用是为了使代码具有可读性。一般在使用python的循环查找时：如果找到目标可以`break`跳出循环，此时便不会输出错误；如果未找到目标，便可以利用`else`来做到反馈错误信息。

### for语句

遍历一个序列中所有的元素。

```python
for i in list:
    pass
else:
    pass
```

使用内建的`range`函数生成这个数的序列。`range(a, b, c)`中，a为起始数，b为终止数，c为步长。

```python
for i in range(a):
    pass
else:
    pass
```

-   for语句有一个可选的`else`从句。

### `break`语句

 `break`用于终止循环语句。

-   一个重要的注释是，如果你从`for`或`while`循环中终止，任何对应的循环`else`块将不执行。

### `continue`语句

`continue`语句是从C中借鉴来的，它表示循环继续执行下一次迭代。

### `pass`语句

 `pass`语句什么也不做。它用于那些语法上必须要有什么语句，但程序什么也不做的场合。

```python
>>> while True:
...     pass  # 等待键盘输入
...
```

另一方面，`pass`可以在创建新代码时用来做函数或控制体的占位符。可以让你在更抽象的级别上思考。`pass`可以默默的被忽视。

```python
>>> def initlog(*args):
...     pass   # 提醒去补完程序
...
```

## 函数

### 函数的定义

```python
def name(a, b, c) :
    pass

name(1, 2, 3)
```

### 局部变量

当你在函数定义内声明变量的时候，它们与函数外具有相同名称的其他变量没有任何关系,即变量名称对于函数来说是局部的。

### `global`语句

使用`global`语句可以清楚地表明变量是在外面的块定义的，并且读取或赋值此变量。
没有`global`语句，是不可能为定义在函数外的变量赋值的。

### 默认参数值

```python
def name(a=5, b, c) :
    pass

name(, 2, 3)
```

上面这个范例运行时，形参a=5。

### 关键字参数

形如：

```python
def parrot(voltage, state='a stiff', action='voom', type='Norwegian Blue'):
    print("-- This parrot wouldn't", action, end=' ')
    print("if you put", voltage, "volts through it.")
    print("-- Lovely plumage, the", type)
    print("-- It's", state, "!")
```

调用时使用

```python
parrot(1000)                                          # 1 positional argument
parrot(voltage=1000)                                  # 1 keyword argument
parrot(voltage=1000000, action='VOOOOOM')             # 2 keyword arguments
parrot(action='VOOOOOM', voltage=1000000)             # 2 keyword arguments
parrot('a million', 'bereft of life', 'jump')         # 3 positional arguments
parrot('a thousand', state='pushing up the daisies')  # 1 positional, 1 keyword
```

即可

## 数据结构

### 列表拓展

-   常用的列表处理函数有：

        * `list.append(x)`

          把一个元素添加到列表的结尾，相当于`a[len(a):] = [x]`。

        * `list.extend(x)`

          将一个给定列表中的所有元素都添加到另一个列表中，相当于`a[len(a):] = L`。

        * `list.insert(i, x)`

          在指定位置插入一个元素。第一个参数是准备插入到其前面的那个元素的索引，例如`a.insert(0, x)`会插入到整个列表之前，而`a.insert(len(a), x)`相当于`a.append(x)`。

        * `list.remove(x)`

          删除列表中值为 x 的第一个元素。如果没有这样的元素，就会返回一个错误。

        * `list.pop([i])`

          从列表的指定位置删除元素，并将其返回。**如果没有指定索引，`a.pop()`返回最后一个元素。** 元素随即从列表中被删除（方法中i两边的方括号表示这个参数是可选的，而不是要求你输入一对方括号，你会经常在Python库参考手册中遇到这样的标记）。

        * `list.clear()`

          从列表中删除所有元素。相当于`del a[:]`。

        * `list.index(x)`

          返回列表中第一个值为 x 的元素的索引。如果没有匹配的元素就会返回一个错误。

        * `list.count(x)`

          返回 x 在列表中出现的次数。

        * `list.sort()`

          对列表中的元素就地进行排序。

        * `list.reverse()`

          就地倒排列表中的元素。

        * `list.copy()`

          返回列表的一个浅拷贝。等同于`a[:]`。

-   要实现队列，使用`collections.deque`，它为在首尾两端快速插入和删除而设计。例如：

```python
>>> from collections import deque
>>> queue = deque(["Eric", "John", "Michael"])
>>> queue.append("Terry")           # Terry arrives
>>> queue.append("Graham")          # Graham arrives
>>> queue.popleft()                 # The first to arrive now leaves
'Eric'
>>> queue.popleft()                 # The second to arrive now leaves
'John'
>>> queue                           # Remaining queue in order of arrival
deque(['Michael', 'Terry', 'Graham'])
```

-   列表推导式
    由包含一个表达式的括号组成，表达式后面跟随一个 for 子句，之后可以有零或多个 for 或 if 子句。结果是一个列表，由表达式依据其后面的`for`和`if`子句上下文计算而来的结果构成。

```python
>>> n = [x ** 2 for x in range(10)]
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
>>> m = [(x, y) for x in [1, 2, 3] for y in [3, 1, 4] if x != y]
[(1, 3), (1, 4), (2, 3), (2, 1), (2, 4), (3, 1), (3, 4)]
```

-   嵌套的列表推导式
    列表解析中的第一个表达式可以是任何表达式，包括列表解析。视具体情况集体分析。

### `del`语句

按给定的索引删除列表中一个子项。

`del`也可以删除整个变量，此后再引用被删除的变量名会引发`not defined`错误（直到另一个值赋给它为止）。

### 元组

一个元组由数个逗号分隔的值组成。

元组是不可变的，一般含有不同类型的元素并通过分拆或索引访问。而列表是可变的，它们的元素通常是相同类型的并通过迭代访问。

元组的封装：`a = ('Jack', 1997)`；序列的拆封：`(b, c) = a`

-   定义一个只有一个元素的元组，需要用逗号占位：`a = (1, )`

### 集合

集合是一个无序不重复元素的集。基本功能包括关系测试和消除重复元素。

大括号或`set()`函数可以用来创建集合。注意：想要创建空集合，你必须使用`set()`而不是`set{}`。

类似 列表推导式，这里有一种集合推导式语法:

```python
>>> a = {x for x in 'abracadabra' if x not in 'abc'}
>>> a
{'r', 'd'}
```

### 字典

字典以关键字为索引，关键字可以是任意不可变类型，通常用字符串或数值。理解字典的最佳方式是把它看做无序的key:value 对集合，键必须是互不相同的（在同一个字典之内）。一对大括号创建一个空的字典：`{}`。初始化列表时，在大括号内放置一组逗号分隔的键：值对，这也是字典输出的方式。

字典的主要操作是依据键来存储和析取值。也可以用`del`来删除key:value对。如果你用一个已经存在的关键字存储值，以前为该关键字分配的值就会被遗忘。试图从一个不存在的键中取值会导致错误。

对一个字典执行`list(d.keys())`将返回一个字典中所有关键字组成的无序列表（如果你想要排序，只需使用`sorted(d.keys())`）。使用`in`可以检查字典中是否存在某个关键字。

-   这里是使用字典的一个小示例:

```python
>>> tel = {'jack': 4098, 'sape': 4139}
>>> tel['guido'] = 4127
>>> tel
{'sape': 4139, 'guido': 4127, 'jack': 4098}
>>> tel['jack']
4098
>>> del tel['sape']
>>> tel['irv'] = 4127
>>> tel
{'guido': 4127, 'irv': 4127, 'jack': 4098}
>>> list(tel.keys())
['irv', 'guido', 'jack']
>>> sorted(tel.keys())
['guido', 'irv', 'jack']
>>> 'guido' in tel
True
>>> 'jack' not in tel
False
```

-   dict() 构造函数可以直接从 key-value 对中创建字典。

```python
>>> dict([('sape', 4139), ('guido', 4127), ('jack', 4098)])
{'sape': 4139, 'jack': 4098, 'guido': 4127}
```

-   此外，字典推导式可以从任意的键值表达式中创建字典。

```python
>>> {x: x**2 for x in (2, 4, 6)}
{2: 4, 4: 16, 6: 36}
```

-   如果关键字都是简单的字符串，有时通过关键字参数指定 key-value 对更为方便。

```python
>>> dict(sape=4139, guido=4127, jack=4098)
{'sape': 4139, 'jack': 4098, 'guido': 4127}
```

### 循环技巧

-   在字典中循环时，关键字和对应的值可以使用`items()`方法同时解读出来。

```python
>>> knights = {'gallahad': 'the pure', 'robin': 'the brave'}
>>> for k, v in knights.items():
...     print(k, v)
...
gallahad the pure
robin the brave
```

-   在序列中循环时，索引位置和对应值可以使用`enumerate()`函数同时得到。

```python
>>> for i, v in enumerate(['tic', 'tac', 'toe']):
...     print(i, v)
...
0 tic
1 tac
2 toe
```

-   **同时循环两个或更多的序列，可以使用`zip()`整体打包。**

```python
>>> questions = ['name', 'quest', 'favorite color']
>>> answers = ['lancelot', 'the holy grail', 'blue']
>>> for q, a in zip(questions, answers):
...     print('What is your {0}?  It is {1}.'.format(q, a))
...
What is your name?  It is lancelot.
What is your quest?  It is the holy grail.
What is your favorite color?  It is blue.
```

-   需要逆向循环序列的话，先正向定位序列，然后调用 reversed() 函数。

```python
>>> for i in reversed(range(1, 10, 2)):
...     print(i)
...
9
7
5
3
1
```

-   要按排序后的顺序循环序列的话，使用 sorted() 函数，它不改动原序列，而是生成一个新的已排序的序列。

```python
>>> basket = ['apple', 'orange', 'apple', 'pear', 'orange', 'banana']
>>> for f in sorted(set(basket)):
...     print(f)
...
apple
banana
orange
pear
```

-   若要在循环内部修改正在遍历的序列（例如复制某些元素），建议您首先制作副本。在序列上循环不会隐式地创建副本。切片表示法使这尤其方便。

```python
>>> words = ['cat', 'window', 'defenestrate']
>>> for w in words[:]:  # Loop over a slice copy of the entire list.
...     if len(w) > 6:
...         words.insert(0, w)
...
>>> words
['defenestrate', 'cat', 'window', 'defenestrate']
```

### 深入条件控制

逻辑操作符 and 和 or 也称作短路操作符：它们的参数从左向右解析，一旦结果可以确定就停止。例如，如果 A 和 C 为真而 B 为假， A and B and C 不会解析 C。作用于一个普通的非逻辑值时，短路操作符的返回值通常是最后一个变量。

可以把比较或其它逻辑表达式的返回值赋给一个变量，例如:

```python
>>> string1, string2, string3 = '', 'Trondheim', 'Hammer Dance'
>>> non_null = string1 or string2 or string3
>>> non_null
'Trondheim'
>>> test1 = string1 and string2 and string3
>>> test1
null
>>> test2 = string2 and string3
>>> test2
'Hammer Dance'
```

### 比较序列和其它类型

序列对象可以与相同类型的其它对象比较。比较操作按**字典序**进行：首先比较前两个元素，如果不同，就决定了比较的结果；如果相同，就比较后两个元素，依此类推，直到所有序列都完成比较。如果两个元素本身就是同样类型的序列，就递归字典序比较。如果两个序列的所有子项都相等，就认为序列相等。如果一个序列是另一个序列的**初始子序列**，较短的一个序列就小于另一个。字符串的字典序按照单字符的**ASCII顺序**。下面是同类型序列之间比较的一些例子：

```python
(1, 2, 3)              < (1, 2, 4)
[1, 2, 3]              < [1, 2, 4]
'ABC' < 'C' < 'Pascal' < 'Python'
(1, 2, 3, 4)           < (1, 2, 4)
(1, 2)                 < (1, 2, -1)
(1, 2, 3)             == (1.0, 2.0, 3.0)
(1, 2, ('aa', 'ab'))   < (1, 2, ('abc', 'a'), 4)
```

## 模块

### 概览

这就是传说中的**脚本**。随着你的程序变得越来越长，你可能想要将它分割成几个更易于维护的文件。你也可能想在不同的程序中使用顺手的函数，而不是把代码在它们之间中拷来拷去。

模块是包括 Python 定义和声明的文件。文件名就是模块名加上 .py 后缀。模块的模块名（做为一个字符串）可以由全局变量`__name__`得到。

导入模块的语句为`import model_name`，可以通过模块名访问函数，如下：

```python
model_name.function()
```

如果打算频繁使用一个函数，你可以将它赋予一个本地变量。

```python
f = model_name.function
f()
```

### 深入

除了包含函数定义外，模块也可以包含可执行语句。这些语句一般用来初始化模块。他们仅在第一次被导入的地方执行一次。

模块的作者可以在模块内部使用全局变量，而无需担心它与某个用户的全局变量意外冲突。

模块可以导入其他的模块。一个习惯是将所有的`import`语句放在模块的开始（或者是脚本）。被导入的模块名会放入当前模块的全局符号表中。

`import`语句的一个变体直接从被导入的模块中导入命名到本模块的语义表中。例如:

```python
>>> from fibo import fib, fib2
>>> fib(500)
1 1 2 3 5 8 13 21 34 55 89 144 233 377
```

这样不会从局域语义表中导入模块名（如上所示， fibo 没有定义）。

甚至有种方式可以导入模块中的**所有定义**，这样可以导入所有除了以下划线( \_ )开头的命名。需要注意的是在实践中往往不鼓励从一个模块或包中使用`*`导入所有，因为这样会让代码变得很难读。不过，在**交互式会话**中这样用很方便省力。

```python
>>> from fibo import *
>>> fib(500)
1 1 2 3 5 8 13 21 34 55 89 144 233 377
```

## 输出方法

我们有两种大相径庭地输出值方法：表达式语句和`print()`函数。

有两种方法可以格式化你的输出：
1\. 字符串处理法：由你自己处理整个字符串，通过使用字符串切割和连接操作可以创建任何你想要的输出形式。
2\. 使用`str.format()`方法。
3\. 旧式字符串格式化。

### 字符串处理法

Python 有办法将任意值转为字符串：将它传入`repr()`或`str()`函数。

函数`str()`用于将值转化为适于人阅读的形式
`repr()`转化为供解释器读取的形式（如果没有等价的语法，则会发生`SyntaxError`异常）。
某对象没有适于人阅读的解释形式的话，`str()`会返回与`repr()`等同的值。
很多类型，诸如数值或链表、字典这样的结构，针对各函数都有着统一的解读方式。**字符串和浮点数，有着独特的解读方式。**
例如：

```python
>>> s = 'Hello, world.'
>>> str(s)
'Hello, world.'
>>> repr(s)
"'Hello, world.'"
>>> str(1/7)
'0.14285714285714285'
>>> x = 10 * 3.25
>>> y = 200 * 200
>>> s = 'The value of x is ' + repr(x) + ', and y is ' + repr(y) + '...'
>>> print(s)
The value of x is 32.5, and y is 40000...
>>> # The repr() of a string adds string quotes and backslashes:
... hello = 'hello, world\n'
>>> hellos = repr(hello)
>>> print(hellos)
'hello, world\n'
>>> # The argument to repr() may be any Python object:
... repr((x, y, ('spam', 'eggs')))
"(32.5, 40000, ('spam', 'eggs’))"
```

### `str.format()`方法

方法 str.format() 的基本用法如下：

```python
>>> print('We are the {} who say "{}!"'.format('knights', 'Ni'))
We are the knights who say "Ni!"
```

大括号和其中的字符会被替换成传入 str.format() 的参数。大括号中的数值指明使用传入 str.format() 方法的对象中的哪一个：

```python
>>> print('{0} and {1}'.format('spam', 'eggs'))
spam and eggs
>>> print('{1} and {0}'.format('spam', 'eggs'))
eggs and spam
```

如果在 str.format() 调用时使用关键字参数，可以通过参数名来引用值。

```python
>>> print('This {food} is {adjective}.'.format(
...       food='spam', adjective='absolutely horrible'))
This spam is absolutely horrible.
```

位置参数和关键字参数可以随意组合。

```python
>>> print('The story of {0}, {1}, and {other}.'.format('Bill', 'Manfred',other='Georg'))
The story of Bill, Manfred, and Georg.
```

`’!a’`（应用`ascii()`），`’!s’` （应用`str()`）和`’!r’`（应用`repr()`）可以在格式化之前转换值。

```python
>>> import math
>>> print('The value of PI is approximately {}.'.format(math.pi))
The value of PI is approximately 3.14159265359.
>>> print('The value of PI is approximately {!r}.'.format(math.pi))
The value of PI is approximately 3.141592653589793.
```

字段名后允许可选的`‘:’`和格式指令。这允许对值的格式化加以更深入的控制。下例将 Pi 转为三位精度。

```python
>>> import math
>>> print('The value of PI is approximately {0:.3f}.'.format(math.pi))
The value of PI is approximately 3.142.
```

在字段后的`’:’`后面加一个整数会限定该字段的最小宽度，这在美化表格时很有用。

```python
>>> table = {'Sjoerd': 4127, 'Jack': 4098, 'Dcab': 7678}
>>> for name, phone in table.items():
...     print('{0:10} ==> {1:10d}'.format(name, phone))
...
Jack       ==>       4098
Dcab       ==>       7678
Sjoerd     ==>       4127
```

### 旧式字符串格式化

操作符`%`也可以用于字符串格式化。例如：

```python
>>> import math
>>> print('The value of PI is approximately %5.3f.' % math.pi)
The value of PI is approximately 3.142.
```

## 文件读写

函数`open()`返回文件对象，通常的用法需要两个参数：`open(filename, mode)`。

第一个参数是一个含有文件名的字符串。第二个参数也是一个字符串，含有描述如何使用该文件的几个字符。`mode`为`’r’`时表示只是读取文件；`’w’`表示只是写入文件（已经存在的同名文件将被删掉）；`’a’`表示打开文件进行追加，写入到文件中的任何数据将自动添加到末尾。`'r+'`表示打开文件进行读取和写入。`mode`参数是可选的，默认为`’r’`。

## 总结

大体的Python的语法和语句就先学习至此。剩下还有"异常与错误处理"，"Python标准库"，"交互式输入"等。具体问题具体分析。
