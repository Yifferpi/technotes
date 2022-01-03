---
title: "Bash"
date: 2021-12-29T21:41:06+01:00
draft: false
---
# Command line essentials

## Commandline
- `>`: pipe into file, overwriting
- `>>`: append to a file
- `&>>`: append both `stdout` and `stderr`
- `&`: run program in child process (e.g `firefox &`)
- `|`: pipe to another application 
- `-`: ?

`source` executes commands from a file in the current shell.
can also be used to refresh environment variables, and that's what it's
mostly used for
[Resource](https://linuxhandbook.com/source-command/)



# Commands Overview

## Navigate the Command line
- [`ls`]()
- [`cd`]()
- [`cat`]()
- [`less` and `more`]()
- [`tree`]()

## Manipulate files
- [`touch`]()
- [`mv`]()
- [`cp`]()
- [`mkdir` and `rmdir`]()

## File permissions
- [`chmod`]()
- [`chown`]()

## Utility
- [`head`]()
- [`tail`]()
- [`cut`]()
- [`sort`]()
- [`tr`]()
- [`df` and `du`]()
- `tee`
    - read from standard in, copy to file and stdout
    - Store output of a command into outputfile and also continue processing:
    `... | tee <outputfile> | grep <pattern>` 
- [`awk`]()
- [`sed`]()
- `grep`
    - `cat file | grep -v ^#`: no lines starting with `#`
    - `cat file | grep -v ^$`: no empty lines

# Bash Script Examples
## Asking user for confirmation
```
while true; do
    # read is the most common way to ask for user input:
    read -p "Do you wish to install this program?" yn
    case $yn in
        [Yy]* ) echo "Installing..."; break;;
        [Nn]* ) exit;;
        * ) echo "Please answer yes or no.";;
    esac
done
```
## while loop
```
while true
do
    read -p "Really run script?" answer
    case $answer in
        [yY]* ) echo "Okay, running:"
                break;;
        [nN]* ) exit;;
        * )     echo "Dude, just enter Y or N please.";;
    esac
done
echo "Hello world"
```
