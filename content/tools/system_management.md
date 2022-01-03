+++
chapter = false
title = "System Management"
weight = 5
+++

This page is concerned with tools that help with management of a linux (ubuntu)
system from the command line.

## nmcli
- `nmcli dev wifi` to list available wifi
- `nmcli dev wifi connect SSID --ask`: connect to a new wifi 
- `nmcli con [up|down] SSID` manage stored connection

`nm-applet` for i3bar utility

## bluetoothctl
- `bluetoothctl` to enter interactive

in bluetooth, you pair once (exchange initial info) and then connect
(two distinct steps!)  
trusting a device means it will autoconnect to that device

## System control
- `pavucontrol`: graphical sound manager

## device listing
- `lsblk -p`: list all storage devices
- `lsblk -f`: list only mounted
- `lsusb`: todo
- `lspci`: todo

## xrandr
todo

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

There are different types of systemd units.

Some example commands:
- `systemctl list-units --type=service --state=active`
- `systemctl status nginx.service`
- [systemd unit types](https://opensource.com/article/20/5/systemd-units)
- [systemd unit files](https://www.digitalocean.com/community/tutorials/understanding-systemd-units-and-unit-files)

