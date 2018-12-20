# 第4章　操作列表

## 4.1 遍历整个列表

```python
>>> magicians = ['alice','david','carolina']
>>> for magician in magicians:
...     print(magician)
...
alice
david
carolina
```

## 4.3 创建数值列表

### 4.3.1 使用函数range()

```python
>>> for value in range(1,5):
...     print(value)
...
1
2
3
4
```
### 4.3.2 使用range()创建数字列表

```python
#使用list()方法
>>> numbers = list(range(1,6))
>>> print(numbers)
[1, 2, 3, 4, 5]

>>> even_numbers = list(range(2,11,2))
>>> print(even_numbers)
[2, 4, 6, 8, 10]
```

### 4.3.3 对数字列表执行简单的统计计算

```python
>>> digits = list(range(10))
>>> print(digits)
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> min(digits)
0
>>> max(digits)
9
>>> sum(digits)
45
```
### 4.3.4 列表解析

```python
>>> squares = [value**2 for value in range(1,10)]
>>> print(squares)
[1, 4, 9, 16, 25, 36, 49, 64, 81]
```

## 4.4 使用列表的一部分

### 4.4.1 切片

```python
>> L = range(0,10)
>>> L
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
#取0到3
>>> L[0:3]
[0, 1, 2]
# 0可以省略
>>> L[:3]
[0, 1, 2]
>>> L[1:]
[1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> L[:]
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
#倒数切片
>>> L[-2:]
[8, 9]
#隔两个取一个
>>> L[1::2]
[1, 3, 5, 7, 9]
```