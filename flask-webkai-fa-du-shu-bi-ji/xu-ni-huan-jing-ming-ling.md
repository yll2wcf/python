#虚拟环境

```py
virtualenv venv  创建虚拟环境

source venv/bin/activate 使用虚拟环境

deactivate 切换到主环境
```


项目需求文件

```py
#导出虚拟文件
 (venv) $ pip freeze >requirements.txt


(venv) $ pip install -r requirements.txt
```