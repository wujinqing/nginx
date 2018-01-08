## Nginx笔记


[Nginx下载地址](http://nginx.org/en/download.html)

[Nginx官方文档](http://nginx.org/en/docs/)


### 常用命令

### nginx -s signal
> signal 对应的命令

### nginx -s stop
> fast shutdown：快速停止服务，当快速停止服务时，worker进程与master进程在收到信号后会立刻跳出循环，退出进程。

### nginx -s quit
> graceful shutdown：优雅的关闭，当优雅停止服务时，首先会关闭监听端口，停止接收新的连接，然后把当前正在处理的连接全部处理完，最后在退出进程

### nginx -s reload
> reloading the configuration file：重新加载配置文件，不停机。

> 一旦master进程接收到reload configuration信号后，它会检查配置文件的语法是否正确，然后尝试应用新的配置，

> 如果成功，master进程进程将启动新的worker进程并且给旧的worker进程发送信息，请求他们将自己关闭. 旧的worker进程接收到一个命令并关闭自己，停止接收新的连接
继续服务现有的连接直到所有现有的连接处理完毕，之后旧的worker进程将退出。

> 如果失败，回滚到老的配置，继续用老的配置进行工作。

