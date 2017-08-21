#定制类

class  中有些特殊字段和方法

`__str__()` 等同Java中 `toString()`

`__repr__()` 是开发者调试服务的


如果一个类想被用于`for ... in`循环，类似`list`或`tuple`那样，就必须实现一个`__iter__()`方法，该方法返回一个迭代对象，然后，Python的`for`循环就会不断调用该迭代对象的`__next__()`方法拿到循环的下一个值，直到遇到`StopIteration`错误时退出循环。


要表现得像list那样按照下标取出元素，需要实现`__getitem__()`方法.


`__getattr__()`方法，动态返回一个属性

```py
class Student(object):

    def __getattr__(self, attr):
        if attr=='age':
            return lambda: 25
        raise AttributeError('\'Student\' object has no attribute \'%s\'' % attr)
```


只需要定义一个`__call__()`方法，就可以直接对实例进行调用。请看示例：
```py
class Student(object):
    def __init__(self, name):
        self.name = name

    def __call__(self):
        print('My name is %s.' % self.name)
```
调用如下：
```py
>>> s = Student('Michael')
>>> s() # self参数不要传入
My name is Michael.
```