## nginx.conf静态资源服务器配置

```
#user  nobody;

# 工作线程数一般与CPU个数一致
worker_processes  1;

#错误日志文件
#error_log  logs/error.log;
#error_log  logs/error.log  notice;
#error_log  logs/error.log  info;

#Nginx进程ID
#pid        logs/nginx.pid;

events {
    #最大并发连接数
    worker_connections  1024;
}

http {
    include       mime.types;
    default_type  application/octet-stream;

    #log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
    #                  '$status $body_bytes_sent "$http_referer" '
    #                  '"$http_user_agent" "$http_x_forwarded_for"';

    #access_log  logs/access.log  main;

    sendfile        on;
    #tcp_nopush     on;

    #keepalive_timeout  0;
    keepalive_timeout  65;

    #gzip  on;

    server {
        #Nginx监听的端口号
        listen       80;
        #域名
        server_name  localhost;

        #charset utf-8;

        #access_log  logs/host.access.log  main;
        #匹配所有请求
        location / {
            #根目录
            root   html;
            index  index.html index.htm;
        }

        #error_page  404              /404.html;

        # redirect server error pages to the static page /50x.html
        #
        error_page   500 502 503 504  /50x.html;
        location = /50x.html {
            root   html;
        }
    }
}
```