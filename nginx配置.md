# Nignx 配置方法

> `注意`:整个 Nginx 配置本质上实在维护一颗配置文件树 —— Nginx.conf，树的根是 Nginx.conf 。 通过 include 引如 module 配置 和 server 配置。

## `nginx.conf` 配置

## `server.conf` 配置

```
server {
    listen       80; # 设置监听端口
    # listen       [::]:80 default_server;
    server_name  _;
    root         /var/static/LearnHTTPServer/; # 文件寻址根路径

    # Load configuration files for the default server block.
    #  include /etc/nginx/default.d/*.conf;

    location / {
    }

    error_page 404 /404.html;
        location = /40x.html {
    }

    error_page 500 502 503 504 /50x.html;
        location = /50x.html {
    }

}
```

## `module.conf` 配置
