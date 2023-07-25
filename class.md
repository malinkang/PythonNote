---
tags: 
    - Python
comments: true
---
# 类

## 1.创建类

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-

#实例的变量名如果以__开头，就变成了一个私有变量（private），只有内部可以访问，外部不能访问
class Student(object):
# 构造函数
    def __init__(self,name,score):
        self.__name=name
        self.__score=score
    def get_name(self):
        return self.__name
    def set_name(self,name):
        self.__name=name
    def get_score(self):
        return self.__score
    def set_score(self,score):
        self.__score=score
stu = Student("malinkang",100)

print "name is %s , score is %d" %(stu.get_name(),stu.get_score())
```

当我们定义了一个class，创建了一个class的实例后，我们可以给该实例绑定任何属性和方法

```python
#给实例绑定属性
stu.age = 30

print "age is %d" % stu.age

#给shi例绑定方法

def set_age(self,age):
    self.age=age

from types import MethodType

stu.set_age = MethodType(set_age,stu,Student)

stu.set_age(40)

print "age is %d" % stu.age
#给一个实例绑定的方法，对另一个实例是不起作用的

#stu2=Student("hello",80)

#stu2.set_age(18)
#print "age is %d" % stu2.age
# 报错： 'Student' object has no attribute 'set_age'

#为了给所有实例都绑定方法，可以给class绑定方法：

Student.set_age = MethodType(set_age, None, Student)

stu2=Student("hello",80)

stu2.set_age(18)

print "age is %d" % stu2.age
```

Python允许在定义class的时候，定义一个特殊的`__slots__`变量，来限制该class能添加的属性。

`__slots__`定义的属性仅对当前类起作用，对继承的子类是不起作用的。

```python
#用tuple定义允许绑定的属性名称
class Person(object):
    __slots__=("name","age")

p=Person()

p.name="张三"

print "name is %s" % p.name

p.gender="男"

print "gender is %s" % p.gender
#     p.gender="男" AttributeError: 'Person' object has no attribute 'gender'
```

Python内置的`@property`装饰器负责把一个方法变成属性调用

```python
class Book(object):

    @property
    def price(self):
        return self.__price

    @price.setter
    def price(self,price):
        self.__price=price

book = Book()

book.price = 15.5

print "price is %f" % book.price
```

## 2.继承  <a id="2.&#x7EE7;&#x627F;"></a>

```python
#继承

class Animal(object):
    def run(self):
        print "Animal is Running"

class Dog(Animal):
     pass

class Cat(Animal):
     pass

def executeRun(animal):
    animal.run()

executeRun(Dog())


#判断一个变量是否是某个类型可以用isinstance()判断：

print isinstance(Dog(),Animal)

# True
```

