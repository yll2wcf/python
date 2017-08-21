# 使用`__slots__`

Python允许在定义class的时候，定义一个特殊的`__slots__`变量，来限制该class实例能添加的属性

```py
class Student(object):
    __slots__ = ('name', 'age') # 用tuple定义允许绑定的属性名称
```

