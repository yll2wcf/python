#datetime

`datetime`是Python处理日期和时间的标准库。

`datetime`是模块，`datetime`模块还包含一个`datetime`类，通过`from datetime import datetime`导入的才是`datetime`这个类。

如果仅导入`import datetime`，则必须引用全名`datetime.datetime`。

获取当前日期和时间：

```py
>>> from datetime import datetime
>>> now = datetime.now() # 获取当前datetime
>>> print(now)
2015-05-18 16:28:07.198690
>>> print(type(now))
<class 'datetime.datetime'>
```


指定某个日期和时间
```py
dt = datetime(2015, 4, 19, 12, 20) # 用指定日期时间创建datetime
```
转换时间戳
```py
dt.timestamp() # 把datetime转换为timestamp 
```
结果  1429417200.0
Python的`timestamp`是一个浮点数。如果有小数位，小数位表示毫秒数。Java／JS 中的结果是毫秒数


###timestamp转换为datetime

使用`datetime`提供的`fromtimestamp()`方法：

```py
>>> from datetime import datetime
>>> t = 1429417200.0
>>> print(datetime.fromtimestamp(t))
2015-04-19 12:20:00
```

###str和datetime转换

转换方法是通过`datetime.strptime()`实现,需要一个日期和时间的格式化字符串

```py
>>> from datetime import datetime
>>> cday = datetime.strptime('2015-6-1 18:19:59', '%Y-%m-%d %H:%M:%S')
>>> print(cday)
2015-06-01 18:19:59
```
日期格式详见文档 [文档](https://docs.python.org/3/library/datetime.html#strftime-strptime-behavior)

datetime 转换字符串通过`strftime()`

```py
>>> from datetime import datetime
>>> now = datetime.now()
>>> print(now.strftime('%a, %b %d %H:%M'))
Mon, May 05 16:28
```

###datetime加减
对日期和时间进行加减实际上就是把datetime往后或往前计算，得到新的`datetime`。加减可以直接用`+`和`-`运算符，不过需要导入`timedelta`这个类：

```py
>>> from datetime import datetime, timedelta
>>> now = datetime.now()
>>> now
datetime.datetime(2015, 5, 18, 16, 57, 3, 540997)
>>> now + timedelta(hours=10)
datetime.datetime(2015, 5, 19, 2, 57, 3, 540997)
>>> now - timedelta(days=1)
datetime.datetime(2015, 5, 17, 16, 57, 3, 540997)
>>> now + timedelta(days=2, hours=12)
datetime.datetime(2015, 5, 21, 4, 57, 3, 540997)
```