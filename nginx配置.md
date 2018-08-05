# Nignx 配置方法

> `注意`:整个 Nginx 配置本质上实在维护一颗配置文件树 —— Nginx.conf，树的根是 Nginx.conf 。 通过 include 引如 module 配置 和 server 配置。

## `nginx.conf` 配置

```
# For more information on configuration, see:
#   * Official English Documentation: http://nginx.org/en/docs/
#   * Official Russian Documentation: http://nginx.org/ru/docs/

user nginx;
worker_processes auto;
error_log /var/log/nginx/error.log;
pid /var/run/nginx.pid;

# Load dynamic modules. See /usr/share/nginx/README.dynamic.
include /usr/share/nginx/modules/*.conf;

events {
    worker_connections  1024;
}


http {
    log_format  main  '$remote_addr - $remote_user [$time_local] "$request" '
                      '$status $body_bytes_sent "$http_referer" '
                      '"$http_user_agent" "$http_x_forwarded_for"';

    access_log  /var/log/nginx/access.log  main;

    sendfile            on;
    tcp_nopush          on;
    tcp_nodelay         on;
    keepalive_timeout   65;
    types_hash_max_size 2048;

    include             /etc/nginx/mime.types;
    default_type        application/octet-stream;

    # Load modular configuration files from the /etc/nginx/conf.d directory.
    # See http://nginx.org/en/docs/ngx_core_module.html#include
    # for more information.
    include /etc/nginx/conf.d/*.conf;
}
```

## `server.conf` 配置

```
server {
    listen       80; # 设置监听端口
    # listen       [::]:80 default_server;
    server_name  _;
    root         /var/static/LearnHTTPServer/; # 文件寻址根路径

    # Load configuration files for the default server block.

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

- module 文件是 .so文件
- 可以自己开发 module
