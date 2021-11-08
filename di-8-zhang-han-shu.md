# 第8章　函数

## 8.1 定义函数

```python
#函数定义
def my_abs(x):
    if x>=0:
        return x
    else:
        return -x;
#函数调用
print(my_abs(-1))
#空函数
def nop():
    pass
```

pass可以用来作为占位符，比如现在还没想好怎么写函数的代码，就可以先放一个pass，让代码能运行起来。

pass还可以用在其他语句里，比如：

```python
if age >= 18:
    pass
```

函数返回多个值

在游戏中经常需要从一个点移动到另一个点，给出坐标、位移和角度，就可以计算出新的新的坐标：

```python
import math

def move(x, y, step, angle=0):
    nx = x + step * math.cos(angle)
    ny = y - step * math.sin(angle)
    return nx, ny
#调用
x, y = move(100, 100, 60, math.pi / 6)
print x, y
151.961524227 70.0
#但其实这只是一种假象，Python函数返回的仍然是单一值
r = move(100, 100, 60, math.pi / 6)
print r
(151.96152422706632, 70.0)
```

原来返回值是一个tuple！但是，在语法上，返回一个tuple可以省略括号，而多个变量可以同时接收一个tuple，按位置赋给对应的值，所以，Python的函数返回多值其实就是返回一个tuple，但写起来更方便。

## 2.函数的参数 <a id="2.&#x51FD;&#x6570;&#x7684;&#x53C2;&#x6570;"></a>

### 2.1.默认参数 <a id="2.1.&#x9ED8;&#x8BA4;&#x53C2;&#x6570;"></a>

```python
def enroll(name,gender,age=6,city='Beijing'):
    print 'name:',name
    print 'gender:',gender
    print 'age:',age
    print 'city:',city

print enroll('malinakng','F',city='Nanyang')
```

默认参数默认值为变量

```python
def add_end(L=[]):
    L.append('END')
    return L

print add_end()
['END']
print add_end()
['END','END']
```

默认值为表达式？

### 2.2.可变参数 <a id="2.2.&#x53EF;&#x53D8;&#x53C2;&#x6570;"></a>

可变参数定义

```python
def calc(*numbers):
    sum = 0
    for n in numbers:
        sum = sum + n * n
    return sum
```

如果已经有一个list或者tuple，要调用一个可变参数怎么办？可以这样做

```python
nums = [1, 2, 3]
calc(nums[0], nums[1], nums[2])
14
```

这种写法当然是可行的，问题是太繁琐，所以Python允许你在list或tuple前面加一个\*号，把list或tuple的元素变成可变参数传进去：

```python
nums = [1, 2, 3]
calc(*nums)
14
```

### 2.3.关键字参数 <a id="2.3.&#x5173;&#x952E;&#x5B57;&#x53C2;&#x6570;"></a>

可变参数允许你传入0个或任意个参数，这些可变参数在函数调用时自动组装为一个tuple。而关键字参数允许你传入0个或任意个含参数名的参数，这些关键字参数在函数内部自动组装为一个dict。

```python
def person(name, age, **kw):
    print 'name:', name, 'age:', age, 'other:', kw
# 调用
>>> person('Adam', 45, gender='M', job='Engineer')
name: Adam age: 45 other: {'gender': 'M', 'job': 'Engineer'}
>>> kw = {'city': 'Beijing', 'job': 'Engineer'}
#和可变参数类似，也可以先组装出一个dict，然后，把该dict转换为关键字参数传进去：
>>> person('Jack', 24, city=kw['city'], job=kw['job'])
name: Jack age: 24 other: {'city': 'Beijing', 'job': 'Engineer'}
#上面复杂的调用可以用简化的写法：
>>> kw = {'city': 'Beijing', 'job': 'Engineer'}
>>> person('Jack', 24, **kw)
name: Jack age: 24 other: {'city': 'Beijing', 'job': 'Engineer'}
```

### 2.4.参数组合 <a id="2.4.&#x53C2;&#x6570;&#x7EC4;&#x5408;"></a>

```python
#定义
def func(a, b, c=0, *args, **kw):
    print 'a =', a, 'b =', b, 'c =', c, 'args =', args, 'kw =', kw
#调用
>>> func(1, 2)
a = 1 b = 2 c = 0 args = () kw = {}
>>> func(1, 2, c=3)
a = 1 b = 2 c = 3 args = () kw = {}
>>> func(1, 2, 3, 'a', 'b')
a = 1 b = 2 c = 3 args = ('a', 'b') kw = {}
>>> func(1, 2, 3, 'a', 'b', x=99)
a = 1 b = 2 c = 3 args = ('a', 'b') kw = {'x': 99}

# 传入tuple和dict
>>> args = (1, 2, 3, 4)
>>> kw = {'x': 99}
>>> func(*args, **kw)
a = 1 b = 2 c = 3 args = (4,) kw = {'x': 99}
```

## 3.高阶函数 <a id="3.&#x9AD8;&#x9636;&#x51FD;&#x6570;"></a>

变量指向函数

函数名其实就是指向函数的变量！对于abs\(\)这个函数，完全可以把函数名abs看成变量，它指向一个可以计算绝对值的函数！

函数本身也可以赋值给变量，即：变量可以指向函数。

```python
>>> f = abs
>>> f(-10)
10
```

传入函数

既然变量可以指向函数，函数的参数能接收变量，那么一个函数就可以接收另一个函数作为参数，这种函数就称之为`高阶函数`。

```python
#定义一个高阶函数
def add(x, y, f):
    return f(x) + f(y）
# 调用函数
>>> add(-5, 6, abs)
11
```

### 3.1.map和reduce函数 <a id="3.1.map&#x548C;reduce&#x51FD;&#x6570;"></a>

map\(\)函数接收两个参数，一个是函数，一个是序列，map将传入的函数依次作用到序列的每个元素，并把结果作为新的list返回。

```python
>>> def f(x) :return x * x
...
#f(x)=x2作用在list上
>>> map (f,[1,2,3,4,5,6,7,8,9])
[1, 4, 9, 16, 25, 36, 49, 64, 81]
>>>
#把list所有数字转换为字符串
>>> map(str, [1, 2, 3, 4, 5, 6, 7, 8, 9])
['1', '2', '3', '4', '5', '6', '7', '8', '9']
```

reduce把一个函数作用在一个序列\[x1, x2, x3...\]上，这个函数必须接收两个参数，reduce把结果继续和序列的下一个元素做累积计算，其效果就是：

```python
reduce(f, [x1, x2, x3, x4]) = f(f(f(x1, x2), x3), x4)
```

例子

```python
#计算总和
>>> def fn(x,y):return x +y
...
>>> reduce(fn ,range(101))
5050
#把序列[1, 3, 5, 7, 9]变换成整数13579
>>> def fn(x,y) :return x*10+y
...
>>> reduce(fn,[1,3,5,7,9])
13579
```

reduce和map综合使用

```python
#将字符串转换为数字

>>> def char2num(s):return {'0': 0, '1': 1, '2': 2, '3': 3, '4': 4, '5': 5, '6': 6, '7': 7, '8': 8, '9': 9}[s]
...
>>> def fn(x, y):return x*10 +y
...
>>> reduce(fn,map(char2num,'13579'))
13579
# 整理成str2int函数
# 在一个函数内部还能定义函数，屌爆了
def str2int(s):
    def fn(x, y):
        return x * 10 + y
    def char2num(s):
        return {'0': 0, '1': 1, '2': 2, '3': 3, '4': 4, '5': 5, '6': 6, '7': 7, '8': 8, '9': 9}[s]
    return reduce(fn, map(char2num, s))
```

### 3.2.fliter函数 <a id="3.2.filter&#x51FD;&#x6570;"></a>

和map\(\)类似，filter\(\)也接收一个函数和一个序列。和map\(\)不同的时，filter\(\)把传入的函数依次作用于每个元素，然后根据返回值是True还是False决定保留还是丢弃该元素。

```python
#在一个list中，删掉偶数，只保留奇数
def is_odd(n):
    return n % 2 == 1

filter(is_odd, [1, 2, 4, 5, 6, 9, 10, 15])
# 结果: [1, 5, 9, 15]

#把一个序列中的空字符串删掉
def not_empty(s):
    return s and s.strip()

filter(not_empty, ['A', '', 'B', None, 'C', '  '])
# 结果: ['A', 'B', 'C']
```

### 3.3.sorted函数 <a id="3.3.sorted&#x51FD;&#x6570;"></a>

```python
>>> sorted([36, 5, 12, 9, 21])
[5, 9, 12, 21, 36]
# 自定义比较函数
def reversed_cmp(x, y):
    if x > y:
        return -1
    if x < y:
        return 1
    return 0
# 传入自定义的比较函数
>>> sorted([36, 5, 12, 9, 21], reversed_cmp)
[36, 21, 12, 9, 5]
#默认情况下，对字符串排序，是按照ASCII的大小比较的，由于'Z' < 'a'，结果，大写字母Z会排在小写字母a的前面。
>>> sorted(['bob', 'about', 'Zoo', 'Credit'])
['Credit', 'Zoo', 'about', 'bob']
# 自定义比较函数，忽略大小写

def cmp_ignore_case(s1, s2):
    u1 = s1.upper()
    u2 = s2.upper()
    if u1 < u2:
        return -1
    if u1 > u2:
        return 1
    return 0
# 调用
>>> sorted(['bob', 'about', 'Zoo', 'Credit'], cmp_ignore_case)
['about', 'bob', 'Credit', 'Zoo']
```

### 3.4.返回函数 <a id="3.4.&#x8FD4;&#x56DE;&#x51FD;&#x6570;"></a>

高阶函数除了可以接受函数作为参数外，还可以把函数作为结果值返回。

```python
def lazy_sum(*args):
    def sum():
        ax = 0
        for n in args:
            ax = ax + n
        return ax
    return sum
#返回函数
f = lazy_sum(1, 3, 5, 7, 9)

print f
#调用函数
print f()
#当我们调用lazy_sum()时，每次调用都会返回一个新的函数，即使传入相同的参数
f1 = lazy_sum(1, 3, 5, 7, 9)
f2 = lazy_sum(1, 3, 5, 7, 9)
# False
print f1==f2
#返回的函数并没有立刻执行，而是直到调用了f()才执行
def count():
    fs = []
    for i in range(1, 4):
        def f():
             return i*i
        fs.append(f)
    return fs



f1,f2,f3=count()

#返回的函数引用了变量i，但它并非立刻执行。等到3个函数都返回时，它们所引用的变量i已经变成了3，因此最终结果为9。
print f1()
#9
#
print f2()
#9
#
print f3()
#9
```

### 3.5.匿名函数 <a id="3.5.&#x533F;&#x540D;&#x51FD;&#x6570;"></a>

当我们在传入函数时，有些时候，不需要显式地定义函数，直接传入匿名函数更方便。

关键字`lambda`表示匿名函数，冒号前面的x表示函数参数。

匿名函数有个限制，就是只能有一个表达式，不用写return，返回值就是该表达式的结果。

```python
# -*- coding: utf-8 -*-
L=map(lambda x: x * x, [1, 2, 3, 4, 5, 6, 7, 8, 9])

print L
#[1, 4, 9, 16, 25, 36, 49, 64, 81]
#把匿名函数赋值给一个变量，再利用变量来调用该函数
f =lambda x:x *x

print f(5)
#25

#匿名函数作为返回值返回
def build(x, y):
    return lambda: x * x + y * y

f1=build(1,2)

print f1()
#5
```

### 3.6.装饰器 <a id="3.6.&#x88C5;&#x9970;&#x5668;"></a>

代码运行期间动态增加功能的方式，称之为“装饰器”（Decorator）

```python
# -*- coding: utf-8 -*-
import functools

def log(text):
    def decorator(func):
#把原始函数的__name__等属性复制到wrapper()函数中
        @functools.wraps(func)
        def wrapper(*args, **kw):
            print '%s %s():' % (text, func.__name__)
            return func(*args, **kw)
        return wrapper
    return decorator
@log('execute')
def add(x,y):
    return x+y

add(1,2)
# add = log('execute')(now)
```

