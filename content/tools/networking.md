+++
chapter = false
title = "Networking tools"
weight = 5
+++

## tcpdump
### Usage
- `tcpdump -i <interface>`
- three steps of verbosity: `-v -vv -vvv`
- finding ssh connections independent of port used:
`tcpdump 'tcp[(tcp[12]>>2):4] = 0x5353482D'`

### Resources
[A tcpdump Tutorial with Examples](https://danielmiessler.com/study/tcpdump/)


## Wireshark
Wireshark is the GUI application and Tshark the command line version.
Wireshard makes packets more readible but the filtering system is essentially the same.


## nmap
### Host discovery
Ping Scan: 
`nmap -sP 192.168.1.0/24`
- in newer versions, this is called `-sn`
- can be prettified with `-oG -` (greppable output)


List Scan:
`nmap -sL 192.168.1.0/24`
`nmap -sP -PN -R --system-dns 192.168.2.0/24 | grep -i .wg`


`-R`: DNS resolution for all targets, not only responsive hosts
- `-sP`: see `-sn`
- `-Pn`: (No ping), skips discovery stage alltogether, `-PN` in older versions

`nmap -sP -sn -oG - 192.168.2.0/24`
- `-sn`: Ping Scan - disable port scan, `-sP` in older versions
- [nmap scripting engine](https://nmap.org/book/man-nse.html)
- [nmap commands](https://securitytrails.com/blog/nmap-commands)
- [nmap overview](https://showmehacker.medium.com/nmap-perform-information-gathering-beginners-detailed-explanation-c37e51a85fbf)

## netcat
todo

## netdiscover
todo

## ip
[Resource](https://www.lartc.org/lartc.html) 

## DNS
- `dig <domainname>`
- `systemd-resolve --statistics` and `systemd-resolve --flush-cache`
