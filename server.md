# server

## SerializingSocket
序列化类

### send_zipped_pickle
将一个对象先进行zlib压缩，然后转换成pickle

### recv_zipped_pickle
与`send_zipped_pickle`对应，这里是反向重建一个对象

### send_array
将一个numpy对象结合一些元数据输出

### recv_array
与`send_array`对应，反向重建一个numpy对象

---
## test
测试
先请启动一个socket 服务器和客户端，然后分别调用`send_zipped_pickle`和`send_array`序列化数据，传输到另一端，然后在另一端反序列化

## start_server
启动socket服务器，默认是5557 端口
发送一个序列化的numpy 对象

## client

启动socket客户端
接受这个服务器发送的numpy对象并反序列化
