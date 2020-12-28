#vSphere

---

ESXi 主机忘记密码

fdisk -l查看磁盘分区，查看到安装了VMWare ESXi的盘为gpt的

ESXi密码文件保存在sda5分区上，将其挂载至mnt

mount  /dev/sda5/ mnt/sda5

cd /mnt/sda5

将文件 state.tgz复制到/tmp下，并用命令tar xzf state.tgz解压，解压的文件为local.tgz,再次解压tar xzf local.tgz，得到 etc文件夹

cp state.tgz /tmp

cd /tmp

ls -lrt

tar xzf state.tgz

tar xzf  local.tgz

进入到etc，编辑shadow文件，将root:后面的峡谷个：：的内容删除，保存退出

cd etc 

vi shadow

将文件夹etc更新到local.tgz再到state.tgz，将state.tgz拷贝到/mnt下，挂载/mnt，把ubuntu安装盘取出，重启服务器

tar -czf local.tgz etc

tar -czf   state.tgz local.tgz  

cp state.tgz  /mn/sda5

reboot

---


重置VCSA6.0 ROOT用户密码

centos7 引导 点击 Troubleshooting

选择“Rescue a Red Hat Enterprise Linux system”

选择continue继续

vi /mnt/sysimage/grub/menu.lst

将带有password的一行代码删掉，然后保存退出。

重启系统 按e 进入

选择kernel /.......一行

在命令行后加入一行代码 init=/bin/bash  

回车返回上级菜单

在kernel /.....这行按“b”启动命令行

passwd root

---

vcenter 命令

command>shell

运行以下命令以列出 vCenter Server Appliance 服务：service-control –list

要查看 vCenter Server Appliance 服务的当前状态，请键入以下命令：service-control –status

运行以下命令以启动特定服务：service-control –startservicename

您也可以键入以下命令启动所有服务：service-control –start –all

运行以下命令以停止特定服务：service-control –stopservicename

您也可以键入以下命令停止所有服务：service-control –stop –all

通过find / -type f -size +100M命令，把大于100M的文件都找了出来

df -h 查看磁盘

du -h -x --max-depth=1 查看磁盘

---

vcenter磁盘清理日志

cd /storage/log/vmware/sso/

通过运行以下命令移除旧的 localhost_access_log、vmware-identity-sts 和 vmware-identity-sts-perf 日志文件：

rm localhost_access_log.*

rm vmware-identity-sts.*

rm vmware-identity-sts-perf.*

rm -rf  /var/log/audit.log-

---
