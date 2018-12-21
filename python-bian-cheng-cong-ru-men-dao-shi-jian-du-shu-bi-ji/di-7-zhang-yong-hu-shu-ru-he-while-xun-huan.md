# 第7章　用户输入和while循环



# 7.1 函数input()的工作原理

## 7.1.4 在Python2.7中获取输入

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

## 7.2 while循环简介

### 7.2.1 使用while循环

```python
sum = 0
n = 99
while n > 0:
    sum = sum + n
    n = n - 2
print sum
```

### 7.2.4 使用break退出循环

### 7.2.5 在循环中使用continue


### 7.2.6 避免无限循环