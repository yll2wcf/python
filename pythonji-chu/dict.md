#dict

Python内置了字典：`dict`的支持，`dict`全称`dictionary`，Java语言中对应为map，使用键-值（key-value）存储，具有极快的查找速度。

例子:
```py
>>> d = {'小明': 95, '小于': 75, '小红': 85}
>>> d['小明']
95
```
如果key不存在就会报错
要避免key不存在的错误，有两种办法，一是通过in判断key是否存在：
```py
>>> '老王' in d
False
```

二是通过dict提供的get方法，如果key不存在，可以返回None，或者自己指定的value：
```py
>>> d.get('老王')
>>> d.get('老王', -1)
-1
```
**注意：返回None的时候Python的交互式命令行不显示结果。**

要删除一个key，用`pop(key)`方法，对应的value也会从dict中删除：
```py
>>> d.pop('小于')
75
>>> d
{'小明': 95, '小红': 85}
```

**正确使用dict非常重要，需要牢记的第一条就是dict的key必须是不可变对象。**


