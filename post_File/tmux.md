###tmux

---
tmux new -s session

tmux attach-session -t <session_name> //连接会话

tmux kill-session -t <session_name>

ctrl+b x //关闭子窗口

tmux switch -t  <session_name>

tmux rename-session -t  <session_name>

tmux ls

tmux list-commands //列出所有 Tmux 命令及其参数

tmux info //列出当前所有 Tmux 会话的信息

tmux source-file ~/.tmux.conf //重新加载当前的 Tmux 配置

Ctrl+b d && tmux detach //会话分离

Ctrl+b s //列出所有会话

Ctrl+b %//划分左右两个窗格。

Ctrl+b "//划分上下两个窗格。

Ctrl+b //光标切换到其他窗格。是指向要切换到的窗格的方向键，比如切换到下方窗格，就按方向键↓。

Ctrl+b ;//光标切换到上一个窗格。

Ctrl+b o//光标切换到下一个窗格。

Ctrl+b {//当前窗格与上一个窗格交换位置。

Ctrl+b }//当前窗格与下一个窗格交换位置。

Ctrl+b Ctrl+o//所有窗格向前移动一个位置，第一个窗格变成最后一个窗格。

Ctrl+b Alt+o//所有窗格向后移动一个位置，最后一个窗格变成第一个窗格。
Ctrl+b x //关闭当前窗格。

Ctrl+b !//将当前窗格拆分为一个独立窗口。

Ctrl+b z//l+//按箭头方向调整窗格大小。

Ctrl+b q//显示窗格编号。
