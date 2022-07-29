# 列表

## 创建列表

常用的列表创建方式有两种：字面量语法与`list()`内置函数。

内置函数list(iterable)则可以把任何一个可迭代对象转换为列表，比如字符串：

```python
>>> list('foo')
['f', 'o', 'o']
```

## 访问列表元素

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
```

## 遍历列表

假如你想在遍历的同时，获取当前循环下标，可以选择用内置函数enumerate()包裹列表对象

```python
l = list('foo')
for index, item in enumerate(l):
    print(index, item)
```
enumerate()接收一个可选的start参数，用于指定循环下标的初始值（默认为0）：

```python
l = list('foo')
for index, item in enumerate(l,10):
    print(index, item)
# 10 f
# 11 o
# 12 o
```

## 列表推导式

```python
l = list(range(0,10))
results = [x*x for x in l if x > 4]
print(results)
#[25, 36, 49, 64, 81]
```

## 修改列表元素

```python
>>> strs = ['ma','lin','kang']
#要把某个元素替换成别的元素，可以直接赋值给对应的索引位置：
>>> strs[0]='M'
>>> strs
['M', 'lin', 'kang']
```

## 在列表中添加元素

#### 1.在列表末尾添加元素

```python
>>> strs = ['ma','lin','kang']
>>> strs.append('hello world')
>>> strs
['ma', 'lin', 'kang', 'hello world']
```

#### 2.在列表中插入元素

```python
>>> strs = ['ma','kang']
>>> strs.insert(1,'lin')
>>> strs
['ma', 'lin', 'kang']
```

## 从列表中删除元素

### 1.使用del语句删除元素

```python
>>> strs = ['ma','lin','kang']
>>> del strs[1]
>>> strs
['ma', 'kang']
```

### 2.使用方法pop\(\)删除元素

```python
>>> strs = ['ma','lin','kang']
>>> strs.pop(1)
'lin'
>>> strs
['ma', 'kang']
>>>
```

### 3.根据值删除元素

```python
>>> strs = ['ma','lin','kang']
>>> strs.remove('lin')
>>> strs
['ma', 'kang']
#方法remove()只删除第一个指定的值
>>> strs = ['ma','lin','kang','ma']
>>> strs.remove('ma')
>>> strs
['lin', 'kang', 'ma']
```


## 使用方法sort\(\)对列表进行永久排序

```python
>>> cars = ['bmw','audi','toyota','subaru']
>>> cars.sort()
>>> print(cars)
['audi', 'bmw', 'subaru', 'toyota']
#反向排序
>>> cars.sort(reverse=True)
>>> print(cars)
['toyota', 'subaru', 'bmw', 'audi']
```

## 使用函数sorted\(\)对列表进行临时排序

```python
>>> cars = ['bmw','audi','toyota','subaru']
>>> print(cars)
['bmw', 'audi', 'toyota', 'subaru']
>>> print(sorted(cars))
['audi', 'bmw', 'subaru', 'toyota']
>>> print(cars)
['bmw', 'audi', 'toyota', 'subaru']
```

### 翻转列表

```python
>>> cars = ['bmw','audi','toyota','subaru']
>>> print(cars)
['bmw', 'audi', 'toyota', 'subaru']
>>> cars.reverse()
>>> print(cars)
['subaru', 'toyota', 'audi', 'bmw']
```

