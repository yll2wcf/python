#切片

取一个list或tuple的部分元素是非常常见的操作。Python提供了切片（Slice）操作符
```py
L = ['老于', '小王', '小明', 'Bob', 'Jack']
print(L[0:3]);

```
输出结果 
```py 
['老于', '小王', '小明'] 
```
`L[0:3]`表示，从索引0开始取，直到索引3为止，但不包括索引3

如果个索引是0，还可以省略：
```py
>>> L[:3]
['老于', '小王', '小明']
```
既然Python支持`L[-1]`取倒数第一个元素，那么它同样支持倒数切片，试试：
```py
>>> L[-2:]  
['Bob', 'Jack']
>>> L[-2:-1]
['Bob']
```

##切片高级用法

通过range(100)生成包含0-99的list
```py
>>>L = list(range(100))
```
所有数，每5个取一个：
```py
>>> L[::5]
[0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60, 65, 70, 75, 80, 85, 90, 95]
```

tuple也是一种list，唯一区别是tuple不可变。因此，tuple也可以用切片操作，只是操作的结果仍是tuple：
```py
>>> (0, 1, 2, 3, 4, 5)[:3]
(0, 1, 2)
```