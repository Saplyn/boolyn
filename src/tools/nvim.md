# NeoVim

[NeoVim](https://neovim.io/) is a modernized version of Vim. It's a fork of
Vim, with the goal of improving the codebase and adding new features.

## Cheatsheet

- substitute:
  - `:s/old/new/`: substitute the **first** occurrence of `old` with `new` in the **current line**.
  - `:s/old/new/g`: substitute **all** occurrences of `old` with `new` in the **current line**.
  - `:#,#s/old/new/g`: substitute **all** occurrences of `old` with `new` in the **range** of lines.
  - `:%s/old/new/g`: substitute **all** occurrences of `old` with `new` in the **entire file**.

## Plugins

- [lazy.nvim](https://github.com/folke/lazy.nvim): A modern plugin manager for Neovim.
- [telescope.nvim](https://github.com/nvim-telescope/telescope.nvim): A highly extendable fuzzy finder.
- [neo-tree.nvim](https://github.com/nvim-neo-tree/neo-tree.nvim/): Easily manage the file system and other tree like structures.
- [trouble.nvim](https://github.com/folke/trouble.nvim): A pretty list for showing diagnostics, references, telescope results, quickfix and location lists.
- [undotree.vim](https://github.com/mbbill/undotree): The undo history visualizer for Vim.
- [todo-comments.nvim](https://github.com/folke/todo-comments.nvim): Highlight, list and search todo comments in your projects.

## Resources

- [dotfyle](https://dotfyle.com/): Discover and share Neovim plugins.
- [kickstart.nvim](https://github.com/nvim-lua/kickstart.nvim): A launch point for your personal nvim configuration
- [LazyVim](https://github.com/LazyVim/LazyVim): A flexible, battery included Neovim distribution.
