#### 启动nginx

``` shell
service nginx start
nginx
```

#### 停止nginx

```
nginx -s stop
```

#### 平滑重启nginx

```
nginx -s reload
```

> 平滑启动的意思是在不停止nginx的情况下，重启nginx，重新加载配置文件，启动新的工作线程，完美停止旧的工作线程。

#### 检查对nginx.conf文件的修改是否正确

```
nginx -t -c /etc/nginx/nginx.conf  
```

or   

```
nginx -t  
```

#### 查看nginx的版本

```
nginx -v   
```