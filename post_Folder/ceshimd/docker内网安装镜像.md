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


{
   "registry-mirrors" :["http://docker.mirrors.ustc.edu.cn",
                                "http://registry.docker-cn.com",
                                "http://hub-mirror.c.163.com"],
     "insecure-registries":["10.0.10.237:5000"]
}

 systemctl restart docker
 systemctl start docker


# 3. 从仓库拉取镜像
docker pull myregistry.vechain.com:5000/my-nginx
docker pull myregistry.vechain.com:5000/bdms-scheduler


docker tag old new