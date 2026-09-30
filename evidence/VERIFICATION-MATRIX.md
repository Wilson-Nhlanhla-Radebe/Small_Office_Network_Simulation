# Verification Matrix

| Area | Result from lab build | Evidence |
|---|---|---|
| LAN 1 addressing | Verified | Router interface |
| LAN 2 addressing | Verified | Vlan1 + client |
| Central DHCP | Verified during build | DHCP client |
| DHCP relay | Verified | Vlan1 helper configuration |
| LAN-to-LAN routing | Verified | Ping tests |
| Office ↔ ISP WAN | Verified, 0% loss | Ping/interface |
| ISP ↔ upstream WAN | Verified | Ping/interface |
| Office default route | Verified | show ip route |
| ISP return routes | Verified | ISP show ip route |
| ISP default route | Verified | ISP show ip route |
| Upstream return route | Verified | Upstream show ip route |
| External PC gateway | Corrected and verified | External PC IP config |
| NAT inside/outside | Verified | Office Router config |
| PAT translation | Verified | show ip nat translations |
| LAN 2 → external test host | Verified after PAT | Ping + NAT table |
| DNS | Verified | DNS service + client test |
| Final .pkt | Saved and Verified | packet-tracer/ |
