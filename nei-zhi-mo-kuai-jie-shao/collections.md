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