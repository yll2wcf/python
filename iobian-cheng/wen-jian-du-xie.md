##文件读写

```py
try:
    f = open('/path/to/file', 'r')   #二进制文件用 rb打开
    print(f.read())
finally:
    if f:
        f.close()
```

Python引入了`with`语句来自动帮我们调用`close()`方法：
```py
with open('/path/to/file', 'r') as f:
    print(f.read())
```
这和前面的try ... finally是一样的，但是代码更佳简洁，并且不必调用`f.close()`方法。


调用`read()`会一次性读取文件的全部内容，如果文件有10G，内存就爆了，所以，要保险起见，可以反复调用`read(size)`方法，每次最多读取size个字节的内容。另外，调用readline()可以每次读取一行内容，调用readlines()一次读取所有内容并按行返回list。因此，要根据需要决定怎么调用。

如果文件很小，read()一次性读取最方便；如果不能确定文件大小，反复调用read(size)比较保险；如果是配置文件，调用readlines()最方便：

```py
for line in f.readlines():
    print(line.strip()) # 把末尾的'\n'删掉
```

文件和读文件是一样的，唯一区别是调用`open()`函数时，传入标识符`'w'`或者`'wb'`表示写文本文件或写二进制文件：

```py
with open('/Users/michael/test.txt', 'w') as f:
    f.write('Hello, world!')
```