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