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