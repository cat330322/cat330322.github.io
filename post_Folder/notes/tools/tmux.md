# tmux

 tmux new -s session-name
 
tmux detach

tmux ls

tmux list-session

tmux attach -t 0 使用会话编号

tmux attach -t session-name 使用会话名称

tmux kill-session -t 0 使用会话编号

tmux kill-session -t session-name 使用会话名称

tmux switch -t 0 使用会话编号

tmux switch -t session-name 使用会话名称

tmux rename-session -t 0 new-name

Ctrl+b d：分离当前会话。

Ctrl+b s：列出所有会话。

Ctrl+b $：重命名当前会话。

新建会话tmux new -s my_session。

在 Tmux 窗口运行所需的程序。

按下快捷键Ctrl+b d将会话分离。

下次使用时，重新连接到会话tmux attach-session -t my_session。

tmux split-window 划分上下两个窗格

划分左右两个窗格  tmux split-window -h

Ctrl+b %：划分左右两个窗格。

Ctrl+b "：划分上下两个窗格。

Ctrl+b <arrow key>：光标切换到其他窗格。<arrow key>是指向要切换到的窗格的方向键，比如切换到下方窗格，就按方向键↓。

Ctrl+b ;：光标切换到上一个窗格。

Ctrl+b o：光标切换到下一个窗格。

Ctrl+b {：当前窗格与上一个窗格交换位置。

Ctrl+b }：当前窗格与下一个窗格交换位置。

Ctrl+b Ctrl+o：所有窗格向前移动一个位置，第一个窗格变成最后一个窗格。

Ctrl+b Alt+o：所有窗格向后移动一个位置，最后一个窗格变成第一个窗格。

Ctrl+b x：关闭当前窗格。

Ctrl+b !：将当前窗格拆分为一个独立窗口。

Ctrl+b z：当前窗格全屏显示，再使用一次会变回原来大小。

Ctrl+b Ctrl+<arrow key>：按箭头方向调整窗格大小。

Ctrl+b q：显示窗格编号。
