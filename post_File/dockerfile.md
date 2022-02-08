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
