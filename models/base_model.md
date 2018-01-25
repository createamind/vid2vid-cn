# 基础模型（BaseModel）


## 初始化方法(initialize)

```python
self.opt = opt 选项
self.gpu_ids = opt.gpu_ids 用哪些GPU
self.isTrain = opt.isTrain 是否是训练状态
self.Tensor = torch.cuda.FloatTensor if self.gpu_ids else torch.Tensor 使用Tensor 还是 cuda的tensor
self.save_dir = os.path.join(opt.checkpoints_dir, opt.name) 检查点文件保存文件
```

主要是定义一个一些方法等着继承的模型来实现，包括：

- forward: 向前传播
- test：测试
- get_image_paths 获取图片数据的路径
- optimize_parameters 优化参数
- get_current_visuals 
- get_current_errors 获取当前的错误率或者损失函数
- save


实现了下几个功能，给继承的模型来调用，包括：
- save_network 保存模型
- load_network 加载膜
- update_learning_rate 更新学习率，每周期调用一次