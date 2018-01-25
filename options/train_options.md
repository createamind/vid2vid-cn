# train_options 训练使用的超参数

- `display_freq` 在屏幕上打印训练结果的频率
- `display_single_pane_ncols` 如果是个正整数，那么将图片以特定的列书展示在网页上
- `update_html_freq` 在网页上保存训练将结果的频率
- `print_freq` 在命令行展示训练结果的频率
- `save_latest_freq` 保存最新结果的频率
- `save_epoch_freq` 每隔几个周期保存一次检查点文件
- `continue_train` 是否是继续训练，如果是会加载之前的检查点文件作为模型继续训练
- `epoch_count` 开始的周期数，
- `phase` 模式 包括   train, val, test 等等
- `which_epoch` 加载哪个周期的检查点文件
- `niter`  在 niter 次训练内使用初始学习率
- `niter_decay` 在 niter_decay 次训练后学习率线性衰减为 0 
- `beta1` adam 算法的动量系数
- `lr` adam 算法的初始学习率
- `no_lsgan` 不使用 最小二乘GAN ，如果是false ，就使用 vanilla GAN
- `lambda_A`  (A -> B -> A) 损失函数的权重
- `lambda_B` (A -> B -> A) 损失函数的权重
- `pool_size` 生成出现的图片保存多少张
- `no_html` 不要立刻保存训练结果到[opt.checkpoints_dir]/[opt.name]/web/ 文件夹
- `lr_policy` 学习率的变化策略 包括  lambda|step|plateau
- `lr_decay_iters` 每 lr_decay_iters 次训练后给 学习率 乘上 缩减系数 gamma
- `identity` 使用 identity 映射。设置1以外的数还会影响identity映射损失的权重。例如，如果identity loss 的权重比重建loss 的权重小10倍，请设置optidentity = 0.1。

- `load_video` 是否加载video ，如果是1 就加载 video，如果是0 就加载 图片
- `data_dir` 数据存储的位置
- `depth` 3D video 的帧数
- `skip` 每隔一定的帧数保存一次
- `overlap` B 的帧数和A 保持一致
- `isTrain = True` 训练模式

