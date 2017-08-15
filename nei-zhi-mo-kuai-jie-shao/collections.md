#collections

collections是Python内建的一个集合模块，提供了许多有用的集合类。

###namedtuple

`namedtuple`是一个函数，它用来创建一个自定义的`tuple`对象，并且规定了`tuple`元素的个数，并可以用属性而不是索引来引用`tuple`的某个元素。

```py
from collections import namedtuple

Point = namedtuple('Point', ['x', 'y'])
p = Point(1, 2)
print(p.x) # 1
print(p.y) # 2 

```
代码Point属于tuple类型，用`namedtuple`可以很方便地定义一种数据类型，它具备tuple的不变性，又可以根据属性来引用，使用十分方便。

表示一个圆
```py
# namedtuple('名称', [属性list]):
Circle = namedtuple('Circle', ['x', 'y', 'r'])
```

###deque

deque是为了高效实现插入和删除操作的双向列表，适合用于队列和栈：
```py
from collections import deque

q = deque(['a', 'b', 'c'])
q.append('x')
q.appendleft('y')
print(q)  # deque(['y', 'a', 'b', 'c', 'x'])
```
`deque`除了实现`list`的`append()`和`pop()`外，还支持`appendleft()`和`popleft()`, 增删元素要比    `list`快

### defaultdict
用`dict`时，如果引用的Key不存在，就会抛出`KeyError`。如果希望key不存在时，返回一个默认值，就可以用`defaultdict`：

```py
>>> from collections import defaultdict
>>> dd = defaultdict(lambda: 'N/A')
>>> dd['key1'] = 'abc'
>>> dd['key1'] # key1存在
'abc'
>>> dd['key2'] # key2不存在，返回默认值
'N/A'
```
注意默认值是调用函数返回的，而函数在创建defaultdict对象时传入。

### OrderedDict
使用`dict`时，Key是无序的。在对`dict`做迭代时，我们无法确定Key的顺序。要保持Key的顺序，可以用`OrderedDict`：

```py
>>> from collections import OrderedDict
>>> d = dict([('a', 1), ('b', 2), ('c', 3)])
>>> d # dict的Key是无序的
{'a': 1, 'c': 3, 'b': 2}
>>> od = OrderedDict([('a', 1), ('b', 2), ('c', 3)])
>>> od # OrderedDict的Key是有序的
OrderedDict([('a', 1), ('b', 2), ('c', 3)])
```
`OrderedDict`的Key会按照插入的顺序排列，不是Key本身排序.

### Counter

`Counter` 是一个简单的计数器，例如，统计字符出现的个数，本质也是 dict

```py
from collections import Counter

c = Counter()
for ch in 'yulianlin':
    c[ch] = c[ch] + 1

print(c) # Counter({'l': 2, 'i': 2, 'n': 2, 'y': 1, 'u': 1, 'a': 1})

```