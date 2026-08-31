# VTP Configuration Lab

## Overview

Configured **VLAN Trunking Protocol (VTP)** across multiple Cisco multilayer switches in Packet Tracer.

The lab uses VTP Server, Client, and Transparent modes to see how VLAN information is shared between switches.

## Topology

![VTP Configuration Topology](topology.png)

Four multilayer switches are connected using trunk links.

## VTP Setup

The switches use the VTP domain:

```text
cisco.com
```

VTP version 1 is running in the lab.

| Switch | VTP Mode | VLAN Information |
|---|---|---|
| Switch0 | Server | VLAN 10 - `ben` |
| Switch1 | Transparent | VLAN 20 - `gwen` |
| Switch2 | Client | VLAN 10 - `ben` |
| Switch3 | Client | VLAN 10 - `ben` |

## VTP Server

Switch0 is configured as the VTP Server.

```text
VTP Operating Mode : Server
VTP Domain Name     : cisco.com
VTP Version         : 1
Configuration Revision : 4
```

VLAN 10 (`ben`) exists on the server.

## VTP Clients

Switch2 and Switch3 are running in Client mode.

Both switches learned VLAN 10 (`ben`) and show the same configuration revision number as the VTP server:

```text
VTP Operating Mode    : Client
Configuration Revision: 4
```

This confirmed that the VLAN information was successfully propagated through the VTP domain.

## Transparent Switch

Switch1 is configured in VTP Transparent mode.

It has its own locally configured VLAN:

```text
VLAN 20 - gwen
```

Its VTP configuration revision remains `0`, and VLAN 10 from the VTP server is not added to its local VLAN database.

## Trunking

The switches are connected using 802.1Q trunk links so VLAN and VTP traffic can pass between them.

On Switch0, the trunk status was verified using:

```text
show interfaces trunk
```

## Verification

I used these commands while checking the lab:

```text
show vtp status
show vlan brief
show interfaces trunk
```

I compared the VTP mode, domain, configuration revision, and VLAN database across the switches to verify the setup.

## What I Learned

This lab helped me understand the difference between **VTP Server, Client, and Transparent modes**.

I also got a better understanding of the VTP configuration revision number and how VLAN changes made on the server can be distributed to client switches.

The transparent switch was useful for seeing how a switch can participate in the topology while maintaining its own local VLAN configuration.

## Lab File

[`vtp-configuration.pkt`](vtp-configuration.pkt)