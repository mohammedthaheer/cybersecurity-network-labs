# STP, RSTP & PortFast Lab

## Overview

Used Cisco Packet Tracer to practice **Spanning Tree Protocol (STP), Rapid Spanning Tree Protocol (RSTP), and PortFast**.

The lab contains separate switch setups for observing spanning-tree behavior and configuring PortFast on end-device ports.

## Topology

![STP RSTP PortFast Topology](topology.png)

## Rapid STP

The switches on the left side were configured to use Rapid PVST+:

```text
spanning-tree mode rapid-pvst
```

Switch6 was elected as the root bridge for VLAN 1.

```text
Spanning tree enabled protocol rstp
This bridge is the root
```

On Switch8, I observed the different spanning-tree port roles:

```text
Fa0/1   Root   FWD
Fa0/2   Desg   FWD
```

Fa0/1 is the root port used to reach the root bridge, while Fa0/2 is operating as a designated forwarding port.

## PortFast

On the separate access switch, PortFast was enabled on the ports connected to end devices:

```text
interface FastEthernet0/1
 spanning-tree portfast

interface FastEthernet0/2
 spanning-tree portfast

interface FastEthernet0/3
 spanning-tree portfast

interface FastEthernet0/4
 spanning-tree portfast
```

PortFast allows access ports connected to end devices to move to the forwarding state without waiting through the normal STP transition process.

The switch was running traditional IEEE spanning tree:

```text
Spanning tree enabled protocol ieee
```

## Verification

I used:

```text
show spanning-tree
show running-config | include spanning-tree
show running-config | section FastEthernet
```

These helped me check the spanning-tree mode, root bridge, port roles and PortFast configuration.

## What I Learned

This lab helped me understand how STP selects a root bridge and assigns different roles to switch ports.

I also compared traditional STP with Rapid STP and practiced using PortFast on ports connected directly to end devices.

One thing I noticed while reviewing the lab was that not every physical link in the triangle was participating in the spanning-tree output. This was a useful reminder to verify interface state instead of assuming a link is active just because it appears connected in the topology.

## Lab File

[`stp-rstp-portfast.pkt`](stp-rstp-portfast.pkt)