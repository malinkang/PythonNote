# 第6章　字典

## 6.1 一个简单的字典

```python
>>> strs = {'ma':1,'lin':2,'kang':3}
```

## 6.2 使用字典

### 6.2.1 访问字典中的值

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
```

### 6.2.2 添加键值对

### 6.2.5 删除键值对

```python
>>> strs = {'ma':1,'lin':2,'kang':3}
>>> del strs['ma']
>>> strs
{'kang': 3, 'lin': 2}
```

## 6.3 遍历字典

### 6.3.1 遍历所有的键值对

```python
>>> user = {'username':'efermi','first':'enrico','last':'fermi'}
>>> for key,value in user.items():
...     print("\nKey: " + key)
...     print("Value: " + value)
...

Key: username
Value: efermi

Key: last
Value: fermi

Key: first
Value: enrico
```

### 6.3.2 遍历字典中的所有键

```python
>>> for key in user.keys():
...     print(key)
...
username
last
first
```

### 6.3.4 遍历字典中的所有值

```python
>>> for value in user.values():
...     print(value)
...
efermi
fermi
enrico
```

