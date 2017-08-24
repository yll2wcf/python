#MySql使用

由于`python3`的更新，原来的`mysqldb`的驱动无法使用了，所以我们需要使用另外一个mysql的驱动pymysql
我们可以通过pip安装`pymysql`
```
pip3 install pymysql
```

代码

```py
import pymysql

# 链接数据库
conn = pymysql.connect(host='127.0.0.1', port=3306, user='root', passwd='', db='test')
cursor = conn.cursor()
# 创建user表:
cursor.execute('create table user (id varchar(20) primary key, name varchar(20))')
# 插入一行记录，注意MySQL的占位符是%s:
cursor.execute('insert into user (id, name) values (%s, %s)', ['1', 'Michael'])
print(cursor.rowcount)
# 提交事务
conn.commit()
cursor.close()
```


查询操作

```py
# 链接数据库
conn = pymysql.connect(host='127.0.0.1', port=3306, user='root', passwd='', db='test')
cursor = conn.cursor()

cursor.execute('select * from user where id = %s', ('1',))
values = cursor.fetchall()
print(values)

# 提交事务
conn.commit()
cursor.close()
```