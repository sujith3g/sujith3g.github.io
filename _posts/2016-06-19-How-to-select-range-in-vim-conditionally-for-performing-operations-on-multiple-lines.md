---
layout: post
comments: true
title: How to select a range conditionally in vim
---

I use `norm` command along with visual selection to perform normal-mode operations on several lines in one go.

Now how to do the range selection based on a condition without switching to Visual selection mode ?

For example, if we want to append a comma(`,`) to each line till the next blank line.
Let's do this without a visual selection, `:.,/^$/-1 norm A,` this command will do the above task in one-go.

### Command explanation

*  `:`  :  the starting of command-mode.
*  `.`  :  the first part of the range selection, were `.` indicates the current line in range selection
*  `,` :  is the separator used between start and end of the range.
*  `/^$/` :  is the pattern for blank line, were `^` is the start and `$` end of line.
*  `-1`  :  `-1` indicates the line before, when it si combined with pattern the line before blank line.
*  `norm A,` :  performs normal mode operation `A,` which will append a `,` to the end of line.

Now you can use any patterns specified in [Ranges doc](http://vim.wikia.com/wiki/Ranges) to select/specify the Range, this blank line pattern is just an example.

This conditional range selection is very useful while recording macro spanning over multiple lines.

Read more about [Ranges](http://vim.wikia.com/wiki/Ranges).

