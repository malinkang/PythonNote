# 第2章　变量和简单数据类型

## 2.2 变量

Python是动态语言。

```python
>>> a = 123
>>> print a
123
>>> a = 'ABC'
>>> print a
ABC
```

### 2.2.1 变量的命名和使用

## 2.3 字符串

在Python中，用引号括起来的都是字符串，其中的引号可以是单引号，也可以是双引号。

### 2.3.1 大小写转换

```python
>>> name = "ada lovelace"
>>> print(name.title())
Ada Lovelace
>>> print(name.upper())
ADA LOVELACE
>>> print(name.lower())
ada lovelace
```

### 2.3.2 拼接字符串

```java
>>> first_name = "ada"
>>> last_name = "lovelace"
>>> full_name = first_name + " " + last_name
>>> print("Hello, " + full_name.title() + "! ")
Hello, Ada Lovelace!
```

### 2.3.3 使用制表符或换行符来添加空白

```python
>>> print("Python")
Python
>>> print("\tPython")
    Python
>>> print("Language:\nPython\nC\nJavaScript")
Language:
Python
C
JavaScript
>>> print('I\'m ok.')
I'm ok.
```

### 2.3.4 删除空白

```python
>>> favorite_language = ' python '
>>> favorite_language
' python '
>>> favorite_language.rstrip()
' python'
>>> favorite_language.lstrip()
'python '
>>> favorite_language.strip()
'python'
```

### 2.3.5 使用字符串时避免语法错误

### 2.3.6 Python2中的print语句

在`Python2`中，无需将要打印的内容放在括号内。从技术上说，`Python3`中的`print`是一个函数，因此括号必不可少。有些`Python2`的`print`语句也可包含括号，但其行为与`Python3`中稍有不同。简单地说，在`Python2`代码中，有些print语句包含括号，有些不包含。

```python
>>> print 'hello, world'
hello, world
#print语句也可以跟上多个字符串，用逗号“,”隔开，就可以连成一串输出：
>>> print 'The quick brown fox', 'jumps over', 'the lazy dog'
#print会依次打印每个字符串，遇到逗号“,”会输出一个空格，因此，输出的字符串是这样拼起来的：
The quick brown fox jumps over the lazy dog
>>> print 100 + 200
300
>>> print '100 + 200 =', 100 + 200
100 + 200 = 300
>>>
```

### 2.3.7 占位符

```python
>>> print 'hello,%s'% 'world'
hello,world
#整数和浮点数还可以指定是否补0和整数与小数的位数
>>> '%3d' % 1
'  1'
'%.3f' % 3.1415926
'3.142'
#如果你不太确定应该用什么，%s永远起作用，它会把任何数据类型转换为字符串
>>> 'Age:%s. Gender: %s' % (25,True)
'Age:25. Gender: True'
#对于Unicode字符串，用法完全一样，但最好确保替换的字符串也是Unicode字符串：
>>> u'Hi, %s' % u'malinkang'
u'Hi, malinkang'
#有些时候，字符串里面的%是一个普通字符怎么办？这个时候就需要转义，用%%来表示一个%：
>>> 'growth rate: %d %%' % 7
'growth rate: 7 %'
```

常见占位符

| 占位符 |        |
| --- | ------ |
| %d  | 整数     |
| %f  | 浮点数    |
| %s  | 字符串    |
| %x  | 十六进制整数 |

### 2.3.8 其他方法

```python
# ord()函数将字母转换成数字
>>> ord('A')
65
#chr()函数将数字转换为字母
>>> chr(65)
'A'
# Unicode表示的字符串用u'...'表示
>>> u'中文'
u'\u4e2d\u6587'
# len()函数可以返回字符串长度
>>> len('中文')
6
>>> len(u'中文')
2
# utf-8转unicode
>>> 'abc'.decode('utf-8')
u'abc'
# unicode转utf-8
>>> u'中文'.encode('utf-8')
'\xe4\xb8\xad\xe6\x96\x87'
>>>
```

## 2.4 数字

### 2.4.1 整数

```python
>>> 10
10
>>> -10
-10
#十六进制
>>> 0x10
16
#8进制
>>> 071
57
>>>
#Python使用两个乘号表示乘方运算：
>>> 3**2
9
>>> 3**3
27
>>> 10**6
1000000
```

### 2.4.2 浮点数

```python
>>> 0.0005
0.0005
>>> -0.00005
-5e-05
>>> 0.00005
5e-05
#结果包含的小数位数可能是不确定的
>>> 0.2 + 0.1
0.30000000000000004
>>> 3*0.1
0.30000000000000004
```

### 2.4.3 使用函数str()避免类型

```python
>>> age = 23 
>>> message = "Happy " + age + "rd Birthday!"
#会导致类型错误
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: cannot concatenate 'str' and 'int' objects
```

调用函数`str()`将非字符串值表示为字符串：

```python
>>> age = 23
>>> message = "Happy " + str(age) + "rd Birthday!"
>>> print(message)
Happy 23rd Birthday!
```

### 2.4.4 Python2中的整数

## 2.5 注释

### 2.5.1 如何编写注释

### 2.5.1 该编写什么样的注释

## 2.6 Python之禅



## 参考

* [Does Python have a string 'contains' substring method?](https://stackoverflow.com/questions/3437059/does-python-have-a-string-contains-substring-method)



