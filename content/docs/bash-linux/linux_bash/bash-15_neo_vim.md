---
title: "Bash - 15 - Neovim"
description: ""
summary: ""
date: 2025-01-01T15:29:36+05:30
lastmod: 2025-01-01T15:29:36+05:30
draft: false
weight: 986
toc: true
seo:
  title: "" # custom title (optional)
  description: "" # custom description (recommended)
  canonical: "" # custom canonical URL (optional)
  noindex: false # false (default) or true
---

`HJKL` for moving around
`H--L` for left and right
`-JK-` for down and up

`:` will go to command line (in some mode)
`:q<Enter>`  for closing the window
`:qa!<Enter>` Get out of Vim (all changes are lost) exiting from all deeper layers at once. 

___
`:help`   is general help window

`Ctrl+]` (square brace) or `double mouse click` on any `tag` vim will jump to that subject similar to help page. (if there are no help pages for that particular word, does't go anywhere )

`Ctrl+O`  (its is not zero), or `Ctrl + right mouse click` or `Ctrl+T` to jump back to previous position. (repeat to go further back)

Help can anything specific can be given as argument to `:help` command.
`:help x` `:help i_<esc>` `:help :quit`

___
`:help quit`  or `:help word` and pressing `Ctrl+D` will bring up all matching help entries to see

`:Tutor` for a tutorial on basics

`:help quickref`  for the reference of command shortcuts


___


`:terminal` for a terminal session inside editor
___________
___________
No Caps Lock

`<Esc>+u`  To undo the last changes

`:index`  for all the `:` commands

Links are opened by moving on it and pressing enter.
Capital K which is `Shift+K` on any item will search for documentation ( `Ctrl+]` searches for tags of the word) 

Pressing `<Esc>` will put in Normal mode (or will cancel the partially typed command), which allows to retype a command.

`:q! <Enter>` quits the editor, Discarding any changes made.
____

#### Text Editing

`nvim filename` to start editing a file in vim.

`:wq` for writing a file and quitting `:q!` will not save.

***Deletion***
`x` deletes any character under the cursor. `delete` key does the same. (not in insert mode)

`dw` delete word erases the word the cursor is on, (for clearly deleting a word, the cursor should be on the first character of the word)

`d$` deletes from cursor till end of the line.


***Insertion***
Pressing `i` starts insert mode just before the cursor and typing can be done. `<Esc>` will bring to normal mode so movement and deletion can happen.


***Append***
`A` Capital A : To append after the line, which is `<shift>+A` pressed in any line will move to the End of that line and starts insert mode to type.

`a` is similar to `i`, it starts the insert / append after the cursor. `i` starts before the cursor.

(inserting / Insert mode commands for these letters)
`i I a A  gI  gi   o   O` need to be looked up.










