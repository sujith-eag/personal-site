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



***Command mode*** : keystrokes act as commands
***Insert and Replace mode*** for editing. (`<Esc>` to exit to Command mode)

Insert mode inserts any characters at cursor position.
Replace mode the characters entered replaces the character at the cursor position.

___

Five categories of keystrokes:
* Mode commands
* Cursor movement commands
* Editing commands
* File commands
* Miscellany

___

#### Mode commands : 
`<Esc>`  to move out of insert / replace mode.
`I, i, A, a, O, o` to move into insert mode at a particular place.
`I` at beginning of line `i` at current cursor position
`a` immediately after the cursor position, `A` at the end of the line
`O` in a blank line immediately above the cursor  `o` immediately below the cursor.
`R, r` to enter replace mode and staying there or replacing one character and moving out after that to command mode.

___

#### Cursor Movement Commands:
`HJKL` for moving around
`H--L` for left and right
`-JK-` for down and up

`0` just zero to move to left end (beginning) of the line in command mode.
`$` (shift+4) to move to end of line in command mode.
`w, b` to move forward or backwards to the next/previous word or punctuation mark.
	`3w` to move 3 word
`W, B` moves one word
`E, e` similar but takes to end of current word or to next punctuation mark.

`G` moves to the end of the file. `nG` can be given to move to a particular line. `6G`

Page Motion
`Ctrl + b` and `Ctrl + d` to move up and down by half page.
`Ctrl + u` and `Ctrl + f` to move up down by one full screen.

`H, M, L` Head, Middle, Last moves to these points in the file.

___

#### Editing Commands

Which allows for cut copy an paste.

There are various forms of Cut (deletion) commands
`x` deletes the current character
`D` deletes from cursor to end of the line.
`dd` deletes the current line (`5dd` to delete multiple lines below it)
`dw` to delete current word or from cursor till next word (`d5w` to delete 5 words)
`db` deletes the previous word or to the left of cursor till end of word.
`d` ??

Deleted items are moved into buffer, can be recalled or pasted anywhere.
`p` to paste before the cursor
`P` to paste after the cursor

`yy` to copy the current line and `yw` to copy the current word to buffer.
`6yy` copies the 6 lines from cursor.

Buffer space: adding any letter from a to z to command allows to select 26 additional buffers.
`a6yy` copies 6 lines from the cursor into buffer `a`, then typing `ap` will paste those 6 lines after the cursor.

`J` to join two consecutive lines into one,
`xp` transposes the current character with next character (cut paste)

`u` undoes the last changes made
`U` undoes all changes made to the current line.
`Ctrl + r` to redo the last command

___

#### File Commands
File commands start with `:`
`:` will go to command line (when in Command mode)
`:w` to save the file
`:w filename` to save as (change file name)
`:r filename` to open a new file.
`:q` for closing a window
`:wq` to save and exit
`:q!` to discard changes and exit
`:qa!` Get out of Vim (all changes are lost) exiting from all deeper layers at once. 

___

#### Miscellany

`/string` or `?string` to search for a string

`%` to match the current section closing braces

`v` to start selection(visual) and moving any direction. (`gU` to Uppercase everything selected)

Search and replace a string using `%s`
`:%s/,/.`

____
____


`:help`   is general help window
Help can anything specific can be given as argument to `:help` command.
`:help x`,  `:help i_<esc>`, `:help :quit`

`Ctrl+]` (square brace) or `double mouse click` on any `tag` vim will jump to that subject similar to help page. (if there are no help pages for that particular word, does't go anywhere )

`Ctrl+O`  (its not zero), or `Ctrl + right mouse click` or `Ctrl+T` to jump back to previous position. (repeat to go further back)


___

`:help quit`  or `:help word` and pressing `Ctrl+D` will bring up all matching help entries to see

`:Tutor` for a tutorial on basics

`:help quickref`  for the reference of command shortcuts

`:terminal` for a terminal session inside editor

___________
___________


No Caps Lock

`<Esc>+u`  To undo the last changes

`:index`  for all the `:` commands

Links are opened by moving on it and pressing enter.
Capital K which is `Shift+K` on any item will search for documentation ( `Ctrl+]` searches for tags of the word) 

Pressing `<Esc>` will put in Command mode (or will cancel the partially typed command), which allows to retype a command.

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
Pressing `i` starts insert mode, with insert starting just before the cursor.

`I`, Capital `I` : starts insert from the beginning of the line the cursor is on currently.

`<Esc>` will bring to Command mode so movement and deletion can happen.


***Append***
`A` Capital A : To append after the line, which is `<shift>+A` pressed in any line will move to the End of that line and starts insert mode.

`a` is similar to `i`, it starts the insert / append after the cursor. `i` starts before the cursor.

(inserting / Insert mode commands for these letters) `i, I, a, A, gI, gi, o, O` 

`gI, gi, o, O` need to be looked up.



