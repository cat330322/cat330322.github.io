#Arch
---

官方仓库地址：http://repo.archlinuxcn.org

镜像地址: https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/

使用方法：在 /etc/pacman.conf 文件末尾添加以下两行：

[archlinuxcn]
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch

之后安装 archlinuxcn-keyring 包导入 GPG key。

单用户模式登录

grub single(输入的时候，在single前面输入空格)


使用 ctrl-r 来搜索命令历史记录

 编辑/etc/profile文件
 
在/etc/profile 文件末尾添加

alias vi=‘/usr/bin/vim'

然后在终端下 . /etc/profile 重新加载/etc/profile文件


 firefox.中文界面请安装简体中文语言包 firefox-i18n-zh-cn。

 1. 软件包基础搜索及安装卸载
 
$ pacman -Ss 软件名称 //(搜索软件包)

$ pacman -S 软件名称 //(安装软件包)

$ pacman -Rs 软件名称 //(卸载软件包)

$ pacman -Syu (更新)

yaourt

2. 包的查询及清理

列出所有本地软件包（-Q,query查询本地；-q省略版本号）

$ pacman -Qq (列出有816个包)

列出所有显式安装（-e,explicitly显式安装；-n忽略外部包AUR）

$ pacman -Qqe (列出200个包)

列出自动安装的包（-d,depends作为依赖项）

$ pacman -Qqd (列出616个)

列出孤立的包（-t不再被依赖的"作为依赖项安装的包"）

$ pacman -Qqdt (列出35个)

注意：通常这些是可以妥妥的删除的。(sudo pacman -Qqdt | sudo pacman -Rs -)

3. 软件包和文件的查询

列出包所拥有的文件

$ sudo pacman -Ql iw



