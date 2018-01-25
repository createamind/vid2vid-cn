# AlignedDataset

## initialize 初始化

1. 指定模式
```python
self.dir_AB = os.path.join(opt.dataroot, opt.phase)
```

2. 指定要使用的转换器列表
```python
transform_list = [transforms.ToTensor(),
                transforms.Normalize((0.5, 0.5, 0.5),
                                    (0.5, 0.5, 0.5))]
```


## \_\_getitem\_\_    获取指定索引的数据

1. 将图片转换为RGB模式，调整大小，并标准化（调整平均值和方差）
```python
  AB = Image.open(AB_path).convert('RGB')
  AB = AB.resize((self.opt.loadSize * 2, self.opt.loadSize), Image.BICUBIC)
  AB = self.transform(AB)
```

2. 拆分出A B 两个数据集,并调整图片大小

```python
A = AB[:, h_offset:h_offset + self.opt.fineSize,
    w_offset:w_offset + self.opt.fineSize]
B = AB[:, h_offset:h_offset + self.opt.fineSize,
    w + w_offset:w + w_offset + self.opt.fineSize]
```

2. 如果`no_clipe == False`，就进行裁剪
```python
if (not self.opt.no_flip) and random.random() < 0.5:
    idx = [i for i in range(A.size(2) - 1, -1, -1)]
    idx = torch.LongTensor(idx)
    A = A.index_select(2, idx)
    B = B.index_select(2, idx)
```

2. 转换成灰度图
```python
if input_nc == 1:  # RGB to gray
    tmp = A[0, ...] * 0.299 + A[1, ...] * 0.587 + A[2, ...] * 0.114
    A = tmp.unsqueeze(0)

if output_nc == 1:  # RGB to gray
    tmp = B[0, ...] * 0.299 + B[1, ...] * 0.587 + B[2, ...] * 0.114
    B = tmp.unsqueeze(0)
```