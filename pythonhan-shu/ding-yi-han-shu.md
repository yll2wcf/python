#定义函数
在Python中，定义一个函数要使用`def`语句，依次写出函数名、括号、括号中的参数和冒号`:`，然后，在缩进块中编写函数体，函数的返回值用return语句返回。
```py
def my_abs(x):
    if x >= 0:
        return x
    else:
        return -x
```

##空函数
如果想定义一个什么事也不做的空函数，可以用`pass`语句：
```py
def nop():
    pass
```

>`pass`语句什么都不做，那有什么用？

实际上`pass`可以用来作为占位符，比如现在还没想好怎么写函数的代码，就可以先放一个`pass`，让代码能运行起来。

`pass`还可以用在其他语句里，比如：
```py
if age >= 18:
    pass
```
缺少了`pass`，代码运行就会有语法错误。

##定义错误处理
当传入了不恰当的参数时，内置函数`abs`会检查出参数错误，而我们定义的`my_abs`没有参数检查，会导致`if`语句出错，出错信息和`abs`不一样。
如:
```py
>>> my_abs('A')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "<stdin>", line 2, in my_abs
TypeError: unorderable types: str() >= int()
>>> abs('A')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: bad operand type for abs(): 'str'
```

修改一下`my_abs`的定义，对参数类型做检查，只允许整数和浮点数类型的参数。数据类型检查可以用内置函数`isinstance()`实现：
```py
def my_abs(x):
    if not isinstance(x, (int, float)):
        raise TypeError('bad operand type')
    if x >= 0:
        return x
    else:
        return -x
```

##返回多个值
比如在游戏中经常需要从一个点移动到另一个点，给出坐标、位移和角度，就可以计算出新的新的坐标：
```py
import math

def move(x, y, step, angle=0):
    nx = x + step * math.cos(angle)
    ny = y - step * math.sin(angle)
    return nx, ny

x, y = move(100, 100, 60, math.pi / 6)
print(x,y);

```
返回值其实是一个`tuple` 但是，在语法上，返回一个`tuple`可以省略括号，而多个变量可以同时接收一个tuple，按位置赋给对应的值，所以，Python的函数返回多值其实就是返回一个`tuple`，但写起来更方便。


##综合案例:
定义一个函数quadratic(a, b, c)，接收3个参数，返回一元二次方程：
```py
ax2 + bx + c = 0
```
的两个解。

公式:
```py
x=(-b±√(b^2-4ac))/2a
```
a为0的时候只有一个解，`b^2-4ac<0`的时候无解。
```py
import math

def quadratic(a, b, c):
    if(a==0 and b==0):
        return;
    delta=b*b-4*a*c
    if(delta<0):
        print("此方程无解")
        return;
    elif(a==0 and b!=0):
        return -c/b
    else:
        return (-b+math.sqrt(delta))/2*a,(-b-math.sqrt(delta))/2*a

a=input("输入a");
b=input("输入b");
c=input("输入c");

r=quadratic(int(a), int(b), int(c));
print(r);

```