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

==================================================================
Congratulations! Installed successfully!
==================================================================
外网面板地址: http://xxx/xxx
内网面板地址: http://:8888/3127751f
username: eq3y3cev
password: 0a4ff6b8
If you cannot access the panel,
release the following panel port [8888] in the security group
若无法访问面板，请检查防火墙/安全组是否有放行面板[8888]端口
==================================================================
Time consumed: 1 Minute!