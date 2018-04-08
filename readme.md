1. 启动 Nginx
/usr/sbin/nginx
or
nginx
路径可以通过 # whereis nginx 命令看。

2. 停止 Nginx
nginx -s stop
3. 查看 Nginx 进程
ps -ef|grep nginx
4. 平滑启动nginx
nginx -s reload
or
kill -HUP `cat /var/run/nginx.pid`
其中进程文件路径在配置文件nginx.conf中可以找到。

平滑启动的意思是在不停止nginx的情况下，重启nginx，重新加载配置文件，启动新的工作线程，完美停止旧的工作线程。

5. 强制停止nginx
pkill -9 nginx

6. 检查对nginx.conf文件的修改是否正确
nginx -t -c /etc/nginx/nginx.conf
or
nginx -t

7. 查看nginx的版本信息
nginx -v
or
nginx -V

