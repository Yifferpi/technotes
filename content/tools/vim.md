+++
chapter = false
title = "Vim"
weight = 5
tags=["editor"]
+++

On this page, a jumble of Vim shortcuts and functions are collected
that I find very useful.

## Delete text

Some examples:
- `ciw`: cut word (without following space), then go into insert mode
- `daw`: cut word including following space
- `dd`: delete entire line, remain in normal mode

`c` goes into insert mode after deleting whereas `d` only cuts

small w only considers letters
big W also considers brackets


- `ctrl-v` to enter Visual block mode
- `shift-I` to go insert mode, change entire block

Command `:>>` and `:<`: shift two indents to the right / one to the left

## Macros
- **Recording:** press `q` followed by key you want to store the makro in, then do
your thing, in the end, press `q` in normal mode again.  
- to execute a macro, press `@` followed by the key the macro is stored in

*how to execute a macro multiple times?*
*how to look at the macro registry*

