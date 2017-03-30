#运行第一个程序

指令输入`python3`  windows输入`python`
进入控制台，接下来敲的都是`python`代码
```py
>>> 100+200
300
```
`print()`函数输出打印文字

```py
>>> print('hello, world')
hello, world
```


##文件编写

在Mac和Linux可以双击 `py`文件执行.

首先需要在`.py`文件的第一行加上一个特殊的注释：
`helloworld.py`
```py
#!/usr/bin/env python3

print('hello world')
```
然后，通过命令给`helloworld.py`以执行权限：
```
$ chmod a+x hello.py
```