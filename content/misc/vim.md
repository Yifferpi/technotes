+++
chapter = false
title = "Vim"
weight = 5
+++

#delete a word
small w only considers letters
big W also considers brackets
c cuts and goes into insert mode afterwards
d only cuts

caw, daw	cut word including space after it
ciw, diw	cut word without space

ctrl-v		enter Visual block mode
shift-I		go insert mode, change entire block

Command `:>>` and `:<`: shift two indents to the right / one to the left

## Macros
- **Recording:** press `q` followed by key you want to store the makro in, then do
your thing, in the end, press `q` in normal mode again.  
- to execute a macro, press `@` followed by the key the macro is stored in

*how to execute a macro multiple times?*
*how to look at the macro registry*

