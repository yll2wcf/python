#装饰器

函数也是一个对象，而且函数对象可以被赋值给变量，所以，通过变量也能调用该函数。

```py
>>> def now():
...     print('2015-3-25')
...
>>> f = now
>>> f()
2015-3-25
```

函数对象有一个`__name__`属性，可以拿到函数的名字：

```py
>>> now.__name__
'now'
>>> f.__name__
'now'
```

假设我们要增强`now()`函数的功能，比如，在函数调用前后自动打印日志，但又不希望修改now()函数的定义，这种在代码运行期间动态增加功能的方式，称之为“装饰器”（Decorator）。


`Decorator`就是一个返回函数的高阶函数。可以定义如下：

```py
def log(func):
    def wrapper(*args, **kw):
        print('call %s():' % func.__name__)
        return func(*args, **kw)
    return wrapper
```
观察上面的`log`，因为它是一个`decorator`，所以接受一个函数作为参数，并返回一个函数。我们要借助Python的`@`语法，把`decorator`置于函数的定义处：
```py
@log
def now():
    print('2015-3-25')
```
调用`now()`函数，不仅会运行`now()`函数本身，还会在运行`now()`函数前打印一行日志：
```py
>>> now()
call now():
2015-3-25
```
把`@log`放到`now()`函数的定义处，相当于执行了语句：
```py
now = log(now)
```

如果decorator本身需要传入参数，那就需要编写一个返回decorator的高阶函数，写出来会更复杂。比如，要自定义log的文本：
```py
def log(text):
    def decorator(func):
        def wrapper(*args, **kw):
            print('%s %s():' % (text, func.__name__))
            return func(*args, **kw)
        return wrapper
    return decorator
```

这个3层嵌套的decorator用法如下：
```py
@log('execute')
def now():
    print('2015-3-25')
```
相当于
```py
 now = log('execute')(now)
```