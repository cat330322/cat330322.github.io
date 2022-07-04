### docker

```
###
利用docker commit新构镜像
1、停止docker容器
docker stop container01
2、commit该docker容器
docker commit container01 new_image:tag
3、用前一步新生成的镜像重新起一个容器
docker run --name container02 -p 80:80 new_image:tag

###发布网站
npm安装包
npm config set registry https://registry.npm.taobao.org
npm install yarn
yarn config set registry https://registry.npm.taobao.org/
yarn buid 打包
dist 替换服务器
docker build -t 20211202 .
FROM nginx
将dist文件中的内容复制到 /usr/share/nginx/html/ 这个目录下面
COPY dist/  /usr/share/nginx/html/ 
docker run --name=dockervue -d -p 8088:80 20211202

###docker pull Registry
docker run -d -p 5000:5000 --restart=always --name registry registry:2
关闭并删除容器
docker stop registry
docker rm registry
## 查看registry当前仓库的镜像
curl http://10.10.1.45:5000/v2/_catalog
## 添加tag
docker tag nginx:1.19.4 localhost:5000/my-nginx
## 推送到本地仓库
docker push localhost:5000/my-nginx
## 删除本地缓存
docker image remove nginx:1.19.4
docker image remove localhost:5000/my-nginx
## 本地仓库拉取
docker pull localhost:5000/my-nginx

###
内网拉取镜像
1、找一个外网电脑拉取镜像
docker pull xxxx
2、将镜像打包为tar包
docker save -o registry.tar registry
3、scp -P 2288  registry.tar  root@x.x.x0.x:/root/ 
4、利用工具上传内网服务器并载入内网docker
docker load -i registry.tar
docker run -d -p 5000:5000 --name registry -v /usr/local/registry:/var/lib/registry  registry
docker tag nginx 127.0.0.1:5000/nginx
docker tag nginx 10.0.10.237:5000/nginx
docker push 127.0.0.1:5000/nginx
docker push 10.0.10.237:5000/nginx
http://ip:5000/v2/_catalog
 "insecure-registries":["你的IP地址:5000"]

{
  "registry-mirrors": ["https://0wrdwnn6.mirror.aliyuncs.com"],
   "insecure-registries":["你的IP地址:5000"]
 }
 
vi /etc/docker/daemon.json 
{
   "registry-mirrors" :["http://docker.mirrors.ustc.edu.cn",
                                "http://registry.docker-cn.com",
                                "http://hub-mirror.c.163.com"],
     "insecure-registries":["10.0.10.237:5000"]
}
 systemctl restart docker
 systemctl start docker
 
###
从仓库拉取镜像
docker pull myregistry.vechain.com:5000/my-nginx
docker pull myregistry.vechain.com:5000/bdms-scheduler
docker tag old new

###
docker pull redis
docker run -itd --name redis20220127 -p 6379:6379 redis

###docker-owncloud
docker run --name owncloud-mysql -p 3000:3306 -e MYSQL\_ROOT\_PASSWORD=caixianjie -d mysql
docker run --name owncloud -p 80:80 --link owncloud-mysql:db -d  owncloud
docker run --name mysql -p 3000:3306-e MYSQL_ROOT_PASSWORD=root -d mysql:5.7
docker run --name owncloud --link mysql:mysql -d -p 80:80 owncloud

###
docker-jdk
docker pull ubuntu
dockerfile
FROM ubuntu-ssh
ADD jdk-8u211-linux-x64.tar.gz /usr/local/
ENV JAVA_HOME /usr/local/jdk1.8.0_211
ENV CLASSPATH $JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
ENV PATH $PATH:$JAVA_HOME/bin
docker build -t jdk-8u211:20190528 . -f jdk18_211dockerfile
docker build -t ubuntu-jdk2022023 .
docker run -d -it jdk-8u211:20190528 /bin/bash
docker run -d  --name ubuntu-jdk  -p 8000:8000 -p 2290:22 ubuntu-jdk20220233
maven 打包：mvn package
Linux运行jar包
要运行java的项目需要先将项目打包成war包或者jar包，打包成war包需要将war包部署到tomcat服务器上才能运行。而打包成jar包可以直接使用java命令执行。
在linux系统中运行jar包主要有以下几种方式。
一、java -jar XXX.jar
这是最基本的jar包执行方式，但是当我们用ctrl+c中断或者关闭窗口时，程序也会中断执行。
二、java -jar XXX.jar &
&代表在后台运行，使用ctrl+c不会中断程序的运行，但是关闭窗口会中断程序的运行。
三、nohup java -jar XXX.jar &
使用这种方式运行的程序日志会输出到当前目录下的nohup.out文件，使用ctrl+c中断或者关闭窗口都不会中断程序的执行。
三、nohup java -jar XXX.jar >temp.out &
>temp.out的意思是将日志输出重定向到temp.out文件，使用ctrl+c中断或者关闭窗口都不会中断程序的执行。
 mysql -u root -p -D xzs < /usr/local/xzs/sql/xzs-mysql.sql
 nohup java -Duser.timezone=Asia/Shanghai -jar -Dspring.profiles.active=prod  xzs-3.5.0.jar  > start1.log  2>&1 &
 
###
docker pull nginx
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

###docker pull mysql
docker run
    -p 3306:3306
    -e MYSQL_ROOT_PASSWORD=localDocker@mysql
    -v /home/docker/mysql/data:/var/lib/mysql:rw
    -v /home/docker/mysql/log:/var/log/mysql:rw
    -v /home/docker/mysql/conf/my.cnf:/etc/mysql/my.cnf:rw
    -v /home/docker/mysql/mysql-files:/var/lib/mysql-files/
    --name mysql
    --restart=always
    -d mysql
docker run -p 3306:3306 --name mysql02 -e MYSQL_ROOT_PASSWORD=123456 -d mysql：8.0
docker exec -it c4bf367b7155  bash
mysql -uroot -p{密码}
mysql> ALTER USER 'root'@'%' IDENTIFIED WITH mysql_native_password BY 'root';
mysql> alter user 'root'@'%' identified by '123456';
mysql> flush privileges;
# 修改用户对应的密码
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123456';
# 刷新权限
flush privileges;
# 修改用户对应的密码
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY '123456';
# 刷新权限
flush privileges;
grant all privileges on *.* to 'root'@'%' with grant option;
flush privileges;
###
create database how2java 创建数据库
===================================
创建表模板
CREATE TABLE hero (
  id int(11) AUTO_INCREMENT,
  name varchar(30) ,
  hp float ,
  damage int(11) ,
  PRIMARY KEY (id)
)  DEFAULT CHARSET=utf8;
===============
插入记录
insert into hero values (null, '盖伦', 616, 100)
===============
select * from hero 查询所有数据
select count(*) from hero 统计表中有多少条数据
select * from hero limit 0,5 分页查询
=====================
update hero set hp = 818 where id = 1 修改表
========================
delete from hero where id = 1 删除数据

###docker pull gitlab/gitlab-ce
$ docker run -d  -p 443:443 -p 80:80 -p 222:22 --name gitlab --restart always -v /home/gitlab/config:/etc/gitlab -v /home/gitlab/logs:/var/log/gitlab -v /home/gitlab/data:/var/opt/gitlab gitlab/gitlab-ce
-d：后台运行
-p：将容器内部端口向外映射
--name：命名容器名称
-v：将容器内数据文件夹或者日志、配置等文件夹挂载到宿主机指定目录

###Alpine源配置文件
/ # cat /etc/apk/repositories
http://dl-cdn.alpinelinux.org/alpine/v3.11/main
http://dl-cdn.alpinelinux.org/alpine/v3.11/community
/ # cat /etc/apk/repositories
https://mirrors.aliyun.com/alpine/v3.6/main/
https://mirrors.aliyun.com/alpine/v3.6/community/
/ # apk search curl
/ # apk add curl
/ # apk del curl
FROM alpine
RUN echo "https://mirrors.aliyun.com/alpine/v3.6/main/" > /etc/apk/repositories; \
echo "https://mirrors.aliyun.com/alpine/v3.6/community/" >> /etc/apk/repositories; \
apk add curl

###docker-baota
docker run --name baota -id -p 18888:8888 -p 180:80 -p 1888:888 -p 121:21 -p 122:22 ubuntu-ssh
apt update 
wget -O install.sh http://download.bt.cn/install/install-ubuntu_6.0.sh && bash install.sh
bt restart
登陆地址 http://{{面板ip地址}}:8888
初始账号 username
初始密码 password
配置用户名
bt 6
配置密码
bt 5


###
docker-compose      # 拉取镜像
docker-compose up -d nginx     # 运行nginx容器
docker-compose up -d     # 运行所有容器
docker-compose ps     # 查看容器运行状态
docker-compose down     # 停止容器和容器网络
docker-compose rm nginx     # 删除nginx容器
version: '3.1'
services:
###
nginx:

    image: nginx     # 镜像名称

    container_name: nginx     # 容器名字

    restart: always     # 开机自动重启

    ports:     # 端口号绑定（宿主机:容器内）

        - '80:80'

        - '443:443'

    volumes:      # 目录映射（宿主机:容器内）

        - ./conf/nginx.conf:/etc/nginx/nginx.conf

        - ./conf.d:/etc/nginx/conf.d

        - ./html:/usr/share/nginx/html 
###
docker-compose -f docker-compose-portainer.yml -p portainer up -d
-p：项目名称
-f：指定docker-compose.yml文件路径
-d：后台启动
MySQL
5.7
docker-compose -f docker-compose-mysql5.7.yml -p mysql5.7 up -d
8.0
docker-compose -f docker-compose-mysql8.0.yml -p mysql8.0 up -d

###
dockerfile
FROM nginx
RUN echo '这是一个本地构建的nginx镜像' > /usr/share/nginx/html/index.html
RUN yum -y install wget
RUN wget -O redis.tar.gz "http://download.redis.io/releases/redis-5.0.3.tar.gz"
RUN tar -xvf redis.tar.gz
RUN yum -y install wget \
    && wget -O redis.tar.gz "http://download.redis.io/releases/redis-5.0.3.tar.gz" \
    && tar -xvf redis.tar.gz
开始构建$ docker build -t nginx:v3 .

1，构建sshd镜像
[root@localhost ~]# cd /opt/
[root@localhost opt]# mkdir sshd  ##创建目录
[root@localhost opt]# cd sshd/
[root@localhost sshd]# vim Dockerfile  ##编写dockerfile文件
FROM centos    ##下载镜像
MAINTAINER this is sshd <xu>   ##描述信息
RUN yum -y update
RUN yum -y install openssh* net-tools lsof telnet passwd
RUN echo '123456' | passwd --stdin root
RUN sed -i 's/UsePAM yes/UsePAM no/g' /etc/ssh/sshd_config
RUN ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key
RUN sed -i '/^session\s\+required\s\+pam_loginuid.so/s/^/#/' /etc/pam.d/sshd
RUN mkdir -p /root/.ssh && chown root.root /root && chmod 700 /root/.ssh
EXPOSE 22  ##端口
CMD ["/usr/sbin/sshd" , "-D"]
[root@localhost sshd]# docker build -t sshd:new .   ##创建镜像
89432272695ab560b18de75a064428e4a7c4a52dfce223afd2e85132ae6c3c72
[root@localhost sshd]# docker run -d -P sshd:new  ##创建映射和容器
[root@localhost sshd]# docker ps -a  ##查看容器状态
CONTAINER ID        IMAGE               COMMAND               CREATED             STATUS              PORTS                   NAMES
89432272695a        sshd:new            "/usr/sbin/sshd -D"   7 seconds ago       Up 6 seconds        0.0.0.0:32768->22/tcp   sad_fermi
[root@localhost sshd]# ssh localhost -p 32768  ##用ssh登录本地

2，构建systemctl镜像
[root@localhost ~]# cd /opt/
[root@localhost opt]# mkdir systemctl   ##创建目录
[root@localhost opt]# cd systemctl/
[root@localhost systemctl]# vim Dockerfile   ##编写dockerfile文件
FROM sshd:new
ENV container docker   ##环境
RUN (cd /lib/systemd/system/sysinit.target.wants/; for i in *; do [ $i == systemd-tmpfiles-setup.service ] || rm -f $i; done); \
rm -f /lib/systemd/system/multi-user.target.wants/*; \
rm -f /etc/systemd/system/*.wants/*; \
rm -f /lib/systemd/system/local-fs.target.wants/*; \
rm -f /lib/systemd/system/sockets.target.wants/*udev*; \
rm -f /lib/systemd/system/sockets.target.wants/*initctl*; \
rm -f /lib/systemd/system/basic.target.wants/*; \
rm -f /lib/systemd/system/anaconda.target.wants/*;
VOLUME [ "/sys/fs/cgroup" ]
CMD ["/usr/sbin/init"]
[root@localhost systemctl]# docker build -t systemd:lasted .   ##创建镜像
[root@localhost systemctl]# docker run --privileged -it -v /sys/fs/cgroup/:/sys/fs/cgroup:ro systemd:lasted /sbin/init
##privateged container 内的root拥有真正的root权限，否则，container内的root只是外部的一个普通用户权限。
[root@localhost ~]# docker exec -it 23a50d568c75 bash  ##进入容器
[root@23a50d568c75 /]# systemctl status sshd   ##查看状态
3，构建Nginx镜像
登录后复制
[root@localhost ~]# cd /opt/
[root@localhost opt]# mkdir nginx   ##创建Nginx目录
[root@localhost opt]# cd nginx/
[root@localhost nginx]# vim Dockerfile
FROM centos:7
MAINTAINER The is nginx <xu>
RUN yum install -y proc-devel gcc gcc-c++ zlib zlib-devel make openssl-devel wget
ADD nginx-1.12.2.tar.gz /usr/local
WORKDIR /usr/local/nginx-1.12.2/
RUN ./configure --prefix=/usr/local/nginx && make && make install
EXPOSE 80
EXPOSE 443
RUN echo "daemon off;">>/usr/local/nginx/conf/nginx.conf
WORKDIR /root/nginx
ADD run.sh /run.sh
RUN chmod 755 /run.sh
CMD ["/run.sh"]
[root@localhost nginx]# vim run.sh
#!/bin/bash
/usr/local/nginx/sbin/nginx   ##开启Nginx服务
[root@localhost nginx]# mount.cifs //192.168.100.3/LNMP-C7 /mnt/  ##挂载镜像
Password for root@//192.168.100.3/LNMP-C7:   <p></p>
[root@localhost nginx]# cp /mnt/nginx-1.12.2.tar.gz ./   ##复制到当前目录下
[root@localhost nginx]# docker build -t nginx:new .   ##创建镜像
[root@localhost nginx]# docker run -d -P nginx:new    ##创建容器
228c1f5b8070d52c6f19d03159ad93a60d682a586c0b1f944dc651ee40576a3e
[root@localhost nginx]# docker ps -a   ##查看容器
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                        PORTS                                           NAMES
228c1f5b8070        nginx:new           "/run.sh"                9 seconds ago       Up 8 seconds                  0.0.0.0:32770->80/tcp, 0.0.0.0:32769->443/tcp   busy_booth
##用浏览器访问网页
FROM ubuntu
ENV TZ Asia/Shanghai
ENV LANG zh_CN.UTF-8
RUN sed -i 's#http://archive.ubuntu.com/#http://cn.archive.ubuntu.com/#' /etc/apt/sources.list
RUN apt-get update && \
apt-get -y install vim && \
apt-get -y install openssh-server && \
apt-get clean && \
rm -rf /tmp/* /var/lib/apt/lists/* /var/tmp/*
RUN echo 'root:root' |chpasswd
RUN sed -ri 's/^PermitRootLogin\s+.*/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN sed -ri 's/UsePAM yes/#UsePAM yes/g' /etc/ssh/sshd_config
RUN mkdir /var/run/sshd
EXPOSE 2299
#Start ssh Service
CMD ["/usr/sbin/sshd", "-D"]
```
