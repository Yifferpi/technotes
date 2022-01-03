+++
chapter = false
title = "VPN"
weight = 5
+++

## Wireguard
Install with `apt install wireguard`

After installation:
```
sudo su
cd /etc/wireguard
umask 077
```
to protect wireguard directory appropriately

Command to generate key pair for server:
`wg genkey | tee server_private_key | wg pubkey > server_public_key`
Repeat for each peer

Create a `wg0.conf` file in `/etc/wireguard` on the server side:

```
[Interface]
Address = 10.253.3.1/24
SaveConfig = true
PrivateKey = <insert server_private_key>
ListenPort = 51900

PostUp = iptables -A FORWARD -i %i -j ACCEPT; iptables -A FORWARD -o %i -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
PostDown = iptables -D FORWARD -i %i -j ACCEPT; iptables -D FORWARD -o %i -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE

[Peer]
PublicKey = <insert client_public_key>
AllowedIPs = 10.253.3.2/32
```
- replace `server_private_key` and `client_public_key`
- possibly change `eth0` to `wlan0`
- don't forget to forward `ListenPort` on the router
### Enable port forwarding on vpn server
In `/etc/sysctl.conf`, change/uncomment `net.ipv4.ip_forward` to `1`
this allows the vpn server to act as a router

### Start up Wireguard
```
systemctl enable wg-quick@wg0
chown -R root:root /etc/wireguard/
chmod -R og-rwx /etc/wireguard/*
```

- `systemctl enable` adds `wg-quick@wg0` to autostart
- the others again limit access to wireguard config directory
- then restart to get wireguard going on the vpn server

### Set up client
Create a `wg0.conf` file in `/etc/wireguard` on the client side:
```
[Interface]
Address = 10.253.3.2/32
PrivateKey = <insert client_private_key>
DNS = 1.1.1.1

[Peer]
PublicKey = <insert server_public_key>
Endpoint = <insert vpn_server_address>:51900
AllowedIPs = 0.0.0.0/0, ::/0
```
- `AllowedIPs = 0.0.0.0` means that only the client is accessible/visible
through the vpn tunnel
- `Address` must be from the address range specified in the server config
under `[Peer] AllowedIPs`
- to bring it up, type `sudo wg-quick up wg0`
- to check if it works: `sudo wg`

### Note
- `AllowedIPs` on client side is like access control: only listed IPs are
allowed incoming, rest is dropped
- on server: `AllowedIPs` is like routing: tells packets where to go

### Resources
[more involved tutorial!
](https://www.ckn.io/blog/2017/11/14/wireguard-vpn-typical-setup/)
[Simple Home Setup
](https://engineerworkshop.com/blog/how-to-set-up-wireguard-on-a-raspberry-pi/)
[Details on allowing certain ip ranges
](https://www.flockport.com/guides/build-wireguard-networks)
