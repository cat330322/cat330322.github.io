docker

---

/etc/docker/daemon.json

{

  "registry-mirrors" :[     
  
    "http://docker.mirrors.ustc.edu.cn",
    
    "http://registry.docker-cn.com",
    
    "http://hub-mirror.c.163.com"]
    
}


sudo systemctl daemon-reload
     
sudo systemctl restart docker

---

vim /etc/apt/sources.lst

deb http://mirrors.zju.edu.cn/kali kali-rolling main contrib non-free

deb-src http://mirrors.zju.edu.cn/kali kali-rolling main contrib non-free

安装docker

curl -fsSL http://mirrors.zju.edu.cn/docker-ce/linux/debian/gpg | apt-key add -
 
echo 'deb http://mirrors.zju.edu.cn/docker-ce/linux/debian/ buster stable' |  tee /etc/apt/sources.list.d/docker.list
 
apt-get update
 
apt-get install docker-ce

---
docker镜像迁移

docker save mynewimage > /tmp/mynewimage.tar

docker load < /tmp/mynewimage.tar

docker save -o [image].tar

docker load -i [image].tar

---

docker run -dit --name mynginx -p 80::80  nginx:latest

docker build -t  [镜像名] .

docker commit container-name  new-image-name

---

docker group

sudo groupadd docker #添加docker用户组

sudo gpasswd -a $USER docker #将当前登陆用户加入到docker用户组中

newgrp docker #更新用户组

---

alpine

docker run -it -p 80:80 alpine:latest 

sed -i 's/dl-cdn.alpinelinux.org/mirrors.tuna.tsinghua.edu.cn/g' /etc/apk/repositories

apk update

apk add nginx 

---

cp

sudo docker cp host_path containerID:container_path

sudo docker cp containerID:container_path host_path

---

dockerfile

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

docker network

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
docker离线安装

下载地址：https://download.docker.com/linux/static/stable/x86_64/

tar xvf docker-19.03.9.tgz

ls -l docker

mv docker/* /usr/bin/

vim /etc/systemd/system/docker.service

添加文件内容：

[Unit]

Description=Docker Application Container Engine

Documentation=https://docs.docker.com

After=network-online.target firewalld.service

Wants=network-online.target

 

[Service]

Type=notify

ExecStart=/usr/bin/dockerd

ExecReload=/bin/kill -s HUP $MAINPID

LimitNOFILE=infinity

LimitNPROC=infinity

TimeoutStartSec=0

Delegate=yes

KillMode=process

Restart=on-failure

StartLimitBurst=3

StartLimitInterval=60s


[Install]

WantedBy=multi-user.target

chmod +x /etc/systemd/system/docker.service

systemctl daemon-reload 

systemctl enable docker.service

systemctl start docker

---
docker本地仓库搭建

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
docker bind

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
docker-awvs

docker pull secfa/docker-awvs

docker run -it -d -p 13443:3443 secfa/docker-awvs

awvs13 username:admin@admin.com

awvs13 password: Admin123

---

docker pull imdevops/hfish

docker run -d --name hfish -p 21:21 -p 22:22 -p 23:23 -p 69:69 -p 3306:3306 -p 5900:5900 -p 6379:6379 -p 8080:8080 -p 8081:8081 -p 8989:8989 -p 9000:9000 -p 9001:9001 -p 9200:9200 -p 11211:11211 –-net=bridge-local –-ip=172.28.xx.xx --restart=always imdevops/hfish:latest 

docker run -d --name hfish -p  23:23 -p 69:69 -p 3306:3306 -p 5900:5900 -p 6379:6379 -p 8080:8080 -p 8081:8081 -p 8989:8989 -p 9000:9000 -p 9001:9001 -p 9200:9200 -p 11211:11211  --restart=always imdevops/hfish:latest 

---
samba

docker pull dperson/samba 

docker run -it --name samba -p 139:139 -p 445:445 -v //home/share:/mount -d dperson/samba -u "user;pass" -s "share;/mount/;yes;no;no;all;none"

chmod 777 /home/share

---
nessus

docker pull leishianquan/awvs-nessus:v4

docker run -it -d -p 13443:3443 -p 8834:8834 leishianquan/awvs-nessus:v4

/etc/init.d/nessusd start user:leishi,pass:leishianquan

---
kali

docker run --name kali -t -d kalilinux/kali-rolling:latest

---

v2ray 

sudo docker pull v2ray/official

sudo docker run -d --name v2ray -v /home/v2ray:/etc/v2ray -p 11080:11080 v2ray/official  v2ray -config=/etc/v2ray/config.json

sudo docker run -d --name v2ray2 -v /home/v2ray2:/etc/v2ray -p 21080:21080 v2ray/official  v2ray -config=/etc/v2ray/config.json

---
redis

docker pull redis

docker run -itd --name redis1 -p 6379:6379 redis

/etc/init.d/redis-server restart

redis-cli -a abc

redis-cli -h 127.0.0.1 -p 6379

---
mysql

docker pull mysql

sudo docker run -p 3306:3306 --name mysql -e MYSQL_ROOT_PASSWORD=xx -d mysql:5.7

mysql -h 127.0.0.1 -P 3306 -uroot -p123456

---
zabbix

docker pull zabbix/zabbix-web-nginx-mysql:centos-latest

docker run --name zabbix-appliance -t  -p 10051:10051 -p 80:80 -d zabbix/zabbix-appliance:latest

（默认用户Admin,密码zabbix）

