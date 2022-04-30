+++
chapter = false
title = "utility tools"
weight = 5
+++

<!-- Introduction: what is a firewall? -->
- `sha256sum file`: compute checksum                                                    
- `sha256 -c sha256sumfile`: to check

## Ghidra
reverse engineering tool with great decompiler

- start project, then open file in CodeBrowser
- accept analyzing

- Menu>Window gives a series of views, e.g. `Defined Strings`, `Function Graph`, and `Function Call Graph`

## GDB

- `br *main+12`: setting breakpoint
- `s`: stepping one instr
- `finish`: continue to return statement of current function
- `continue`: continue regular execution until next break

- `info frame 0`: print some info about frame 0
- `x/4w $sp` or `x/4w x7fffde60`: print 4 words starting at stack pointer or given address
- `x/s $rdi`: print value in rdi formated as a string
- `x/10i`, `x/xg`, `x/20xb`
- `set $buffer=0x7ffffffddd0`: set arbitrary variable, must not exist in HW 
- `ni`: show next instruction
- `vmmap`: show all memory regions mapped to our virtual memory
- gdb disables *Address Space Layout Randomization* (ASLR) by default.
- turn on with `aslr on` before `run`
- printing addresses with `print main`, subtracting labels allowed!
- `checksec`: display which security measures are active in the binary

- `info file` prints info about the file, e.g., entry point, symbols, etc.

- `info file` prints info about the file, e.g., entry point, symbols, etc.

