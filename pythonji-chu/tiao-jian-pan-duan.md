#条件判断

关键字: `if` `else` `elif`

`elif`是`else if`的缩写，完全可以有多个`elif`，所以if语句的完整形式就是：

```py
if <条件判断1>:
    <执行1>
elif <条件判断2>:
    <执行2>
elif <条件判断3>:
    <执行3>
else:
    <执行4>
```

python并不像Java语言中使用`{}`包裹执行语句, python是识别缩进的

```py
age = 3
if age >= 18:
    print('your age is', age)
    print('adult')
else:
    print('your age is', age)
    print('teenager')
```
输出
```
your age is 3
teenager
```
