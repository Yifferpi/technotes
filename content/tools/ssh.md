+++
chapter = false
title = "ssh"
weight = 5
+++
# Secure SHell

## SSH
- forward port reachable from remote host:
`ssh -L localport:192.168.x.x:remoteport user@domain.tld`
- `-p` flag to use a different port
- backticks to execute a command remotely!

`ssh-copy-id user@host` to copy own public key to host
## SSHD
config file location: `/etc/ssh/sshd_config`

- set `PubkeyAuthentification` to `yes` for auth via public key
- set `PasswordAuthentication` to `no` to only allow public key
- `systemctl restart sshd.service` for changes to take effect

*all of the above requires sudo*

[Reverse SSH tunnel](https://www.rustimation.eu/index.php/reverse-ssh-tunnel-schritt-fur-schritt/)
`ssh -p2000 -fNC -R 10011:localhost:22 pi@dyn.IP.adresse` for reverse

`ssh -p 10011 localhost` on gateway

Problems with cronjob at reboot.. here a solution:
[](https://github.com/axthosarouris/reverse-ssh-tunnel)


- `ssh-agent bash` to create a new agent
- `ssh-add ~/.ssh/id-rsa` to add key and enter password  
the above is valuable for cases like ansible, where otherwise
the password would need entering many times

- `ssh -J host1 host2` to do a proxyjump. It is just like ssh into 
host1, then from there into host2. Not sure wheteher host1 or your
own permissions count.
- this can also be achieved with the keyword `ProxyJump` in the config file

[ssh with command exec](https://blog.jbowen.dev/tips/ssh-tmux/)

## scp
todo
