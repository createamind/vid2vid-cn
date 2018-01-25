# HTML

生成html文档用于展示

## \_\_init\_\_

添加网页标题
```python
self.doc = dominate.document(title=title)
```

网页自动刷新，reflesh变量表示自动刷新的间隔
```python
meta(http_equiv="reflesh", content=str(reflesh))
```
## get\_image\_dir


## add_header
增加html头结点

## add_table
增加表格,表格用来存放图片
## add_images
动态的在表格中增加图片，

## save

保存html文件为index.html到`web_dir`目录下