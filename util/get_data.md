# GetData

## \_\_init\_\_ 

指定要获取pix2pix的数据还是cyclegan的数据

## \_get\_options 
获取指定html文本中连接（\<a\>）中以'.zip' 或者 'tar.gz结尾的连接，即可下载的压缩包的连接列表

## \_present\_options
让用户在从指定连接中获取的不同的数据集中选择一个

## \_download\_data

下载只有的数据集，先下载压缩包到临时目录，然后解压到正式目录，移除压缩包

## get
指定保存路径，调用\_download\_data 函数，返回数据里在本地的绝对路径