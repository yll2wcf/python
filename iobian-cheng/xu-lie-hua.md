#序列化

变量从内存中变成可存储或传输的过程称之为序列化，在Python中叫pickling，反之叫unpickling

Python提供了`pickle`模块来实现序列化。

```py
>>> import pickle
>>> d = dict(name='Bob', age=20, score=88)
>>> pickle.dumps(d)
b'\x80\x03}q\x00(X\x03\x00\x00\x00ageq\x01K\x14X\x05\x00\x00\x00scoreq\x02KXX\x04\x00\x00\x00nameq\x03X\x03\x00\x00\x00Bobq\x04u.'
```

或者用另一个方法`pickle.dump()`直接把对象序列化后写入一个file-like Object：
```py
>>> f = open('dump.txt', 'wb')
>>> pickle.dump(d, f)
>>> f.close()
```

读取
```py
>>> f = open('dump.txt', 'rb')
>>> d = pickle.load(f)
>>> f.close()
>>> d
{'age': 20, 'score': 88, 'name': 'Bob'}
```


## JSON

Python内置的`json`模块提供了非常完善的 Python 对象到`JSON`格式的转换。

```py
>>> import json
>>> d = dict(name='Bob', age=20, score=88)
>>> json.dumps(d)
'{"age": 20, "score": 88, "name": "Bob"}'
```

`dumps()`方法返回一个`str`，内容就是标准的`JSON`。类似的，`dump()`方法可以直接把JSON写入一个file-like Object。

要把`JSON`反序列化为`Python`对象，用`loads()`或者对应的`load()`方法，前者把JSON的字符串反序列化，后者从file-like Object中读取字符串并反序列化：
```py
>>> json_str = '{"age": 20, "score": 88, "name": "Bob"}'
>>> json.loads(json_str)
{'age': 20, 'score': 88, 'name': 'Bob'}
```

前面的代码之所以无法把`Student`类实例序列化为`JSON`，是因为默认情况下，`dumps()`方法不知道如何将`Student`实例变为一个`JSON`的{}对象。

可选参数`default`就是把任意一个对象变成一个可序列为JSON的对象，我们只需要为`Student`专门写一个转换函数，再把函数传进去即可：
```py
def student2dict(std):
    return {
        'name': std.name,
        'age': std.age,
        'score': std.score
    }
```
`Studen`t实例首先被`student2dict()`函数转换成`dict`，然后再被顺利序列化为JSON：
```py
>>> print(json.dumps(s, default=student2dict))
{"age": 20, "name": "Bob", "score": 88}
```

下次如果遇到一个Teacher类的实例，照样无法序列化为JSON。我们可以偷个懒，把任意class的实例变为dict：
```py
print(json.dumps(s, default=lambda obj: obj.__dict__))
```
因为通常class的实例都有一个`__dict__`属性，它就是一个dict，用来存储实例变量。也有少数例外，比如定义了`__slots__`的class。

同样的道理，如果我们要把JSON反序列化为一个Student对象实例，loads()方法首先转换出一个dict对象，然后，我们传入的object_hook函数负责把dict转换为Student实例

```py
def dict2student(d):
    return Student(d['name'], d['age'], d['score'])
```