# CycleGAN模型


## initialize 初始化 

  1. 定义生成器网络

  ```python
  self.netG_A = ...
  self.netG_B = ...
  ```

  2. 如果是训练模式才需要判别器网络
  ```python
  if self.isTrain:
              use_sigmoid = opt.no_lsgan
              self.netD_A = ...
              self.netD_B = ...
  ```

  3. 如果是继续上次的训练过程， 就需要从外部载入生成器和判别器网络

  ```python
    if not self.isTrain or opt.continue_train:
      which_epoch = opt.which_epoch
      self.load_network(self.netG_A, 'G_A', which_epoch)
      self.load_network(self.netG_B, 'G_B', which_epoch)
      if self.isTrain:
          self.load_network(self.netD_A, 'D_A', which_epoch)
          self.load_network(self.netD_B, 'D_B', which_epoch)
  ```

  4. 训练模式载入各种参数
  - self.old_lr 学习率
  - self.fake_A_pool
  - self.fake_B_pool
  - self.criterionGAN gan损失函数
  - self.criterionCycle = torch.nn.L1Loss() # L1损失函数作为循环的损失函数
  - self.criterionIdt = torch.nn.L1Loss() # L1作为
  - self.optimizer_G 生成器优化器
  - self.optimizer_D_A A判别器的优化器
  - self.optimizer_D_B B 判别器的优化器

  - self.optimizers 优化器列表
  - self.schedulers 

## set_input 设置输入

可以用在A 到 B 网络，也可以用在 B 到 A 网络
AtoB 布尔值表示方向，如果为true ，方向就是A 到 B，否则是B 到 A

## forward 向前传播

但是这里只实现了input变量的初始化

```python
self.real_A = Variable(self.input_A)
self.real_B = Variable(self.input_B)
```

## test 测试

实现了A -> B -> A ; 和 B -> A ->  B 两个步骤


## backward_D_basic 判别器向后传播的一部分

> 是传统的ganloss 步骤
结合real 和fake 两个loss ，然后对loss向后传播
```
loss_D.backward()
```


## backward_D_A 和 backward_D_B

分别是A判别器的向后传播，B判别器的向后传播，区别在于两个read 和 fake 的定义相反



## backward_G 生成器向后传播





## optimize_parameters 优化步骤

包括生成器和判别器的优化步骤和梯度清零



## get_current_errors 获取损失函数值

获取当前的各个网络的损失函数值，以字典的形式返回



## get_current_visuals 获取当前的图像
把real_A,fake_A,rec_A,real_B,fake_B,rec_B tensor转换成图像，组成字典返回

## save 保存网络

保存了所有的生成器和判别器网络