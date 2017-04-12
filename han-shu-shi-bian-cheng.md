#高阶函数


以Python内置的求绝对值的函数`abs()`为例
```py
>>> f = abs
>>> f(-10)
10
```
变量f现在已经指向了abs函数本身。直接调用abs()函数和调用变量f()完全相同。

>函数名其实也是变量

`abs`指向`10`后，就无法通过`abs(-10)`调用该函数了！因为`abs`这个变量已经不指向求绝对值函数而是指向一个整数`10`
```py
>>> abs = 10
>>> abs(-10)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'int' object is not callable
```
实际代码不要这么写



**一个函数就可以接收另一个函数作为参数，这种函数就称之为高阶函数。**

```py
def add(x, y, f):
    return f(x) + f(y)
```
用代码验证下:
```py
>>> add(-5, 6, abs)
11
```    