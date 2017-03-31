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

python并不像Java语言中使用`{}`包裹执行语句, python是识别冒号`:`后的缩进的

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

下面代码，只要x是非零数值、非空字符串、非空list等，就判断为`True`，否则为`False`。
```py
if x:
    print('True')
```


##注意 
1. 不要忘了写冒号`:`

###条件判断的问题
最后看一个有问题的条件判断。很多同学会用input()读取用户的输入，这样可以自己输入，程序运行得更有意思：
```
birth = input('birth: ')
if birth < 2000:
    print('00前')
else:
    print('00后')
```
上面代码执行后，输入数字会报错， 因为input输入的都是字符串,需要通过`int()`函数转换成整数
```
s = input('birth: ')
birth = int(s)
if birth < 2000:
    print('00前')
else:
    print('00后')
```

