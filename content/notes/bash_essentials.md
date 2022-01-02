---
title: "Bash Essentials"
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

## Utility
### grep
- `cat file | grep -v ^#`: no lines starting with `#`
- `cat file | grep -v ^$`: no empty lines

### tee
- read from standard in, copy to file and stdout

Store output of a command into outputfile and also continue processing:
`... | tee <outputfile> | grep <pattern>` 

## Connectivity
- `rfkill list` and `rfkill unblock 0`

### SSH
- forward port reachable from remote host:
`ssh -L localport:192.168.x.x:remoteport user@domain.tld`

### nmcli
- `nmcli dev wifi` to list available wifi
- `nmcli dev wifi connect SSID --ask`: connect to a new wifi 
- `nmcli con [up|down] SSID` manage stored connection

`nm-applet` for i3bar utility

### bluetoothctl
- `bluetoothctl` to enter interactive

in bluetooth, you pair once (exchange initial info) and then connect
(two distinct steps!)  
trusting a device means it will autoconnect to that device

## System control
- `pavucontrol`: graphical sound manager
- `lsblk -p`: list all storage devices
- `lsblk -f`: list only mounted

### Autostart
- cron `on reboot`
- `systemctl [enable|disable] postgres`: add/remove from autostart
works only if service is stopped

### Mounting a device
- `sudo mount /dev/sda ~/mountdir`
- `sudo umount [device|dir]`

### systemctl
- `systemctl list-dependencies <service>`
- `systemctl is-active <service>`

### DNS
- `dig <domainname>`
- `systemd-resolve --statistics` and `systemd-resolve --flush-cache`


## Security
- `sha256sum file`: compute checksum
- `sha256 -c sha256sumfile`: to check

### ufw
Unix firewall  
`gufw` for graphical version

### ip
[Resource](https://www.lartc.org/lartc.html)


