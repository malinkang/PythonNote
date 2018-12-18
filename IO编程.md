## IO编程


### 目录
* [1.文件读写](#1.文件读写)
* [2.操作文件和目录](#2.操作文件和目录)



-------------------------------------------

<h3 id="1.文件读写">1.文件读写</h3>

```Python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
#打开文件
try:
    f = open("/Users/malinkang/Documents/Git/PythonNote/oop.md",'r')
    print f.read()
finally:
    if f:
        f.close()
#Python引入了with语句来自动帮我们调用close()方法
with open("/Users/malinkang/Documents/Git/PythonNote/oop.md", 'r') as f:
    print f.read()
#每次读取一行
with open("/Users/malinkang/Documents/Git/PythonNote/SUMMARY.md", 'r') as f:
    for line in f.readlines():
        print(line.strip())# 把末尾的'\n'删掉

# 写入文件

with open("/Users/malinkang/Documents/Git/PythonNote/SUMMARY.md", 'w') as f:
    print f.write('Hello,world')

```

<h3 id="2.操作文件和目录">2.操作文件和目录</h3>

```Python

#!/usr/bin/env python
# -*- coding: utf-8 -*-
__author__ = 'malinkang'

import os
#操作系统名字
print os.name
#获取详细的系统信息
print os.uname()
#环境变量
print os.environ
#获取某一个环境变量
print os.getenv("LOGNAME")
#获取当前的绝对路径
print os.path.abspath('.')
#判断是否是文件
print os.path.isfile("genymotion-log.zip")
#创建一个目录
os.mkdir("/Users/malinkang/Documents/Git/PythonNote/testdir")
#删除一个目录
os.rmdir("/Users/malinkang/Documents/Git/PythonNote/testdir")

#文件重命名
os.rename('test.txt', 'test.py')
#删除文件
os.remove('test.py')

#获取文件后缀
print os.path.splitext("abc.txt")
#输出('abc', '.txt')

#合并、拆分路径的函数并不要求目录和文件要真实存在

#拼接一个路径
#把两个路径合成一个时，不要直接拼字符串，而要通过os.path.join()函数，这样可以正确处理不同操作系统的路径分隔符
print os.path.join("/Users/malinkang/Documents/Git/PythonNote","abc.txt")
#拆分路径
print os.path.split("/Users/malinkang/Documents/Git/PythonNote/abc.txt")
#列出当前目录所有文件
print os.listdir(".")
#列出当前目录所有.zip的文件
[x for x in os.listdir('.') if os.path.isfile(x) and os.path.splitext(x)[1]==".zip"]
#输出['genymotion-log.zip']

```
