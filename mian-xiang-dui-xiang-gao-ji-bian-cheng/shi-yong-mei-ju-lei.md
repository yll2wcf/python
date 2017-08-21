#使用枚举类

```py
from enum import Enum

Month = Enum('Month', ('Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'))
```

可以直接使用`Month.Jan`来引用一个常量


如果需要更精确地控制枚举类型，可以从Enum派生出自定义类：
```py
from enum import Enum, unique

@unique
class Weekday(Enum):
    Sun = 0 # Sun的value被设定为0
    Mon = 1
    Tue = 2
    Wed = 3
    Thu = 4
    Fri = 5
    Sat = 6
    
```
`@unique`装饰器可以帮助我们检查保证没有重复值。


