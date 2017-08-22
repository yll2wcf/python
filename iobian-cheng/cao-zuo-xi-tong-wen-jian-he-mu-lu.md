##OS 模块

```py
>>> import os
>>> os.name # 操作系统类型
'posix' # posix，说明系统是Linux、Unix或Mac OS X，如果是nt，就是Windows系统。
```

* `uname()` 详细系统信息
* `os.environ` 环境变量
* `os.environ.get('key')` 获取某个环境变量的值


os.path.split()函数，这样可以把一个路径拆分为两部分，后一部分总是最后级别的目录或文件名：

```py
>>> os.path.split('/Users/michael/testdir/file.txt')
('/Users/michael/testdir', 'file.txt')
```
os.path.splitext()可以直接让你得到文件扩展名，很多时候非常方便：
```
>>> os.path.splitext('/path/to/file.txt')
('/path/to/file', '.txt')
```

`shutil`模块中找到很多实用函数，它们可以看做是`os`模块的补充。比如`copyfile()` 函数


###例子 

列出所有的.py文件
```py
>>> [x for x in os.listdir('.') if os.path.isfile(x) and os.path.splitext(x)[1]=='.py']
['apis.py', 'config.py', 'models.py', 'pymonitor.py', 'test_db.py', 'urls.py', 'wsgiapp.py']
```
