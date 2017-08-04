#偏函数

当函数的参数个数太多，需要简化时，使用`functools.partial`可以创建一个新的函数，这个新函数可以固定住原函数的部分参数，从而在调用时更简单。

例如
`int()`函数可以把字符串转换为整数，当仅传入字符串时，`int()`函数默认按十进制转换，如果传入base参数，就可以做N进制的转换：
```py
>>> int('12345', base=8)
5349
>>> int('12345', 16)
74565

```

要转换大量的二进制字符串，每次都传入`int(x, base=2)`非常麻烦
简化代码
```py
>>> import functools
>>> int2 = functools.partial(int, base=2)
>>> int2('1000000')
64
>>> int2('1010101')
85
```

创建偏函数时，实际上可以接收函数对象、`*args`和`**kw`这3个参数
```py
int2 = functools.partial(int, base=2)
int2('10010')
```
相当于
```py
kw = { 'base': 2 }
int('10010', **kw)
```

当传入：
```py
max2 = functools.partial(max, 10)
```
实际上会把10作为*args的一部分自动加到左边，也就是：
```py
max2(5, 6, 7)
```
相当于：
```py
args = (10, 5, 6, 7)
max(*args)
```