#路由
例子 
 `http://www.facebook.com/<your-name>`， 用 户 名 (your-name)是地址的一部分。Flask 支持这种形式的 URL
```py
@app.route('/user/<name>')      
def user(name):
    return '<h1>Hello, %s!</h1>' % name
```

不过也可使用类型定义。例如，路由 `/user/<int:id>` Flask 支持在路由中使用 int、float 和 path 类型。 path 类型也是字符串


启动模式`debug`为`True`

```py
if __name__ == '__main__':
    app.run(debug=True)

```




#框架 

flask-bootstrap  
Flask-Moment本地化日期和时间
Flask-Moment 是一个 Flask 程序扩展，能把 moment.js 集成到 Jinja2 模板中。