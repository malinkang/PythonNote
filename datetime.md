```python
#获取一年中第几周
#https://stackoverflow.com/questions/2600775/how-to-get-week-number-in-python
import datetime
print(datetime.date(2022, 1, 2).isocalendar().week) #52
print(datetime.date(2022, 1, 2).isocalendar().year) #2021
```