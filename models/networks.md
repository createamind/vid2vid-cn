## networks

## 函数系列

### 变量初始化系列
针对 卷积层、线性层、批正则化层

- `init_weights` 初始化方法 根据不同的类型调用一下几个方法
  - `weights_init_normal` 高斯分布初始化
  - `weights_init_xavier` xavier分布初始化
  - `weights_init_kaiming`  kaiming 初始化
  - `weights_init_orthogonal` 正交初始化


### get_norm_layer

###  get_scheduler

### 网络定义

- define_G
  生成器网络定义，which_model_netG 参数决定构成生成器的组件，可以是
  - `resnet_9blocks`
  - `resnet_6blocks`
  - `unet_128`
  - `unet_256`
- define_D
  判别器网络定义，which_model_netD 参数决定构成判别器的组件，可以是
  - `basic`
  - `n_layers`


## 类系列

### GANLoss GAN损失函数
构建GAN损失函数
GAN结构可以是LSGAN ，也可以是传统的GAN
LSGAN 的损失函数使用 MSELoss


### ResnetGenerator 残差网络生成器


### ResnetBlock 残差网络组件


### UnetGenerator Unet 生成器



### UnetSkipConnectionBlock Unet 跨层连接组件

### NLayerDiscriminator NLayer 判别器


### 