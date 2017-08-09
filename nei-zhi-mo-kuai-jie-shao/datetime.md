#datetime

`datetime`是Python处理日期和时间的标准库。

`datetime`是模块，`datetime`模块还包含一个`datetime`类，通过`from datetime import datetime`导入的才是`datetime`这个类。

如果仅导入`import datetime`，则必须引用全名`datetime.datetime`。

获取当前日期和时间：

```
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
Python的timestamp是一个浮点数。如果有小数位，小数位表示毫秒数。Java／JS 中的结果是毫秒数