# EIGRP Routing

This lab demonstrates dynamic routing using EIGRP in Cisco Packet Tracer.

## Topology

The network consists of four routers connected using serial links.

## Configuration

EIGRP was configured using Autonomous System 10.

Each router advertises its directly connected networks so that routes can be dynamically learned from neighboring routers.

## Verification

The configuration was verified using:

- `show ip protocols`
- `show ip eigrp neighbors`
- `show ip route`
- `show ip route eigrp`
- `show running-config | section router eigrp`

EIGRP neighbor relationships were successfully established and remote networks appeared in the routing table as EIGRP learned routes (`D`).

## Files

- `EIGRP routing.pkt` - Cisco Packet Tracer lab file
- Screenshots - EIGRP configuration and verification