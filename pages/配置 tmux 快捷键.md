- 根据 简书博客 [tmux简洁教程及config关键配置](https://gitee.com/link?target=https%3A%2F%2Fwww.jianshu.com%2Fp%2Ffd3bbdba9dc9) 和 伯乐在线 [Tmux 速成教程：技巧和调整](https://gitee.com/link?target=http%3A%2F%2Fblog.jobbole.com%2F87584%2F) 的两篇博客，我也用上了比较好用的 tmux. 贴一下 tmux 的配置和快捷键作用，以及自己配置的 alias。
- Conf 配置
	- ``` conf
	  # ignore
	  unbind C-b
	  set -g prefix C-b
	  
	  # 设置按键为 vim 按键
	  setw -g mode-keys vi
	  
	  # 使用 alt + 方向键切换 panes
	  bind -n M-Left select-pane -L
	  bind -n M-Right select-pane -R
	  bind -n M-Up select-pane -U
	  bind -n M-Down select-pane -D
	  
	  # 使用 shift + 方向键切换 window
	  bind -n S-Left previous-window
	  bind -n S-Right next-window
	  
	  # 通过 prefix + r 直接更新配置
	  bind-key r source-file ~/.tmux.conf \; display-message "tmux.conf reloaded"
	  
	  # 使用 prefix + h 水平切分窗口
	  bind-key v split-window -h
	  
	  # 使用 prefix + v 垂直切分窗口
	  bind-key h split-window -v
	  
	  # 设置底栏
	  # 颜色
	  set -g status-bg black
	  set -g status-fg white
	  
	  # 对齐方式
	  set-option -g status-justify centre
	  
	  # 左下角
	  set-option -g status-left '#[bg=black,fg=green][#[fg=cyan]#S#[fg=green]]'
	  set-option -g status-left-length 20
	  
	  # 窗口列表，自动以当前文件夹命名 window
	  setw -g automatic-rename on
	  set-window-option -g window-status-format '#[dim]#I:#[default]#W#[fg=grey,dim]'
	  set-window-option -g window-status-current-format '#[fg=cyan,bold]#I#[fg=blue]:#[fg=cyan]#W#[fg=dim]'
	  
	  # 右下角
	  set -g status-right '#[fg=green][#[fg=cyan]%m-%d %H:%M#[fg=green]]'
	  ```
- alias 配置
	- ``` bash
	  alias tm="tmux"
	  alias tma="tmux attach"
	  alias tmt="tmux attach-session -t"
	  alias tmk="tmux kill-session -t"
	  ```
	- 定义了 4 个 alias
		- `tm`  用于快速启动 tmux
		- `tma`  用于快速连接到默认的 tmux 会话
		- `tmt`  用于直接连接指定的 tmux 会话
		- `tmk`  用于 kill 一个会话
- 之后，在使用的过程中，基本上连上远程之后，输入  `tma`  就能够继续工作~