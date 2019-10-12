tmux 是一个终端扩展器（Terminal multiplexer），或者终端复用工具。它可以在一个屏幕里面创建多个终端。

# 简单使用

直接执行进入 tmux 系统。

```sh
tmux
```

tmux 系统初始界面和原来的终端界面差不多，只是这个是虚拟终端（pseudo terminals），最下面多出了一行状态栏（status line），状态栏显示当前会话（session）信息以及用来输入交互命令（这个和 vim 差不多）。

状态栏显示如下：

```
[0] 0:bash*                     "CN-00121983" 09:45 01-Oct-19
```

其中 `[0]` 在最左边，表示当前会话，并且名称为 0，`0:bash` 表示窗口名称为 0，命令是 bash，`*` 表示当前窗口， `"CN-00121983" 09:45 01-Oct-19` 这部分靠右边对齐，表示主机名和日期。

会话就是 tmux 系统里面的一系列虚拟终端，一个会话可以包含多个窗口。窗口就是整个屏幕的内容，一个窗口可以分为多个矩形面板，每个面板表示一个虚拟终端。

简单来说，一个 tmux 系统可以建立多个会话，一个会话可以建立多个窗口，一个窗口可以分离多个面板。

离开会话，返回真实的终端是按组合键 `ctrl+b,d`，可以试一下。每次直接执行 `tmux` 都会创建一个新的会话。 需要执行 `tmux attach` 返回最近的一次会话。

会话是持久存在的，即使断开连接或离开 tmux，也不会消失。只有离开 tmux 会话，然后通过子命令 kill-session 或 kill-server 杀掉后才会消失。

```sh
$ tmux ls
0: 1 windows (created Tue Oct  1 09:21:19 2019) [274x65]
$ tmux kill-session -t 0
$ tmux ls
no server running on /tmp/tmux-1000/default
```

# 

# 术语

- detach 分离，表示离开终端
- attach 附加，表示进入终端
- pseudo terminals 虚拟终端


