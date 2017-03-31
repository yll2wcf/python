#循环
循环分为 `for...in`和`while`循环
一种是for...in循环，依次把list或tuple中的每个元素迭代出来

比如计算`list`中数的和
```py
sum = 0
for x in [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]:
    sum = sum + x
print(sum)
```
