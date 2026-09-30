# Command Evidence

## Office Router

### Interfaces

Verified:

    Gi0/0/0   10.0.0.1      up/up
    Gi0/0/1   192.168.1.1   up/up
    Vlan1     192.168.2.1   up/up

### DHCP relay

    interface Vlan1
     ip address 192.168.2.1 255.255.255.0
     ip helper-address 192.168.1.2

### Routing

The routing table showed connected routes for 192.168.1.0/24, 192.168.2.0/24, and 10.0.0.0/30, plus a default route via 10.0.0.2.

### NAT

Gi0/0/1 and Vlan1 were configured as NAT inside. Gi0/0/0 was configured as NAT outside.

An observed translation included:

    Inside local  : 192.168.2.2
    Inside global : 10.0.0.1
    Outside       : 203.0.113.10

## ISP Router

Verified return routes for 192.168.1.0/24 and 192.168.2.0/24 via 10.0.0.1, plus a default route via 10.0.0.6.

## Internet Router

Verified a return route for 10.0.0.0/30 via 10.0.0.5 and a connected 203.0.113.0/24 network.

## Client verification

A LAN 2 client successfully obtained a 192.168.2.x address with mask 255.255.255.0 and gateway 192.168.2.1.

## Connectivity

Verified during the build: LAN 2 → LAN 1 hosts; Office Router ↔ ISP Router; ISP Router ↔ Internet Router; Internet Router → 203.0.113.10; Office Router → 203.0.113.10; and LAN 2 client → 203.0.113.10 after PAT.

## DNS status

DNS was tested separately from raw IP connectivity. The final configuration includes a DNS record for example.com mapped to 203.0.113.10 and distributes 192.168.1.2 as the DNS server through DHCP.
