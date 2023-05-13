---
title: "Environment setup"
date: 2023-05-13T13:33:16+01:00
draft: false
---

# Environment configuration when setting up a new device

## ZSH 

Install `zsh` using your system package manager.
Then setup `ohmyzsh` by running the following command:

 `sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"`

## Starship prompt

To replace the prompt with [starship](https://starship.rs/), first install a Nerdfont, such as [this](https://github.com/ryanoasis/nerd-fonts/releases/download/v3.0.0/Hack.zip).

Then install starship with: `curl -sS https://starship.rs/install.sh | sh`



## Tmux config (taken from [1])

Copy the below text into your `~/.tmux.conf` file (or create an empty file if it doesn't already exist)
```bash

# remap prefix from 'C-b' to 'C-a'
unbind C-b
set-option -g prefix C-a
bind-key C-a send-prefix

# split panes using | and -
bind | split-window -h
bind - split-window -v
unbind '"'
unbind %

bind r source-file ~/.tmux.conf

# switch panes using Alt-arrow without prefix
bind -n M-Left select-pane -L
bind -n M-Right select-pane -R
bind -n M-Up select-pane -U
bind -n M-Down select-pane -D

# Enable mouse mode (tmux 2.1 and above)
set -g mouse on

######################
### DESIGN CHANGES ###
######################

# loud or quiet?
set -g visual-activity off
set -g visual-bell off
set -g visual-silence off
setw -g monitor-activity off
set -g bell-action none

#  modes
setw -g clock-mode-colour colour5
setw -g mode-style 'fg=colour1 bg=colour18 bold'

# panes
set -g pane-border-style 'fg=colour19 bg=colour0'
set -g pane-active-border-style 'bg=colour0 fg=colour9'

# statusbar
set -g status-position bottom
set -g status-justify left
set -g status-style 'bg=colour18 fg=colour137 dim'
set -g status-left ''
set -g status-right '#[fg=colour233,bg=colour19] %d/%m #[fg=colour233,bg=colour8] %H:%M:%S '
set -g status-right-length 50
set -g status-left-length 20

setw -g window-status-current-style 'fg=colour1 bg=colour19 bold'
setw -g window-status-current-format ' #I#[fg=colour249]:#[fg=colour255]#W#[fg=colour249]#F '

setw -g window-status-style 'fg=colour9 bg=colour18'
setw -g window-status-format ' #I#[fg=colour237]:#[fg=colour250]#W#[fg=colour244]#F '

setw -g window-status-bell-style 'fg=colour255 bg=colour1 bold'

# messages
set -g message-style 'fg=colour232 bg=colour16 bold'
```



[1] https://www.hamvocke.com/blog/a-guide-to-customizing-your-tmux-conf/

## Fuzzy Searching (fzf)

fzf is a fuzzy search utility for the command line.

Install by running:


 ```bash
 git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
 ~/.fzf/install
 ```

