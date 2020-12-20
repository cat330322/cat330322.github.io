ESXI

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
