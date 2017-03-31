#循环
循环分为 `for...in`和`while`循环

### for...in
一种是for...in循环，依次把list或tuple中的每个元素迭代出来

比如计算`list`中数的和
```py
sum = 0
for x in [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]:
    sum = sum + x
print(sum)
```
如果要计算1-100的整数之和，从1写到100有点困难，幸好Python提供一个`range()`函数，可以生成一个整数序列，再通过`list()`函数可以转换为list。比如`range(5)`生成的序列是从0开始小于5的整数：
```py
>>> list(range(5))
[0, 1, 2, 3, 4]
```

`range(101)`就可以生成0-100的整数序列，计算如下：
```py
sum = 0
for x in range(101):
    sum = sum + x
print(sum)
```

### while
只要条件满足，就不断循环，条件不满足时退出循环。
```py
sum = 0
n = 99
while n > 0:
    sum = sum + n
    n = n - 2
print(sum)
```
