#迭代

Python的for循环要比Java中的强大许多

只要是可迭代对象，无论有无下标，都可以迭代，比如dict就可以迭代：
```py
>>> d = {'a': 1, 'b': 2, 'c': 3}
>>> for key in d:
...     print(key)
...
a
c
b
```
因为dict的存储不是按照list的方式顺序排列，所以，迭代出的结果顺序很可能不一样。

默认情况下，dict迭代的是`key`。如果要迭代`value`，可以用
```py
for value in d.values()
```
如果要同时迭代`key`和`value`，可以用
```py
for k, v in d.items()
```

字符串也是可迭代对象:

```py
>>> for ch in 'ABC':
...     print(ch)
...
A
B
C
```

通过collections模块的Iterable类型可以判断当前类型是否可以迭代：
```py
>>> from collections import Iterable
>>> isinstance('abc', Iterable) # str是否可迭代
True
>>> isinstance([1,2,3], Iterable) # list是否可迭代
True
>>> isinstance(123, Iterable) # 整数是否可迭代
False
```


>如果要对list实现类似Java那样的下标循环怎么办？

Python内置的`enumerate`函数可以把一个list变成索引-元素对，这样就可以在for循环中同时迭代索引和元素本身
```py
>>> for i, value in enumerate(['A', 'B', 'C']):
...     print(i, value)
...
0 A
1 B
2 C
```

上面的for循环里，同时引用了两个变量，在Python里是很常见的，比如下面的代码：

```py
>>> for x, y in [(1, 1), (2, 4), (3, 9)]:
...     print(x, y)
...
1 1
2 4
3 9
```


