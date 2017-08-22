# StringIO

数据读写不一定是文件，也可以在内存中读写。
`StringIO`顾名思义就是在内存中读写`str`。
```py
>>> from io import StringIO
>>> f = StringIO()
>>> f.write('hello')
5
>>> f.write(' ')
1
>>> f.write('world!')
6
>>> print(f.getvalue())
hello world!
```

`getvalue()`方法用于获得写入后的str。


# BytesIO

如果要操作二进制数据，就需要使用`BytesIO`。和`StringIO`类似，可以用一个`bytes`初始化`BytesIO`

```py
>>> from io import BytesIO
>>> f = BytesIO(b'\xe4\xb8\xad\xe6\x96\x87')
>>> f.read()
b'\xe4\xb8\xad\xe6\x96\x87'
```