# Tmux

[Tmux](https://github.com/tmux/tmux) is a terminal multiplexer, enabling a
number of terminals to be created, accessed, and controlled from a single
screen.

## Command Cheatsheet

- `tmux`: Creates a unnamed session
  - `tmux new -s <id>`: Create a named session
- `tmux a`: Attach to most recent session
  - `tmux a -t <id>`: Attach to specified session
- `tmux ls`: List all sessions
- `tmux kill-session <id>`: Kill specified session

## Keybind Cheatsheet

> <kbd>Ctrl</kbd> + <kbd>b</kbd>: Prefix key.

- Session Management
  - <kbd>d</kbd>: **D**etach
- Pane
  - <kbd>%</kbd>: Split horizontal
  - <kbd>"</kbd>: Split vertical
  - *direction arrow*: Switch pane
  - <kbd>q</kbd>: **Q**uick jump to pane
  - <kbd>Ctrl</kbd> + *direction arrow*: Resize
  - <kbd>Alt</kbd> + *direction arrow*: Aggressive Resize
  - <kbd>Alt</kbd> + *number*: Apply layout
  - <kbd>x</kbd>: Kill pane
  - <kbd>,</kbd>: Rename pane
- Window
  - <kbd>c</kbd>: **C**reate new window
  - <kbd>w</kbd>: **W**indow List
  - <kbd>n</kbd>: **N**ext window
  - <kbd>&</kbd>: Kill window
  - <kbd>$</kbd>: Rename window
- Copy mode
  - <kbd>[</kbd>: Enter copy mode
  - (copy mode) *space*: starts copy
  - (copy mode) *enter*: ends copy

## Resources

- [Tmux](https://github.com/tmux/tmux)
- [Tmux Cheatsheet](https://tmuxcheatsheet.com/)
