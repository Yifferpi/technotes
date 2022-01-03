+++
chapter = false
title = "Firewall"
weight = 5
+++

<!-- Introduction: what is a firewall? -->

## iptables
- [General concepts](https://www.thegeekstuff.com/2011/01/iptables-fundamentals/)

## nftables

[a good resource](https://wiki.archlinux.org/title/Nftables)

- `nft --handle list ruleset`: lists rules including handles
- `nft insert rule inet filter input ip saddr grader.dtf.netsec.inf.ethz.ch accept`
- `nft delete rule inet filter input handle 17`
- `nft add rule inet filter input tcp dport 5432 drop`

## ufw
Unix firewall  
`gufw` for graphical version
