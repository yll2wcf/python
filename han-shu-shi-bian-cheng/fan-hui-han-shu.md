#返回函数

函数可以把函数作为返回值返回，如果不需要立刻求和，而是在后面的代码中，以不返回求和的结果，而是返回求和的函数：

```py
def lazy_sum(*args):
    def sum():
        ax = 0
        for n in args:
            ax = ax + n
        return ax
    return sum
```

调用lazy_sum()时，返回的并不是求和结果，而是求和函数：
```py
>>> f = lazy_sum(1, 3, 5, 7, 9)
>>> f
<function lazy_sum.<locals>.sum at 0x101c6ed90>
```