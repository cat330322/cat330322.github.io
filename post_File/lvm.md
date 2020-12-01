lvm分区
---

umount /home 如果提示无法卸载，因为有进程占用/home，使用如下命令来终止占用进程

fuser -m /home  

如果依然无法卸载，使用以下命令：

[root@localhost home]# umount -l /home

---

PV->VG->LV

8e类型来使他们可用于LVM

30=uefi

---

pvcreate /dev/sdb# 创建为物理卷

pvdisplay 

pvremove /dev/sdb1 

---

vgcreate data /dev/sdb1

vgextend data /dev/sdb2  # 将新增的物理卷添加到已有的逻辑卷组中

vgremove  data 

---

lvcreate -l +100%FREE -n lvdata data

lvresize -L 200M /dev/volume-group1/lv1 

lvextend -l +100%FREE /dev/mapper/data-lvdata

e2fsck -f /dev/volume-group1/lv1  检查磁盘错误

resize2fs  /dev/mapper/data-lvdata  #更新磁盘 定义

resize2fs -p /dev/mapper/VolGroup-lv_home 100G #重定义大小

lvremove 

---

mkfs.ext4 /dev/volume-group1/lv1

mkdir /lvm-mount

mount /dev/mapper/lv1 /data
