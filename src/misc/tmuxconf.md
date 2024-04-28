# .tmux.conf

```bash
# Quality of life
set -g mouse on
setw -g mode-keys vi

# Enable color modes
set -g default-terminal "screen-256color"
set-option -ga terminal-overrides ",xterm-256color:Tc"

# Disable key escape
set -sg escape-time 0

# Quality of life
set -g mouse on
setw -g mode-keys vi
setw -g history-limit 10000000

# Easy reload config file
bind r source-file ~/.tmux.conf

# Move around panes with hjkl
bind h select-pane -L
bind j select-pane -D
bind k select-pane -U
bind l select-pane -R

########## Styling ##########

# Pane border color
set-option -g pane-active-border-style fg=colour213
set-option -g pane-border-style fg=colour239

# Pane number display
set-option -g display-panes-active-colour colour201
set-option -g display-panes-colour colour189

# Clock
set-window-option -g clock-mode-colour colour207

# Enable status bar
set-option -g status "on"

# Status bar basic setting
set -g status-interval 1
set -g status-left-length 20
set -g status-right-length 50

# [win/cur{/}tab/----------/time]
set-window-option -g window-status-separator ""

# [win/cur/tab/{----------}/time]
set-option -g status-style bg=colour0,fg=colour255

# [{win}/cur/tab/----------/time]
set-option -g status-left "\
#[bg=\#5e5faf, fg=colour189]#{?client_prefix,#[bg=colour167],}  #{?window_zoomed_flag,󰻿 ,}#S\
#[bg=colour0, fg=\#5e5faf]#{?client_prefix,#[fg=colour167],}◤"

# [win/{cur}/tab/----------/time]
set-window-option -g window-status-current-format "\
#[bg=colour0, fg=\#5e5faf]◢\
#[bg=\#5e5faf, fg=colour189]#I\
#[bg=colour189, fg=\#5e5faf]◤\
#[bg=colour189, fg=\#5e5faf, bold]#W\
#[bg=colour0, fg=colour189]◤"

# [win/cur/{tab}/----------/time]
set-window-option -g window-status-format "\
#[bg=colour0, fg=#5e5faf]◢\
#[bg=#5e5faf, fg=colour189]#I\
#[bg=\#4e4e4e, fg=#5e5faf]◤\
#[bg=\#4e4e4e, fg=colour189]#W\
#[bg=colour0, fg=\#4e4e4e]◤"

# [win/cur/tab/----------/{time}]
set-option -g status-right "\
#[bg=colour0, fg=\#5e5faf]◢\
#[bg=\#5e5faf, fg=colour189]%d %b %Y %H:%M "

# Window list color
set-window-option -g mode-style bg=#5e5faf,fg=colour189
```
