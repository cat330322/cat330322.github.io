# docker registry

---
###docker本地仓库搭建

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

