# Visualizer
这个类实现一些可视化的功能


## \_\_init\_\_


如果要在html上展示数据,就先建相关的文件夹


```python
if self.use_html:
    self.web_dir = os.path.join(opt.checkpoints_dir, opt.name, 'web')
    self.img_dir = os.path.join(self.web_dir, 'images')
    print('create web directory %s...' % self.web_dir)
    util.mkdirs([self.web_dir, self.img_dir])
```

## reset
重置 saved变量，saved变量表示是否已经保存了图片到文件夹，作用在于防止重复保存时覆盖了先前的图片

## display\_current\_results
展示当前的训练结果

1. 要展示几列图片
```python
ncols = self.opt.display_single_pane_ncols
```

2. 嵌入图片到表格
```python
for label, image_numpy in visuals.items():
  label_html_row += '<td>%s</td>' % label
  images.append(image_numpy.transpose([2, 0, 1]))
  idx += 1
  if idx % ncols == 0:
      label_html += '<tr>%s</tr>' % label_html_row
      label_html_row = ''
```

3. 如果图片数不能整除表格的列数，那么用空白图片填补
```python
while idx % ncols != 0:
    images.append(white_image)
    label_html_row += '<td></td>'
    idx += 1
```

4. 如果图片还没保存就保存图片
```python
if self.use_html and (save_result or not self.saved):
...
```

## plot\_current\_errors
展示迄今为止的损失函数值的变化

x轴是周期数
y轴是损失函数值

## print\_current\_errors

打印当前损失函数，包括，周期数，训练迭代数和时间

## save\_images
保存图片到本地