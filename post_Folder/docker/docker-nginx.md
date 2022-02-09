docker search nginx

docker run -d --name mynginx -p 80:80 nginx

docker exec -it 21e1 /bin/bash

进入到nginx容器内部后，我们可以cd /etc/nginx，可以看到相关的nginx配置文件都在/etc/nginx目录下

而nginx容器内的默认首页html文件目录为/usr/share/nginx/html

日志文件位于/var/log/nginx

$ apt-get update

$ apt-get install vim

root@21e1ca6037f8:/etc/nginx/conf.d# vim default.conf

server{

       listen 80;

       charset utf-8;

       server_name 192.168.112.135;


       location / {

          proxy_pass http://192.168.112.135:8080;

          proxy_redirect default;
          
       }

    }
