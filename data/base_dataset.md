# BaseDataset

## BaseDataset 类

用于继承的基础类


## get_transform 图片转换方法
参数`opt`中的属性`resize_or_crop`决定转换模式
有以下几种模式可选：

- `resize_and_crop` 调整图片长宽到`opt.loadSize`并随机 crop
- `crop` 随机 crop
- `scale_width` 调整图片宽度到`opt.fineSize`
- `scale_width_and_crop`   调整图片宽度到`opt.fineSize`并随机 crop


## __scale_width 
调整图片宽度的方法