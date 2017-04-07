#迭代

Python的for循环要比java中的强大许多

只要是可迭代对象，无论有无下标，都可以迭代，比如dict就可以迭代：
```py
>>> d = {'a': 1, 'b': 2, 'c': 3}
>>> for key in d:
...     print(key)
...
a
c
b
```
因为dict的存储不是按照list的方式顺序排列，所以，迭代出的结果顺序很可能不一样。

默认情况下，dict迭代的是`key`。如果要迭代`value`，可以用
```py
for value in d.values()
```
如果要同时迭代`key`和`value`，可以用
```py
for k, v in d.items()
```

字符串也是可迭代对象:

```py
>>> for ch in 'ABC':
...     print(ch)
...
A
B
C
```

通过collections模块的Iterable类型可以判断当前类型是否可以迭代：
```py
>>> from collections import Iterable
>>> isinstance('abc', Iterable) # str是否可迭代
True
>>> isinstance([1,2,3], Iterable) # list是否可迭代
True
>>> isinstance(123, Iterable) # 整数是否可迭代
False
```


>如果要对list实现类似Java那样的下标循环怎么办？

Python内置的`enumerate`函数可以把一个list变成索引-元素对，这样就可以在for循环中同时迭代索引和元素本身
```py
>>> for i, value in enumerate(['A', 'B', 'C']):
...     print(i, value)
...
0 A
1 B
2 C
```

上面的for循环里，同时引用了两个变量，在Python里是很常见的，比如下面的代码：

```py
>>> for x, y in [(1, 1), (2, 4), (3, 9)]:
...     print(x, y)
...
1 1
2 4
3 9
```


##总结
根据前面的知识
```py
tiangan = '甲乙丙丁戊己庚辛壬癸'
dizhi = '子丑寅卯辰巳午未申酉戌亥'

jiazi = [ tiangan[x % len(tiangan)] + dizhi[x % len(dizhi)] for x in range(60)]

print(jiazi)
```
输出结果:
```py
['甲子', '乙丑', '丙寅', '丁卯', '戊辰', '己巳', '庚午', '辛未', '壬申', '癸酉', '甲戌', '乙亥', '丙子', '丁丑', '戊寅', '己卯', '庚辰', '辛巳', '壬午', '癸未', '甲申', '乙酉', '丙戌', '丁亥', '戊子', '己丑', '庚寅', '辛卯', '壬辰', '癸巳', '甲午', '乙未', '丙申', '丁酉', '戊戌', '己亥', '庚子', '辛丑', '壬寅', '癸卯', '甲辰', '乙巳', '丙午', '丁未', '戊申', '己酉', '庚戌', '辛亥', '壬子', '癸丑', '甲寅', '乙卯', '丙辰', '丁巳', '戊午', '己未', '庚申', '辛酉', '壬戌', '癸亥']
```

知识点:

1. len( str )---- 返回字符串长度。
2. %------------- 除完的余数。
3. 字符串[x]字符串第N个字节
4. [x for x in range(60)]  根据`for`循环生成list