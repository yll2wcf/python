#list

Python内置的一种数据类型是列表：list。list是一种有序的集合，可以随时添加和删除其中的元素。
```py
>>> classmates = ['Michael', 'Bob', 'Tracy']
>>> classmates
['Michael', 'Bob', 'Tracy']
```

用len()函数可以获得list元素的个数。
不能越界,记得最后一个元素的索引是len(classmates) - 1。
如果要取最后一个元素，除了计算索引位置外，还可以用-1做索引，直接获取最后一个元素：
```
>>> classmates[-1]
'Tracy'
```

-2 为倒数第二个  -3 倒数第三个  以此类推

##方法

`append()`追加元素
`insert()`插入元素
`pop()` 删除最后元素或指定元素
要把某个元素替换成别的元素，可以直接赋值给对应的索引位置：

```py
classmates.append('Adam')
classmates.insert(1, 'Jack')
classmates.pop()
classmates.pop(1)
classmates[1] = 'Sarah'
```
