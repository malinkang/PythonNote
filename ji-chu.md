# 基础

## 目录

* [1.输入输出](ji-chu.md#1.输入输出)
* [2.数据类型](ji-chu.md#2.数据类型)
* [3.变量](ji-chu.md#3.变量)
* [4.list](ji-chu.md#4.list)
* [5.tuple](ji-chu.md#5.tuple)
* [6.条件判断](ji-chu.md#6.条件判断)
* [7.循环](ji-chu.md#7.循环)
* [8.dict](ji-chu.md#8.dict)
* [9.set](ji-chu.md#9.set)
* [10.切片](ji-chu.md#10.切片)
* [11.迭代](ji-chu.md#11.迭代)
* [12.列表生成式](ji-chu.md#12.列表生成式)
* [13.生成器](ji-chu.md#13.生成器)

## 1.输入输出 <a id="1.&#x8F93;&#x5165;&#x8F93;&#x51FA;"></a>

### 1.1输出

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

### 1.2输入

Python提供了一个`raw_input`，可以让用户输入字符串，并存放到一个变量里。

```python
>>> name = raw_input()
malinkang
>>> print name
malinkang
>>> raw_input('please enter your name')
please enter your namemalinkang
'malinkang'
>>> print 'hello,',name
hello, malinkang
```

## 2.数据类型 <a id="2.&#x6570;&#x636E;&#x7C7B;&#x578B;"></a>

### 2.1整数

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
```

### 2.2浮点数

```python
>>> 0.0005
0.0005
>>> -0.00005
-5e-05
>>> 0.00005
5e-05
>>>
```

### 2.3字符串

```python
#转义字符
>>> print 'I\'m ok.'
I'm ok.
>>> print 'line1\nline2'
line1
line2
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

占位符

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

| 占位符 |  |
| :--- | :--- |
| %d | 整数 |
| %f | 浮点数 |
| %s | 字符串 |
| %x | 十六进制整数 |

### 2.4 布尔值

```python
>>> True
True
>>> False
False
>>> 3 > 2
True
>>> 3 > 5
False
```

布尔值可以用`and`、`or`和`not`运算

```python
>>> True and True
True
>>> True and False
False
>>> False and False
False
>>> True or True
True
>>> True or False
True
>>> False or False
False
>>> not True
False
>>> not False
True
```

### 2.5空值

空值是Python里一个特殊的值，用`None`表示。

## 3.变量 <a id="3.&#x53D8;&#x91CF;"></a>

Python是动态语言。

```python
>>> a = 123
>>> print a
123
>>> a = 'ABC'
>>> print a
ABC
```

## 4.list <a id="4.list"></a>

list是一种有序的集合，可以随时添加和删除其中的元素。

```python
>>> strs = ['ma','lin','kang']
>>> strs
['ma', 'lin', 'kang']
#用len()函数可以获得list元素的个数：
>>> len(strs)
3
#用索引来访问list中每一个位置的元素，记得索引是从0开始的
>>> strs[1]
'lin'
#如果要取最后一个元素，除了计算索引位置外，还可以用-1做索引，直接获取最后一个元素
>>> strs[-1]
'kang'
#以此类推，可以获取倒数第2个、倒数第3个
>>> strs[-3]
'ma'
#list是一个可变的有序表，所以，可以往list中追加元素到末尾
>>> strs.append('hello world')
>>> strs
['ma', 'lin', 'kang', 'hello world']
#要删除list末尾的元素，用pop()方法：
>>> strs.pop()
'hello world'
>>> strs
['ma', 'lin', 'kang']
#要删除指定位置的元素，用pop(i)方法，其中i是索引位置：
>>> strs.pop(1)
'lin'
>>> strs
['ma', 'kang']
#也可以把元素插入到指定的位置，比如索引号为1的位置：
>>> strs.insert(1,'lin')
>>> strs
['ma', 'lin', 'kang']
#要把某个元素替换成别的元素，可以直接赋值给对应的索引位置：
>>> strs[0]='M'
>>> strs
['M', 'lin', 'kang']
#list里面的元素的数据类型也可以不同
>>> str = ['ABC',123,True,None]
>>> len(str)
4
>>> strs = ['python','java',['asp','php'],'scheme']
>>> strs[2][1]
'php'
```

## 5.tuple <a id="5.tuple"></a>

另一种有序列表叫元组：tuple。tuple和list非常类似，但是tuple一旦初始化就不能修改。

因为tuple不可变，所以代码更安全。如果可能，能用tuple代替list就尽量用tuple。

```python
#定义tuple
>>> strs =('ma','lin','kang')
>>> strs
('ma', 'lin', 'kang')
#定义空的tuple
>>> t = ()
>>> t
()
#python只有1个元素的tuple定义时必须加一个逗号,以消除歧义
>>> t = (1,)
>>> t
(1,)

>>> strs = ( 'a','b',['A','B'])
>>> strs[2][0]
'A'
>>> strs[2][0]='X'
>>> strs[]2][1]='Y'
('a', 'b', ['X', 'Y'])
```

## 6.条件判断 <a id="6.&#x6761;&#x4EF6;&#x5224;&#x65AD;"></a>

if语句

```python
age = 20
if age >= 18:
    print 'your age is', age
    print 'adult'
```

if...else

```python
age = 3
if age >= 18:
    print 'your age is', age
    print 'adult'
else:
    print 'your age is', age
    print 'teenager'
```

if...elif... else

```python
age = 3
if age >= 18:
    print 'adult'
elif age >= 6:
    print 'teenager'
else:
    print 'kid'
```

if语句执行有个特点，它是从上往下判断，如果在某个判断上是True，把该判断对应的语句执行后，就忽略掉剩下的elif和else。

```python
if x:
    print 'True'
```

只要x是非零数值、非空字符串、非空list等，就判断为True，否则为False。

## 7.循环 <a id="7.&#x5FAA;&#x73AF;"></a>

for...in 循环

```python
sum = 0
for x in [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]:
    sum = sum + x
print sum
```

while循环

```python
sum = 0
n = 99
while n > 0:
    sum = sum + n
    n = n - 2
print sum
```

## 8.dict <a id="8.dict"></a>

dict和java里的map一样，用来存储键值对的。

```python
>>> strs = {'ma':1,'lin':2,'kang':3}
#获取长度
>>> len(strs)
3
#根据key获取value
>>> strs['ma']
1
#使用in判断key是否存在
>>> 'ma' in strs
True
#通过dict提供的get方法，如果key不存在，可以返回None，或者自己指定的value：
>>> strs.get('kang')
3
>>> strs.get('haha','a')
'a'
>>> strs.pop('lin')
2
>>> strs
{'kang': 3, 'ma': 1}
```

## 9.set <a id="9.set"></a>

set和dict类似，也是一组key的集合，但不存储value。

```python
>>> s = set([1,1,2,2,3,3])
>>> s
set([1, 2, 3])
>>> s.add(4)
>>> s
set([1, 2, 3, 4])
>>> s.remove(1)
>>> s
set([2, 3, 4])
#做交集和并集计算
>>> s2 = set([1,2,3])
>>> s & s2
set([2, 3])
>>> s | s2
set([1, 2, 3, 4])
```

## 10.切片 <a id="10.&#x5207;&#x7247;"></a>

Python提供了切片（Slice）操作符，可以从列表中取指定索引范围的操作。

```python
>>> L = range(100)
>>> L
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99]
# 取0到3
>>> L[0:3]
[0, 1, 2]
# 0可以省略
>>> L[:3]
[0, 1, 2]
# 倒数切片
>>> L[-2:]
[98, 99]
#前10个数，每两个取一个
>>> L[:10:2]
[0, 2, 4, 6, 8]
#所有数，每5个取一个
>>> L[::5]
[0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60, 65, 70, 75, 80, 85, 90, 95]
#甚至什么都不写，只写[:]就可以原样复制一个list
>>> L[:]
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30, 31, 32, 33, 34, 35, 36, 37, 38, 39, 40, 41, 42, 43, 44, 45, 46, 47, 48, 49, 50, 51, 52, 53, 54, 55, 56, 57, 58, 59, 60, 61, 62, 63, 64, 65, 66, 67, 68, 69, 70, 71, 72, 73, 74, 75, 76, 77, 78, 79, 80, 81, 82, 83, 84, 85, 86, 87, 88, 89, 90, 91, 92, 93, 94, 95, 96, 97, 98, 99]
# 元组
>>> T = (0,1,2,3)
>>> T[:3]
(0, 1, 2)
# 字符串
>>> S = 'ABCDEDG'
>>> S[:4:2]
'AC'
>>>
```

## 11.迭代 <a id="11.&#x8FED;&#x4EE3;"></a>

dict迭代

```text
#默认迭代key
>>> d = {'a':1,'b':2,'c':3}
>>> for key in d : print key
...
a
c
b
#迭代value
>>> for value  in d.itervalues(): print value
...
1
3
2
# 同时迭代key和value
>>> for k , v in d.iteritems(): print k,v
...
a 1
c 3
b 2
```

字符串遍历

```python
>>> for ch in 'ABC': print ch
...
A
B
C
```

通过collections模块的Iterable类型判断一个对象是否是可迭代对象

```python
>>> from collections import Iterable
>>> isinstance('abc', Iterable) # str是否可迭代
True
>>> isinstance([1,2,3], Iterable) # list是否可迭代
True
>>> isinstance(123, Iterable) # 整数是否可迭代
False
```

Python内置的enumerate函数可以把一个list变成索引-元素对，这样就可以在for循环中同时迭代索引和元素本身：

```python
>>> for i, value in enumerate(['A', 'B', 'C']): print i,value
...
0 A
1 B
2 C
```

上面的for循环里，同时引用了两个变量，在Python里是很常见的，比如下面的代码：

```python
>>> for x, y in [(1, 1), (2, 4), (3, 9)]:
...     print x, y
...
1 1
2 4
3 9
```

## 12.列表生成式 <a id="12.&#x5217;&#x8868;&#x751F;&#x6210;&#x5F0F;"></a>

列表生成式即List Comprehensions，是Python内置的非常简单却强大的可以用来创建list的生成式。

```python
>>> [x * x for x in range(1, 11)]
[1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
>>> [x * x for x in range(1, 11) if x % 2 == 0]
[4, 16, 36, 64, 100]
>>> [m + n for m in 'ABC' for n in 'XYZ']
['AX', 'AY', 'AZ', 'BX', 'BY', 'BZ', 'CX', 'CY', 'CZ']
>>> d = {'x': 'A', 'y': 'B', 'z': 'C' }
>>> [k + '=' + v for k, v in d.iteritems()]
['y=B', 'x=A', 'z=C']
```

## 13.生成器 <a id="13.&#x751F;&#x6210;&#x5668;"></a>

通过列表生成式，我们可以直接创建一个列表。但是，受到内存限制，列表容量肯定是有限的。而且，创建一个包含100万个元素的列表，不仅占用很大的存储空间，如果我们仅仅需要访问前面几个元素，那后面绝大多数元素占用的空间都白白浪费了。

所以，如果列表元素可以按照某种算法推算出来，那我们是否可以在循环的过程中不断推算出后续的元素呢？这样就不必创建完整的list，从而节省大量的空间。在Python中，这种一边循环一边计算的机制，称为生成器（Generator）。

创建生成器的第一种方法

```text
>>> g = (x*x for x in range(10))
>>> for n in g :print n
...
0
1
4
9
16
25
36
49
64
81
```

创建生成器的第二种方法，使用`yield`关键字

```python
def fib(max):
    n, a, b = 0, 0, 1
    while n < max:
        yield b
        a, b = b, a + b
        n = n + 1
```

变成generator的函数，在每次调用next\(\)的时候执行，遇到yield语句返回，再次执行时从上次返回的yield语句处继续执行。

