#运行测试函数

为了运行单元测试，你可以在 manage.py 脚本中添加一个自定义命令。

```py
@manager.command
def test():
    """Run the unit tests."""
    import unittest
    tests = unittest.TestLoader().discover('tests')
    unittest.TextTestRunner(verbosity=2).run(tests)

```

运行单元脚本

```py
>>> python manage.py test
```


 Python 包可用于生成虚拟信息，其中功能相对完善的是 ForgeryPy  参考书中 11.3.1
 
 