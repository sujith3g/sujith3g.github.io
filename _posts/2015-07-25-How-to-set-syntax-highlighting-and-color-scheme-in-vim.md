---
layout: post
comments: true
title: How to set syntax highlighting and color scheme in vim
---

Whenever a git merge occurs in any of my repo, Vim opens up for editing commit message. 
Initially even getting out of Vim was very difficult for me. I was about to change my default editor in git configs.
Then I thought of learning how to use Vim, because it will be very useful, when editing files in remote-server using ssh.
Yesterday I learned How to set the syntax highlighting and color scheme in Vim.

For enabling syntax highlighting and line numbers, add the following lines to the `~/.vimrc` file, create it if not present.

~~~
syntax on
set nu
~~~

Now for adding color scheme, you have to download any of the color schemes like [distinguished](https://github.com/Lokaltog/vim-distinguished) for Vim.
Now extract it and move `*.vim` files in `colors` directory to `~/.vim/colors/`.

~~~sh
  $ mv ~/Downloads/vim-distinguished/colors/*.vim ~/.vim/colors/
~~~

Now add the following line to the `~/.vimrc` file

~~~
colorscheme distinguished
~~~
I assume that `syntax on` is already there in it.
