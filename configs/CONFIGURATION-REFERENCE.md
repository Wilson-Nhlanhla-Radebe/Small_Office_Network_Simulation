# Configuration Reference

## Office Router

### LAN 1

    interface GigabitEthernet0/0/1
     ip address 192.168.1.1 255.255.255.0
     ip nat inside

### LAN 2 / SVI

    interface Vlan1
     ip address 192.168.2.1 255.255.255.0
     ip helper-address 192.168.1.2
     ip nat inside

### WAN

    interface GigabitEthernet0/0/0
     ip address 10.0.0.1 255.255.255.252
     ip nat outside

### Default route

    ip route 0.0.0.0 0.0.0.0 10.0.0.2

### NAT ACLs

    access-list 2 permit 192.168.1.0 0.0.0.255
    access-list 3 permit 192.168.2.0 0.0.0.255

### PAT

    ip nat inside source list 2 interface GigabitEthernet0/0/0 overload
    ip nat inside source list 3 interface GigabitEthernet0/0/0 overload

## ISP Router

Office-facing: 10.0.0.2/30
Upstream-facing: 10.0.0.5/30

Return routes:

    ip route 192.168.1.0 255.255.255.0 10.0.0.1
    ip route 192.168.2.0 255.255.255.0 10.0.0.1

Default route:

    ip route 0.0.0.0 0.0.0.0 10.0.0.6

## Internet Router

ISP-facing: 10.0.0.6/30
External LAN: 203.0.113.1/24

Return route:

    ip route 10.0.0.0 255.255.255.252 10.0.0.5

## External PC

IP: 203.0.113.10
Mask: 255.255.255.0
Gateway: 203.0.113.1
