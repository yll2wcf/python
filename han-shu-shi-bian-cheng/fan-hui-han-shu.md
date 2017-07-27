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
调用函数f时，才真正计算求和的结果：
```py
>>> f()
25
```
上面这种形式称为闭包。

调用`lazy_sum()`时，每次调用都会返回一个新的函数，即使传入相同的参数：

```py
>>> f1 = lazy_sum(1, 3, 5, 7, 9)
>>> f2 = lazy_sum(1, 3, 5, 7, 9)
>>> f1==f2
False
```
`f1()`和`f2()`的调用结果互不影响。
