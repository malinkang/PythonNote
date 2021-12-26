# 第5章　if语句

## 5.3 if语句

### 5.3.1 简单的if语句

```python
age = 20
if age >= 18:
    print 'your age is', age
    print 'adult'
```

```python
if age is not None#判断是否
```

### 5.3.2 if-else语句

```python
age = 3
if age >= 18:
    print 'your age is', age
    print 'adult'
else:
    print 'your age is', age
    print 'teenager'
```

### 5.3.3 if-elif-else语句

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
