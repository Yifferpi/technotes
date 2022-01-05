+++
chapter = false
title = "Bash"
weight = 5
+++

- [Bash Essentials](#command-line-essentials)
    - [special symbols](#special-symbols)
    - [hotkeys](#hotkeys)
    - [source vs. sh](#source-versus-sh)
    - [foreground and background jobs](#foreground-and-background-jobs)
- [Bash Script Examples](#bash-script-examples)


# Command line essentials

The following paragraphs explain shell tricks and concepts that are very helpful
in everyday use. They are mostly not commands.

## special symbols
- `>`: pipe into file, overwriting
- `>>`: append to a file
- `&>>`: append both `stdout` and `stderr`
- `&`: run program in child process (e.g `firefox &`)
- `|`: pipe to another application 
- `-`: ?

## hotkeys
- `Ctrl-l`: clear the terminal (same as typing `clear`)
- `Ctrl-a`: Go to beginning of line
- `Ctrl-e`: Move cursor to end of line
- `Ctrl-r`: Reverse command search, find a command in recent history
- `Ctrl-c`: Terminate the current process
- `Ctrl-d`: End of file (EOF), on empty line, this closes the shell
- `Ctrl-w`: delete part of the word before the cursor 
(e.g. `hello wor|ld` becomes `hello ld`)
- `Ctrl-u`: delete part of the line before the cursor
(e.g. `hello w|orld` becomes `orld`)

## source versus sh
`source` (or `.`) executes a script in the current shell. It is commonly used to 
reread configuration files (e.g. `. ~/.bash_rc`)

In contrast, `bash <script>` (or `./script`) spawns a new child process in which 
the script is executed.

[Resource](https://linuxhandbook.com/source-command/)

## foreground and background jobs
Most programs you start from a shell take over that shell. After the program is
launched, all commands you type in the window go to the program rather than the
underlying shell. 
- Launching a program with `&` appended (e.g. `firefox &`) starts
the program in the background.
- Pressing `Ctrl-z` when the program is in foreground (i.e. occupying the shell)
moves the program to the background and suspends it.
- Typing `bg` resumes the program in the background.
- Typing `fg` brings the program to the foreground again.

You can also have multiple programs run in the background.
- Current programs spawned from this shell can be listed with `jobs`.
- The first column of the listed jobs contains the job IDs.
- You can bring a specific program to foreground with `fg <job_id>`

## todo
- stdin stdout and stderr
- special directories `.` and `..`
- important environment variables
- config file
- concept of $PATH

## Commands Overview

- [`ls`]()
- [`cd`]()
- [`cat`]()
- [`less` and `more`]()
- [`tree`]()
- [`touch`]()
- [`mv`]()
- [`cp`]()
- [`mkdir` and `rmdir`]()
- [`chmod`]()
- [`chown`]()
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


# Bash script examples
In the following paragraphs, some common and frequently used bash script 
patterns are collected.

## Asking user for confirmation
```bash
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
```bash
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
## find script directory
```bash
DIR=$(dirname "$0")
cd "$DIR"
```

