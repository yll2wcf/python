#关键字参数
可变参数允许你传入0个或任意个参数，这些可变参数在函数调用时自动组装为一个tuple。而关键字参数允许你传入0个或任意个含参数名的参数，这些关键字参数在函数内部自动组装为一个dict。示例：

使用`**`控制
```py
def person(name, age, **kw):
    print('name:', name, 'age:', age, 'other:', kw)

```
和可变参数类似，也可以先组装出一个`dict`，然后，把该`dict`转换为关键字参数传进去：

```py
>>> extra = {'city': 'Beijing', 'job': 'Engineer'}
>>> person('Jack', 24, **extra)
name: Jack age: 24 other: {'city': 'Beijing', 'job': 'Engineer'}
```
`**extra`表示把`extra`这个`dict`的所有`key-value`用关键字参数传入到函数的`**kw`参数，`kw`将获得一个`dict`，注意`kw`获得的`dict`是`extra`的一份拷贝，对`kw`的改动不会影响到函数外的`extra`。


##命名关键字参数
