###Arch-UFEI

---

timedatectl set-ntp true

向parted命令加载sdx分区

parted /dev/sdx

建立gpt分区表

(parted)mklabel gpt

建立ESP分区

(parted) mkpart primary 1 512M

建立剩余部分全部分区

(parted) mkpart primary 512M -1

设定ESP分区标志：boot

(parted) set 1 boot on

查看与退出

(parted) p

(parted) q

生成ESP分区的文件系统FAT32

mkfs.vfat -F32 /dev/sdx(n)

对其他分区进行分区进行格式化

mkfs.ext4 /dev/sdx(n)

建立swap分区

mkswap /dev/sdx(n)

挂载分区

mount /dev/sdx(n) /mnt(挂载根分区)
mkdir /mnt/boot(建立boot目录)
mount /dev/sdx(n)/mnt/boot(挂载boot分区)
mkdir /mnt/boot/efi(建立efi分区)
mount /dev/sdx(n) /mnt/boot/efi(挂载efi分区)
mkdir /home(建立home目录)
mount /dev/sdx(n) /mnt/home(挂载home分区)
swapon /dev/sdx(n)(激活swap分区)


fdisk -l

mkfs.ext4 /dev/sda1

mount /dev/sda1 /mnt

vim /etc/pacman.d/mirrorlist

Server = http://mirrors.163.com/archlinux/$repo/os/$arch

pacstrap /mnt base linux linux-firmware base-devel 

genfstab -U /mnt >> /mnt/etc/fstab

cat /mnt/etc/fstab

arch-chroot /mnt

ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime

hwclock –systohc 

nano /etc/locale.gen

 en_US.UTF-8 UTF-8
 
 zh_CN.UTF-8 UTF-8

locale-gen
nano /etc/locale.conf    》 LANG=en_US.UTF-8 输入保存 

pacman -S vim

pacman -S net-tools

pacman -S dhcpcd

systemctl enable dhcpcd

pacman -S grub efibootmgr

grub-install --efi-directory=/boot/efi --bootloader-id=arch-grub --recheck

grub-mkconfig -o /boot/grub/grub.cfg

passwd root

---

pacman -S xorg

sudo pacman -S xf86-video-intel  #intel#

sudo pacman -S xf86-input-libinput
sudo pacman -S xf86-input-synaptics  #触摸板驱动#

sudo pacman -S sddm

systemctl enable sddm

执行# pacman -S konsole

pacman -S plasma

添加用户

useradd -m -g users -G wheel -s /bin/bash arch

执行：# passwd 用户名

执行：# nano /etc/sudoers

在 root ALL=(ALL) ALL 下面添加

用户名 ALL=(ALL) ALL

pacman -S networkmanager net-tools

systemctl enable NetworkManager

九.安装声音软件包

pacman -S alsa-utils pulseaudio pulseaudio-alsa

~/.xprofile export LC_ALL=zh_CN.UTF-8 中文界面

装wqy-zenhei和wqy-microhei两个包就可以了 中文语言
