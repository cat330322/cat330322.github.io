# Git
---

ssh-keygen -t rsa 

---

git init

git add .

git commit -m "first commit"

git branch -M main

git remote add origin git@github.com:cat330322/cat330322.github.io.git

git push -u origin master

git status

---

#查看当前生效的配置信息

git config -l

git config --global user.name <用户名>

git config --global user.email <邮箱地址>

git config --global http.postBuffer <缓存大小>

调用 git status/git diff 命令时以高亮或彩色方式显示改动状态

git config --global color.ui true

git config --global credential.helper cache  //配置可以缓存密码，默认缓存时间15分钟

git config --global credential.helper 'cache --timeout=<缓存时间>'

git config --global credential.helper store //配置长期存储密码

---
#git clone

git clone <远程仓库的网址> -b <分支名称> <本地目录>  // //-b 指定要克隆的分支，默认是master分支

---
#git remote

git remote -v //列出远程仓库的详细信息，在别名后面列出URL地址

git remote add <远程仓库的别名> <远程仓库的URL地址> //添加远程仓库

git remote rename <原远程仓库的别名> <新的别名>  //修改远程仓库的别名

git remote remove <远程仓库的别名> // 删除指定名称的远程仓库

git remote set-url <远程仓库的别名> <新的远程仓库URL地址> //修改远程仓库的 URL 地址

---
#git branch

git branch -v //列出本地的所有分支并显示最后一次提交，当前所在分支以 "*" 标出

git branch 分支名//创建新分支，新的分支基于上一次提交建立

git branch -M 原分支名称 新的分支名称//修改分支名称

git branch -d <分支名称> //删除指定的本地分支 //git branch -D <分支名称> 

---
#git checkout

git checkout <分支名称> //切换到已存在的指定分支

git checkout -b <分支名称> //创建并切换到指定的分支，保留所有的提交记录,等同于 "git branch" 和 "git checkout" 两个命令合并

git checkout --orphan <分支名称> //创建并切换到指定的分支，删除所有的提交记录

git checkout <文件路径> //替换掉本地的改动，新增的文件和已经添加到暂存区的内容不受影响

---
#git cherry-pick

git cherry-pick <commit ID>  //把已经提交的记录合并到当前分支

---

#git add
git add <文件路径> //把指定的文件添加到暂存区中

git add -u [<文件路径>] //添加所有修改、已删除的文件到暂存区中

git add -A [<文件路径>]//查看所有修改、已删除但没有提交的文件，进入一个子命令系统

git add -i [<文件路径>]

---
###git commit
git commit -m "<提交的描述信息>" //把所有修改、已删除的文件提交到本地仓库中

git commit -a -m "<提交的描述信息>"//修改上次提交的描述信息

---
###git fetch

git diff  //比较当前文件和暂存区中文件的差异，显示没有暂存起来的更改

git diff --cached比较暂存区中的文件和上次提交时的差异

git diff HEAD//比较当前文件和上次提交时的差异

git diff commit -id//查看从指定的版本之后改动的内容

git diff   "分支名称"or"分支名称" //比较两个分支之间的差异

git diff <分支名称>...<分支名称> //查看两个分支分开后各自的改动内容

---
#git pull

git pull从远程仓库获取最新版本。

---
#git push
git push <远程仓库的别名> <本地分支名>:<远程分支名> //把本地仓库的分支推送到远程仓库的指定分支

git push <远程仓库的别名> :<远程分支名>

git push <远程仓库的别名> --delete <远程分支名>

---
###git log
git log 打印所有的提交记录

git log  "commit ID"//打印从第一次提交到指定的提交的记录

git log -指定的数量//打印指定数量的最新提交的记录

---

###git reset

重置暂存区，但文件不受影响

git reset --mixed 文件路径>] //相当于将用 "git add" 命令更新到暂存区的内容撤出暂存区，可以指定文件

git reset --mixed  commit-ID 将 HEAD 的指向改变，撤销到指定的提交记录，文件未修改

git reset --soft [commit ID] 相当于调用 "git reset --mixed" 命令后又做了一次 "git add"

git reset --hard [commit-ID]将 HEAD 的指向改变，撤销到指定的提交记录，文件也修改了

---
###git revert
git revert  commit-ID //生成一个新的提交来撤销某次提交

---
###git tag

git tag //打印所有的标签

git tag 标签名称 commit ID 添加轻量标签，指向提交对象的引用，可以指定之前的提交记录

git tag -a 标签名称 -m 标签描述信息  commit ID//添加带有描述信息的附注标签，可以指定之前的提交记录

git checkout 标签名称//切换到指定的标签

git show 标签名称 //查看标签的信息

git tag -d  标签名称 //删除指定的标签

git push 远程仓库的别名  标签名称 将指定的标签提交到远程仓库

git push 远程仓库的别名 –tags //将本地所有的标签全部提交到远程仓库

---
###git mv
git mv  源文件/文件夹  目标文件/文件夹  //重命名指定的文件或者文件夹

---
###git rm
git rm 文件路径 //移除跟踪指定的文件，并从本地仓库的文件夹中删除

git rm -r 文件夹路径 //移除跟踪指定的文件夹，并从本地仓库的文件夹中删除

git rm --cached //移除跟踪指定的文件，在本地仓库的文件夹中保留该文件

---
#Git操作场景示例删除掉本地不存在的远程分支
多人合作开发时，如果远程的分支被其他开发删除掉，在本地执行 git branch --all 依然会显示该远程分支，可使用下列的命令进行删除：

git pull -p //使用 pull 命令，添加 -p 参数

---
