###ssh

--

ssh-keygen -t rsa //生成密钥

---

ssh：agent，ssh-add

启动ssh代理并添加密钥

ssh-agent $SHELL

eval `ssh-agent` 

[ssh-keygen]

1、把专用密钥添加到 ssh-agent 的高速缓存中：

ssh-add /root/.ssh/id_dsa

2、从ssh-agent中删除密钥：

ssh-add -d ~/.ssh/id_xxx.pub

3、查看ssh-agent中的密钥：

ssh-add -l

ssh-add -X 解锁

ssh-add -x 加锁

ssh-add -L查看私钥对应公钥

ssh-copy-id -i /root/.ssh/id_rsa root@xx.xx.xx.xx

ssh root@xx.x.x.x

非默认，手动指定ssh -i ~/.ssh/id_rsa_tst1 root@x.x.x.x

ssh-keygen -f /root/.ssh/id_rsa -P'123456'

一次输入

ssh-agent bash

ssh-add /root/.ssh/id_rsa

ssh -i /root/.ssh/id_rsa root@x.x.x.x

ssh
正向代理（-L）：相当于 iptable 的 port forwarding、本地起端口映射到其他机器

HostB$ ssh -L 8888 UserC@HostC1

HostA$ ssh -L 8888:HostC:22 UserB@HostB1

反向代理（-R）：相当于 frp 或者 ngrok 非本地起端口映射到其他机器

HostC$ ssh -R 8888:HostD:22 UserB@HostB1

HostC$ ssh -R 8888:localhost:22 UserB@HostB1


socks5 代理（-D）：相当于 ss/ssr 本地或非本地起 Socket Proxy

HostA$ ssh -D 80801

HostA$ ssh -D 8080 UserB:HostB

HostA$ ssh -D localhost:8080 -p 22 UserB:HostB123

