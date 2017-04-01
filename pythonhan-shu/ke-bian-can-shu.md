#可变参数
在Python函数中，还可以定义可变参数。

定义可变参数和定义一个`list`或`tuple`参数相比，仅仅在参数前面加了一个*号。参数numbers接收到的是一个tuple
```py
def calc(*numbers):
    sum = 0
    for n in numbers:
        sum = sum + n * n
    return sum
```


```py
>>> calc(1, 2)
5
>>> calc()
0
```


>如果已经有一个list或者tuple，要调用一个可变参数怎么办？

```py
>>> nums = [1, 2, 3]
>>> calc(nums[0], nums[1], nums[2])
14
```

这种写法当然是可行的，问题是太繁琐，所以Python允许你在`list`或`tuple`前面加一个`*`号，把`list`或`tuple`的元素变成可变参数传进去：

```py
>>> nums = [1, 2, 3]
>>> calc(*nums)
14
```
`*nums`表示把`nums`这个`list`的所有元素作为可变参数传进去。这种写法相当有用，而且很常见。
