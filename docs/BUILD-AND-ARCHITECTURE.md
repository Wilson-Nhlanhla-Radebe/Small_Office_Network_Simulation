# Build and Architecture

## Design

Two internal office networks:

- 192.168.1.0/24
- 192.168.2.0/24

A centralized server at 192.168.1.2 provides DHCP and can provide DNS. LAN 2 DHCP requests are relayed by the Office Router Vlan1 interface to 192.168.1.2.

The Office Router connects to an ISP router over 10.0.0.0/30. The ISP connects to an upstream Internet Router over 10.0.0.4/30. The upstream router provides an external test LAN at 203.0.113.0/24.

## Traffic flows

### DHCP

LAN 2 workstation → Switch 2 → Vlan1 gateway → DHCP relay → 192.168.1.2 → LAN 2 DHCP pool

### Internal routing

192.168.2.0/24 → Office Router → 192.168.1.0/24

### External traffic

192.168.2.x → Office Router → PAT → 10.0.0.1 → ISP → upstream router → 203.0.113.10

### Return traffic

Upstream devices require routes back toward the office WAN. This lab explicitly verifies return routing instead of testing only the outbound direction.

## Troubleshooting methodology

1. Interface status
2. Gateway reachability
3. Internal LAN routing
4. WAN link reachability
5. Default routes
6. Return routes
7. External host reachability
8. NAT/PAT
9. DNS
