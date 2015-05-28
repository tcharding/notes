== Raspberry Pi Torrent Box ===

=== overview ===
* config hardware
* install raspbian
* config external hard disk
* add user/config root + user accounts
* iptables 

=== samba ===
iptables
* -A INPUT -s 10.0.0.0/24 -p udp --dport 137 -j ACCEPT
* -A INPUT -s 10.0.0.0/24 -p udp --dport 138 -j ACCEPT
* -A INPUT -s 10.0.0.0/24 -p tcp --dport 139 -j ACCEPT
* -A INPUT -s 10.0.0.0/24 -p tcp --dport 445 -j ACCEPT

* # apt-get install samba samba-common-bin
backup config file
* # cp /etc/samba/smb.conf /etc/samba/smb.conf.old
* # vim /etc/samba/smb.conf

=== openvpn ===
set up Raspberry Pi as OpenVPN router
iptables
* ssh
* http[s]

if you want routing capabilities config packet forwarding
* # vim /etc/sysctl.conf
net.ipv4.ip_forward=1

install openvpn
* # apt-get install openvpn

set up vpn service 
I used: ProXPN
config details: http://ericdoerr.com/guides/setup-raspberry-pi-as-an-openvpn-router.html

run openvpn, and detach process (Contral-A-D)

install deluge (bittorrent client)
* # apt-get install deluge deluge-console

start it and stop it
* # deluged
* # pkill deluged
 
edit config
* # vim /root/.config/deluge/auth
user:password:level
> media:fam:10

run deamon
* # deluged
run console 
* # deluge-console
enter in console 
config -s allow_remote True

and check it worked (still in console)
config allow_remote
exit

kill and restart daemon
* # pkill deluged
* # deluged
