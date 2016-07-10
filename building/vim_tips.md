## Vim
### vimrc
```vim
execute pathogen#infect()
syntax on
filetype plugin indent on
set encoding=utf-8
set fileencoding=utf-8
let g:netrw_liststyle=3
set runtimepath^=~/.vim/bundle/ctrlp.vim
set path+=$PWD/**
```
### plugins
* The most important one is pathogen for plugin management.
* vim-rails: for rails project. Turn vim to an IDE.
* NerdTREE: for a tree structure like an IDE.

### useful built-in commands
* gf: go to a file based on current cursor position. bf: go back to earlier file. Ctrl-W gf: open in a tab.
* `:find`: find in current directory

### ctags
Use exuberant-tags to generate an index for the current project tree.
* `:ta method1`: use this in source code. goes to the definition of method1.
