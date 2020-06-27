---
layout: post
comments: true
title: How to move cursor to the last edited location in Vim
---

For moving or jumping cursor to the last edited locations in [Vim](https://en.wikipedia.org/wiki/Vim_(text_editor)) use `g,` and `g;` commands in normal mode.

`g,` moves cursor forward or to the newer positions in change list, `g;` moves the cursor to the older location or positions in the changelist.

Both of these operations can accept `count` as an optional argument, which will take cursor to the `n`-th position in the change list.

To know more about `changelist` use `:help changelist`.

