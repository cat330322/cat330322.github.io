###docker

---

/etc/docker/daemon.json

{
  "registry-mirrors" :[     
    "http://docker.mirrors.ustc.edu.cn",
    "http://registry.docker-cn.com",
    "http://hub-mirror.c.163.com"]
}

---

docker run -dit --name mynginx -p 80::80  nginx:latest

docker build -t  [镜像名] .

docker commit container-name  new-image-name

---

### docker group

sudo groupadd docker #添加docker用户组

sudo gpasswd -a $USER docker #将当前登陆用户加入到docker用户组中

newgrp docker #更新用户组

---

###docker 加速

# /etc/docker/daemon.json

{

    "registry-mirrors": ["http://hub-mirror.c.163.com"]
    
}

systemctl restart docker.service

---

###alpine

docker run -it -p 80:80 alpine:latest 

sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories

apk update

apk add nginx 

---
### cp

sudo docker cp host_path containerID:container_path

sudo docker cp containerID:container_path host_path

---
### dockerfile

FROM	基础镜像

RUN	制作镜像过程中需要的执行命令(安装服务)

CMD	容器启动的时候执行的初始命令，容易被替换(启动服务)

ENTRYPOINT  容器启动的时候执行的初始命令，不能被替换，如果同时使用CMD和ENTRYPOINT，cmd命令将作为ENTRYPOINT命令的参数

ADD	把dockerfile当前目录下的文件拷贝到容器中（自动解压tar包）

COPY	把dockerfile当前目录下的文件拷贝到容器中（不解压tar包）

WORKDIR 指定容器的默认工作目录

EXPOSE  镜像要暴露的端口

VOLUME  持久化卷

ENV	环境变量(ssh的密码,数据库的密码)

LABEL	镜像的属性标签

MAINTAINER  管理者标识

---

###docker network

docker network ls

docker network create my_net

docker network create default_network

docker network inspect default_network

docker network create -d macvlan  --subnet=192.168.209.0/24 --gateway=192.168.209.2 -o parent=eno16777728 mynet

-d macvlan  加载kernel的模块名

--subnet 宿主机所在网段

--gateway 宿主机所在网段网关

-o parent 继承指定网段的网卡

docker network create -d macvlan  --subnet=172.1.1.0/24 --gateway=172.1.1.254 -o parent=enp2s0f0 bridge-local

docker run --net=mynet --ip=192.168.209.152  -it --rm centos /bin/bash

--ip 可以指定容器的IP

docker run -d -it -p 8888:8888 -p 80:80 -p --net=bridge-local --ip=172.1.1.150  -it ubuntu-baota

docker run -d -it -P 

---

###mysql

mysql -u root -p

show databases;

use wordpress;

show tables;

desc wp_users;

select *from wp_user;

UPDATE wp_users SET user_pass = MD5( '123456' ) WHERE user_login = 'admin';

---

# docker registry

---

# docker本地仓库搭建

docker pull registry

mkdir /opt/data/registry -p

sudo docker run -itd  -p 5000:5000 --restart=always  -v /opt/data/registry/:/var/lib/registry --name registry registry:2

curl 172.1.1.201:5000/v2/_catalog

netstat -anput | grep 5000

sudo vi /usr/lib/systemd/system/docker.service

ExecStart=/usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock --insecure-registry [resgistryIP]:5000

docker tag ubuntu:v1 172.1.1.201:5000/ubuntu_v1

dokcer images

docker push IP/ubuntu_v1

sudo docker pull  本地仓库IP地址:5000/alpine

例：
docker pull busybox

docker tag busybox 192.168.10.59:5000/busybox

docker push 192.168.10.59:5000/busybox

---

借助nginx ssl 认证

docker pull registry

docker run  -p 5000:5000  --restart=always   -v /data/myregistry:/var/lib/registry -d  registry

http://127.0.0.01:5000/v2/_catalog

{ "insecure-registries":["192.168.116.148:5000"] } //添加damon

docker tag busybox  127.0.0.1:5000/busybox-test //重命名镜像，添加新的tag，使之与registry 相匹配

docker rmi 127.0.0.1:5000  //busybox-test 删除镜像

docker pull  127.0.0.1:5000/busybox-test //从本地镜像下载。

---

#dokcer-bind

docker-sameersbn/bind


docker run --name bind -d --restart=always \

--publish 53:53/tcp --publish 53:53/udp --publish 10000:10000/tcp \

--volume /srv/docker/bind:/data \

--net=bridge-local --ip=172.1.1.11 \

sameersbn/bind:latest



docker run --name bind13 -d --restart=always \

--volume /srv/docker/bind13:/data \

--net=bridge-local --ip=172.1.1.13 \

sameersbn/bind

---

netstat -anp 查看端口

kill -9 pid

/usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf 启动进程


