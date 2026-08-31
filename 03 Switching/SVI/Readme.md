# SVI Inter-VLAN Routing Lab

## Overview

Configured inter-VLAN routing using **Switch Virtual Interfaces (SVIs)** on a Cisco multilayer switch in Packet Tracer.

Two VLANs were created and the 3560 switch was configured to perform Layer 3 routing between them.

## Topology

![SVI Lab Topology](topology.png)

## VLAN Configuration

| VLAN | Assigned Ports | SVI Address |
|---|---|---|
| 50 | Fa0/1, Fa0/2 | 1.0.0.10/8 |
| 60 | Fa0/3, Fa0/4 | 2.0.0.10/8 |

VLAN 50 contains the devices connected to Fa0/1 and Fa0/2, while VLAN 60 contains the devices connected to Fa0/3 and Fa0/4.

## SVI Configuration

I configured an SVI for each VLAN:

```text
interface Vlan50
 ip address 1.0.0.10 255.0.0.0

interface Vlan60
 ip address 2.0.0.10 255.0.0.0
```

Layer 3 routing was enabled on the multilayer switch using:

```text
ip routing
```

This allows the switch to route traffic between VLAN 50 and VLAN 60 without using an external router.

## Verification

I used the following commands to check the configuration:

```text
show vlan brief
show ip interface brief
show running-config | section interface Vlan
show running-config | include ip routing
```

These confirmed the VLAN assignments, SVI addresses, and that IP routing was enabled.

## What I Learned

This lab helped me understand how a multilayer switch can handle both Layer 2 switching and Layer 3 routing.

Compared with router-on-a-stick, SVIs allow inter-VLAN routing to happen directly on the multilayer switch instead of sending traffic through an external router.

It also helped me understand the role of an SVI as the Layer 3 gateway for devices within a VLAN.

## Lab File

[`svi-configuration.pkt`](svi-configuration.pkt)