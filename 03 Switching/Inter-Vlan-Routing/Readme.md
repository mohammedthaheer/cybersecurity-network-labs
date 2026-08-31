# Inter-VLAN Routing Lab

## Overview

Configured inter-VLAN routing using the **router-on-a-stick** method in Cisco Packet Tracer.

The network contains two VLANs connected through a Layer 2 switch. A trunk link between the switch and router allows Router0 to route traffic between the two VLANs.

## Topology

![Inter-VLAN Routing Topology](topology.png)

## VLAN Configuration

| VLAN | Name | Ports | Network |
|------|------|-------|---------|
| 100 | s/w | Fa0/1, Fa0/2 | 192.168.10.0/24 |
| 200 | i/t | Fa0/3, Fa0/4 | 192.168.20.0/24 |

The switch port connected to Router0 (`Fa0/5`) was configured as a trunk.

```text
interface FastEthernet0/5
 switchport mode trunk
```

## Router Configuration

I created two subinterfaces on Router0 for the two VLANs.

### VLAN 100

```text
interface FastEthernet0/0.100
 encapsulation dot1Q 100
 ip address 192.168.10.100 255.255.255.0
```

### VLAN 200

```text
interface FastEthernet0/0.200
 encapsulation dot1Q 200
 ip address 192.168.20.100 255.255.255.0
```

The router addresses act as the default gateways for their respective VLANs.

## Verification

I used the following commands to check the configuration:

```text
show vlan brief
show interfaces trunk
show running-config | section FastEthernet
```

The trunk was up and carrying VLANs 100 and 200.

## What I Learned

This lab helped me understand how VLANs separate devices into different broadcast domains and why a Layer 3 device is required for communication between VLANs.

It also gave me hands-on practice with **802.1Q trunking, router subinterfaces, access ports, and default gateways**.

From a security perspective, VLAN segmentation can be used to separate different groups of devices, while controls such as ACLs can later be added to restrict traffic between those networks.

## Lab File

[`inter-vlan-routing.pkt`](inter-vlan-routing.pkt)