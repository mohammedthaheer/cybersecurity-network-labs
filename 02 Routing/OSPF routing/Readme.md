# Multi-Area OSPF Lab

## Overview

This lab was created to practice multi-area OSPF routing in Cisco Packet Tracer.

The network uses three OSPF areas, with Area 0 acting as the backbone and two routers connecting Area 0 to Area 1 and Area 2.

## Topology

![OSPF Topology](topology.png)

## OSPF Areas

- Area 0 - Backbone network
- Area 1 - 192.168.10.0/24 network
- Area 2 - 192.168.20.0/24 network

The routers between Area 0 and the other areas act as Area Border Routers (ABRs).

## Configuration

OSPF process 7 was used throughout the lab.

Example configuration for the Area 0 / Area 1 ABR:

```text
router ospf 7
 network 172.16.0.0 0.0.255.255 area 0
 network 192.168.10.0 0.0.0.255 area 1
```

The other ABR connects Area 0 and Area 2:

```text
router ospf 7
 network 172.16.0.0 0.0.255.255 area 0
 network 192.168.20.0 0.0.0.255 area 2
```

## Verification

I used the following commands to verify OSPF:

```text
show ip protocols
show ip ospf neighbor
show ip route
```

The routers formed FULL OSPF neighbor adjacencies and routes from other areas appeared in the routing table as `O IA`.

For example, the Area 1 router learned networks from Area 2 through OSPF:

```text
O IA 5.0.0.1/32
O IA 192.168.20.0/24
```

The Area 2 router also learned the Area 1 networks:

```text
O IA 4.0.0.1/32
O IA 192.168.10.0/24
```

## What I Learned

This lab helped me understand how multi-area OSPF works and why Area 0 is used as the backbone.

I also practiced configuring ABRs, forming OSPF neighbor adjacencies, and checking the difference between intra-area (`O`) and inter-area (`O IA`) routes.

## Lab File

[`OSPF routing.pkt`](OSPF%20routing.pkt)