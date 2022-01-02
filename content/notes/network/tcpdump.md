---
title: "Tcpdump Essentials"
date: 2021-12-28T10:06:13+01:00
draft: false
---


# Usage
- `tcpdump -i <interface>`
- three steps of verbosity: `-v -vv -vvv`
- finding ssh connections independent of port used:
`tcpdump 'tcp[(tcp[12]>>2):4] = 0x5353482D'`

# Resources
[A tcpdump Tutorial with Examples](https://danielmiessler.com/study/tcpdump/)

