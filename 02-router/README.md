# Lab 02 — Router: Inter-Network Communication

## Objective

Build and configure a network consisting of two separate IPv4 subnets connected through a Cisco router.

The goal was to enable communication between devices in different networks and understand how a router forwards IP packets.

## Network Topology

**Devices:**
- 1 × Cisco 2911 Router
- 2 × Cisco 2960 Switches
- 2 × PC-PT

**Topology:**

```text
PC0
 |
Switch0
 |
Router0
 |
Switch1
 |
PC1
```

## IP Addressing

| Device | Interface | IP Address | Subnet Mask |
|---|---|---|---|
| PC0 | FastEthernet0 | 192.168.1.10 | 255.255.255.0 |
| Router0 | GigabitEthernet0/0 | 192.168.1.1 | 255.255.255.0 |
| Router0 | GigabitEthernet0/1 | 192.168.2.1 | 255.255.255.0 |
| PC1 | FastEthernet0 | 192.168.2.10 | 255.255.255.0 |

### Default Gateways

- PC0: `192.168.1.1`
- PC1: `192.168.2.1`

## Router Configuration

```text
enable
configure terminal

interface gigabitEthernet 0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit

interface gigabitEthernet 0/1
ip address 192.168.2.1 255.255.255.0
no shutdown
end
```

Configuration was saved to startup-config:

```text
copy running-config startup-config
```

## Verification

### Interface Status

Command:

```text
show ip interface brief
```

Both configured interfaces reached the `up/up` state.

### Routing Table

Command:

```text
show ip route
```

The router automatically learned two directly connected networks:

- `192.168.1.0/24` via GigabitEthernet0/0
- `192.168.2.0/24` via GigabitEthernet0/1

Local routes for the router's own interface addresses were also present.

### Connectivity Tests

**PC0 → PC1**

- Packets sent: 4
- Packets received: 3
- Packet loss: 25%

**PC1 → PC0**

- Packets sent: 4
- Packets received: 4
- Packet loss: 0%

The first ping included an initial timeout. Subsequent packets were successfully delivered.

## Key Concepts

- IPv4 addressing and subnet masks
- Router interfaces
- Default Gateway
- ARP resolution
- Ethernet frames and IP packets
- IP forwarding
- Routing table
- Directly connected routes
- Running-config and startup-config

## Result

Successfully configured a Cisco router to provide communication between two different IPv4 networks.

Verified connectivity, inspected the routing table, examined ARP resolution and saved the router configuration.

## Tools

- Cisco Packet Tracer
- Cisco IOS CLI
