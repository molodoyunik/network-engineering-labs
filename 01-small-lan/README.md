# Lab 01 — Building a Small LAN
## Objective
Build a small local network using Cisco Packet Tracer and verify connectivity between hosts.
## Topology
- 3 PCs
- 1 Cisco 2960 switch
- Ethernet connections
## IP Addressing
- PC0 — 10.10.10.1 / 255.255.255.0
- PC1 — 10.10.10.2 / 255.255.255.0
- PC2 — 10.10.10.3 / 255.255.255.0
All three hosts belong to the same IP network.
## Tasks
1. Created a network topology with three PCs and one switch.
2. Configured IP addresses and subnet masks on all PCs.
3. Verified connectivity using ping.
## Verification
PC0 successfully reached PC1 and PC2 using ICMP Echo Request/Reply.
Packet loss: 0%.
## Independent Task — Packet Flow Analysis
Used Packet Tracer Simulation Mode to inspect the traffic generated during the first ping.
Observed that ARP messages appear before the ICMP packets when the destination MAC address is not yet known.
## Conclusion
The three PCs can communicate through the switch because they belong to the same IP network.
The lab also demonstrated the relationship between ARP and ICMP during initial communication.
