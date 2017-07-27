#sorted 排序算法

排序也是在程序中经常用到的算法。

Python内置的`sorted()`函数就可以对list进行排序：

```py
>>> sorted([36, 5, -12, 9, -21])
[-21, -12, 5, 9, 36]
```
`sorted()`函数也是一个高阶函数，它还可以接收一个key函数来实现自定义的排序，例如按绝对值大小排序：
```py
>>> sorted([36, 5, -12, 9, -21], key=abs)
[5, 9, -12, -21, 36]
```

照ASCII的大小比较的，由于'Z' < 'a'，下面排序不是我们想要的，应该忽略大小写
```py
>>> sorted(['bob', 'about', 'Zoo', 'Credit'])
['Credit', 'Zoo', 'about', 'bob']
```
都改成小写进行排序：
```py
>>> sorted(['bob', 'about', 'Zoo', 'Credit'], key=str.lower)
['about', 'bob', 'Credit', 'Zoo']
```
反向排序,传入第三个参数reverse=True
```py
>>> sorted(['bob', 'about', 'Zoo', 'Credit'], key=str.lower, reverse=True)
['Zoo', 'Credit', 'bob', 'about']
```