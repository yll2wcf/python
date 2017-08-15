#面向对象

和Java思想一样

写法

```py
class Student(object):

    def __init__(self, name, score):
        self.name = name
        self.score = score

    def print_score(self):
        print('%s: %s' % (self.name, self.score))
```

class后面紧接着是类名，即Student，类名通常是大写开头的单词，紧接着是(object),表示该类是从哪个类继承下来的

注意到`__init__`方法前后有两个下划线，第一个参数永远是self，表示创建的实例本身，因此，在`__init__`方法内部，就可以把各种属性绑定到self，因为self就指向创建的实例本身。

有了`__init__`方法，在创建实例的时候，就不能传入空的参数了，必须传入与`__init__`方法匹配的参数，但self不需要传，Python解释器自己会把实例变量传进去


## 权限控制
如果要让内部属性不被外部访问，可以把属性的名称前加上两个下划线`__`
需要注意的是，在Python中，变量名类似`__xxx__`的，也就是以双下划线开头，并且以双下划线结尾的，是特殊变量，特殊变量是可以直接访问的。

修改一下
```py
class Student(object):

    def __init__(self, name, score):
        self.__name = name
        self.__score = score

    def print_score(self):
        print('%s: %s' % (self.__name, self.__score))
```