Network Configuration
=====================

ip addr
ip link set enp2s0 up
ip link show dev enp2s0


ip link set enp2s0 up
ip addr add 192.168.1.2/24 broadcast 192.168.1.255 dev enp2s0
ip route add default via 192.168.1.1
