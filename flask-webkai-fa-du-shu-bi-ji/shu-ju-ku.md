#数据库

```py
mysql://username:password@hostname/database 
postgresql://username:password@hostname/database 
sqlite:////absolute/path/to/database 
sqlite:///c:/absolute/path/to/database
```

```py
class Role(db.Model):
    __tablename__ = 'roles'
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(64), unique=True)
    users = db.relationship('User', backref='role', lazy='dynamic')

    def __repr__(self):
        return '<Role %r>' % self.name
```

![](/assets/1504665015593.jpg)

![](/assets/1504665108828.jpg)


```__repr()__``` 方法，返回一个具有可读性的字符 串表示模型，可在调试和测试时使用。