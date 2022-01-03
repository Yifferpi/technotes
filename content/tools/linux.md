---
title: "Linux Essentials"
date: 2021-12-28T10:06:13+01:00
draft: false
---

## directory structure

contains all sorts of configuration files
- `/etc/passwd`: userlist
- `/etc/shadow`: userlist including password hashes
- `/etc/group`: groups and list of users that belong to it
- `/etc/environment`: global environment variables
- `/etc/hosts`: static lookup table for hostnames, superseded by DNS
- `/etc/hostname`: static hostname used to init kernel hostname
- `/etc/machine-info`: contains info like location, chassis, prettyname, etc.
not present on every machine

- `/etc/apt`: config of apt
- `/etc/apt/sources.list`: file with apt repository sources
- `/etc/apt/sources.list.d`: directory for more sources

- `/etc/systemd/multi-user.target.wants`: autostart services

- `/etc/NetworkManager/system-connectons`: wifi connections, SSIDs


Variable content that is changed by programs. Prominently:

- `/var/log`: place where many logfiles are

## Interprocess Communication (IPC)
- Good [Resource](https://opensource.com/sites/default/files/gated-content/inter-process_communication_in_linux.pdf)
- [sockets AF_NET, etch](https://stackoverflow.com/questions/51008595/what-is-the-purpose-of-sock-dgram-and-sock-stream-in-the-context-af-unix-sockets)

## General
[tty, etc](https://dev.to/napicella/linux-terminals-tty-pty-and-shell-192e)
