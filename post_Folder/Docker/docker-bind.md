###dokcer-bind

---

docker-sameersbn/bind

---

docker run --name bind -d --restart=always \

--publish 53:53/tcp --publish 53:53/udp --publish 10000:10000/tcp \

--volume /srv/docker/bind:/data \

--net=bridge-local --ip=172.1.1.11 \

sameersbn/bind:latest


---

docker run --name bind13 -d --restart=always \

--volume /srv/docker/bind13:/data \

--net=bridge-local --ip=172.1.1.13 \

sameersbn/bind

---

netstat -anp 查看端口

kill -9 pid

/usr/bin/perl /usr/share/webmin/miniserv.pl /etc/webmin/miniserv.conf 启动进程


