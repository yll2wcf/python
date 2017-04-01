#关键字参数
可变参数允许你传入0个或任意个参数，这些可变参数在函数调用时自动组装为一个tuple。而关键字参数允许你传入0个或任意个含参数名的参数，这些关键字参数在函数内部自动组装为一个dict。示例：

```py
def person(name, age, **kw):
    print('name:', name, 'age:', age, 'other:', kw)

```