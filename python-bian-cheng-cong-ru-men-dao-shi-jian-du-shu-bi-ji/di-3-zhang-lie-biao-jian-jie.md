# 第3章　列表简介

## 3.1 列表是什么

### 3.1.1 访问列表元素

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

## 3.2 修改、添加和删除元素

### 3.2.1 修改列表元素

```python
>>> strs = ['ma','lin','kang']
#要把某个元素替换成别的元素，可以直接赋值给对应的索引位置：
>>> strs[0]='M'
>>> strs
['M', 'lin', 'kang']
```

## 3.3 组织列表

### 3.3.1 使用方法sort()对列表进行永久排序

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

### 3.3.2 使用函数sorted()对列表进行临时排序

```python
>>> cars = ['bmw','audi','toyota','subaru']
>>> print(cars)
['bmw', 'audi', 'toyota', 'subaru']
>>> print(sorted(cars))
['audi', 'bmw', 'subaru', 'toyota']
>>> print(cars)
['bmw', 'audi', 'toyota', 'subaru']
```

### 3.3.3 倒着打印列表

```python
>>> cars = ['bmw','audi','toyota','subaru']
>>> print(cars)
['bmw', 'audi', 'toyota', 'subaru']
>>> cars.reverse()
>>> print(cars)
['subaru', 'toyota', 'audi', 'bmw']
```
### 3.3.4 确定列表的长度

```python
>>> cars = ['bmw','audi','toyota','subaru']
>>> len(cars)
4
```