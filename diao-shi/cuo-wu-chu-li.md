#错误处理

```py

import logging

try:
    print('try...')
    r = 10 / int('2')
    print('result:', r)
except ValueError as e:
    logging.exception(e)
except ZeroDivisionError as e:
    logging.exception(e)
else:
    print('no error!')
finally:
    print('finally...')
print('END')

```

Python内置的`logging`模块可以非常容易地记录错误信息


`raise` 关键字抛出错误
```py
raise FooError('invalid value: %s' % s)  
```
`raise`语句如果不带参数，就会把当前错误原样抛出。