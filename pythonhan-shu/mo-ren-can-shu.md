#默认参数

Python定义函数的时候，可以指定参数默认的值，这时候可以不传该参数

例: 我们经常计算x2，所以，完全可以把第二个参数n的默认值设定为2,比Java的重载方法要简单。
```py
def power(x, n=2):
    s = 1
    while n > 0:
        n = n - 1
        s = s * x
    return s
```

当我们调用`power(5)`时，相当于调用`power(5, 2)`

**注意**
    
* 一是必选参数在前，默认参数在后
* 当函数有多个参数时，把变化大的参数放前面，变化小的参数放后面。
* 默认参数要牢记一点：默认参数必须指向不变对象！`L=[]`这种就有可能有问题

下面定义了一个函数 
```py
def enroll(name, gender, age=6, city='Beijing'):
    print('name:', name)
    print('gender:', gender)
    print('age:', age)
    print('city:', city)
```
观察下, 如果age和city分别为空的时候,如何输入
```py
enroll('Bob', 'M', 7)
#可以不按顺序提供部分默认参数。当不按顺序提供部分默认参数时，需要把参数名写上。
enroll('Adam', 'M', city='Tianjin')
```