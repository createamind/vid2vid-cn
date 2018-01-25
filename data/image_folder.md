## is_image_file
判断是否是图像文件，满足后缀是 ['.jpg', '.JPG', '.jpeg', '.JPEG','.png', '.PNG', '.ppm', '.PPM', '.bmp', '.BMP',]中的一个


## make_dataset 创建数据集

子文件夹的名字就是数据集的名字，根据子文件夹创建数据集，子文件夹下的所以图片文件的路径都作为`images`数组的元素返回

> os.walk(top, topdown=True, onerror=None, followlinks=False) 
>可以得到一个三元tupple(dirpath, dirnames, filenames), 
> - 第一个为起始路径，
> - 第二个为起始路径下的文件夹，
> - 第三个是起始路径下的文件。

## default_loader 默认的loader
  作用是把打开图片并转换为RGB模式


## ImageFolder

根据数据集的根路径构造一个dataloader，在获取图像前进行转换指定的转换操作