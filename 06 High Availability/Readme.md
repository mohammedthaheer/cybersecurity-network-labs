# HSRP High Availability Lab

## Overview

This lab demonstrates the implementation of **HSRP (Hot Standby Router Protocol)** in Cisco Packet Tracer to provide default gateway redundancy.

Two routers are configured in the same HSRP group and share a virtual IP address. One router operates as the **Active router**, while the other operates as the **Standby router**.

A failure was simulated on the Active router to verify that the Standby router automatically takes over the virtual gateway.

---

## Topology

The network consists of:

- 2 client PCs
- 1 Layer 2 switch
- 2 HSRP routers
- 1 upstream/ISP router

The two HSRP routers connect the LAN to the upstream router and provide redundant gateway connectivity for the end devices.

---

## IP Addressing

| Device | Interface | IP Address | Purpose |
|---|---|---|---|
| Router1 | Fa0/0 | 192.168.10.10 | HSRP LAN interface |
| Router1 | Fa0/1 | 2.0.0.1 | Upstream connection |
| Router2 | Fa0/0 | 192.168.10.50 | HSRP LAN interface |
| Router2 | Fa0/1 | 3.0.0.2 | Upstream connection |
| ISP Router | Fa0/0 | 2.0.0.2 | Connection to Router1 |
| ISP Router | Fa0/1 | 3.0.0.1 | Connection to Router2 |
| HSRP Virtual Gateway | — | 192.168.10.20 | Default gateway for LAN hosts |

---

## HSRP Configuration

Both routers participate in **HSRP Group 1** using the virtual IP address:

```text
192.168.10.20