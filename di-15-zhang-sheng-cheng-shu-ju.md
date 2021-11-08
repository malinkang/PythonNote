# 第15章 生成数据

## 15.1 安装matplotlib

```text
pip install --user matplotlib
```

输入如下命令没有任何错误信息说明安装成功

```text
>>> import matplotlib
```

### 15.1.5 matplotlib画廊

{% embed url="https://matplotlib.org/" %}

## 15.2 绘制简单的折线图

```python
import matplotlib.pyplot as pyplot
square = [1,4,9,16,25]
pyplot.plot(squares)
pyplot.show()
```

![](../.gitbook/assets/image%20%288%29.png)

### 15.2.1 修改标签文字和线条粗细

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
import matplotlib.pyplot as pyplot
squares = [1,4,9,16,25]
pyplot.plot(squares,linewidth=5)
# 设置图表标题，并给坐标轴加上标签
pyplot.title("Square Numbers",fontsize=24)
pyplot.xlabel("Value",fontsize=14)
pyplot.ylabel("Square of Value",fontsize=14)
#设置刻度标记的大小
pyplot.tick_params(axis="both",labelsize=14)
pyplot.show()
```

![](../.gitbook/assets/image%20%282%29.png)

### 15.2.2 校正图形

```text
#!/usr/bin/env python
# -*- coding: utf-8 -*-
import matplotlib.pyplot as pyplot
input_values = [1,2,3,4,5]
squares = [1,4,9,16,25]
pyplot.plot(input_values,squares,linewidth=5)
pyplot.show()
```

![](../.gitbook/assets/image%20%285%29.png)

### 15.2.3 使用scatter\(\)绘制散点图

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
import matplotlib.pyplot as pyplot
pyplot.scatter(2,4)
pyplot.show()
```

![](../.gitbook/assets/image%20%287%29.png)

### 15.2.4 使用scatter\(\)绘制一系列点

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
import matplotlib.pyplot as pyplot
x_values = [1,2,3,4,5]
y_values = [1,4,9,16,25]
pyplot.scatter(x_values,y_values,s=100)
pyplot.show()
```

![](../.gitbook/assets/image.png)

### 15.2.5 自动计算数据

```python
#!/usr/bin/env python
# -*- coding: utf-8 -*-
import matplotlib.pyplot as pyplot
x_values = list(range(1,20))
y_values = [x**2 for x in x_values]
pyplot.scatter(x_values,y_values,s=100)
pyplot.show()
```

![](../.gitbook/assets/image%20%284%29.png)

### 15.2.6 删除数据点的轮廓

### 15.2.7 自定义颜色

```python
pyplot.scatter(x_values,y_values,c='red',s=100)
```

![](../.gitbook/assets/image%20%281%29.png)

### 15.2.8 使用颜色映射

```python
pyplot.scatter(x_values,y_values,c=y_values,cmap=pyplot.cm.Blues,s=100)
```

![](../.gitbook/assets/image%20%289%29.png)

### 15.2.9 自动保存图表

```python
# pyplot.show()
pyplot.savefig('squares_plot.png',bbox_inches='tight')
```

## 15.3 随机漫步

### 15.3.1 创建RandomWalk\(\)类



