# train

## ck_array
两个参数(i,o)，分布表示input output，打印输入和输出的A B 之间的差距

## save_videos
参数：
web_dir
visuals
vid_path
epoch
保存video


## 训练步

1. 从opt.epoch_count 个周期开始训练
```python
for epoch in range(opt.epoch_count, opt.niter + opt.niter_decay + 1):
...
```

2. 记录起止时间

```python
iter_start_time = time.time()
...
(epoch, opt.niter + opt.niter_decay, time.time() - epoch_start_time))
...

```
3. 固定间隔保存video
```python
if total_steps % opt.display_freq == 0:
  ...
  save_videos(web_dir, visuals, vid_path, epoch)
````

4. 固定步数间隔和周期间隔保存模型

```python
if total_steps % opt.save_latest_freq == 0:
  ···
  model.save('latest')

if total_steps % 20010 == 0:
  ...
  model.save(total_steps)
...
if epoch % opt.save_epoch_freq == 0:
  ...
  model.save('latest')
  model.save(epoch)
```