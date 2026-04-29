```bash
$ git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
$ vim ~/.tmux.conf

# 插件列表
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-resurrect'
set -g @plugin 'tmux-plugins/tmux-continuum'

# 开启自动保存和自动恢复
set -g @continuum-restore 'on'

# 尝试恢复窗格内容和 bash 历史记录（关键点）
set -g @resurrect-capture-pane-contents 'on'
set -g @resurrect-save-bash-history 'on'
set -g @continuum-save-interval '5' # 5 min autosave
set -g status-right 'Continuum status: #{continuum_status}'

# 初始化 TPM (放在文件最后)
run '~/.tmux/plugins/tpm/tpm'

$ tmux source ~/.tmux.conf

$ tmux
$ (in tmux session) Prefix + I to reload session

# TEST
$ ls ~/.tmux/plugins/
# make sure tpm/ tmux-resurrect/ tmux-continuum/ in it

# Prefix + Ctrl-s should show state saved!
# 👉 请紧盯屏幕底部的状态栏！你应该会看到一行字闪过：Tmux environment saved! (只有看到这句话，才说明存档文件真正写入到你的硬盘里了)

```

