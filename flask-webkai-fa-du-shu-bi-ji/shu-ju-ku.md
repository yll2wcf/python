# 数据库

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

`__repr()__` 方法，返回一个具有可读性的字符 串表示模型，可在调试和测试时使用。

添加数据先添加到数据库会话中，然后在`commit()`   
调用 `db.session.rollback()` 后，添加到数据库会话 中的所有对象都会还原到它们在数据库时的状态。

## 语句

```py
 >>> db.session.delete(mod_role)     
 >>> db.session.commit()


>>> Role.query.all()


>>> User.query.filter_by(role=user_role).all()
```

通过`str()` 获取SQL语句
```py
>>> str(User.query.filter_by(role=user_role))'SELECT users.id AS users_id, users.username AS users_username, users.role_id AS users_role_id FROM users WHERE :param_1 = users.role_id'
```
![](/assets/1504773100230.jpg)




#数据库迁移

```
(venv) $ pip install flask-migrate
```
配置 Flask-Migrate

```py 
from flask.ext.migrate import Migrate, MigrateCommand 
 ...     
migrate = Migrate(app, db)     
manager.add_command('db', MigrateCommand)
```
初始化
```
python manager.py db init
```
创建脚本语句
```
python manager.py db migrate -m "initial migration"
```

