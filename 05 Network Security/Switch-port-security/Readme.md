# Switch Port Security — Sticky MAC Address Lab

## Overview

This lab demonstrates the configuration of **Cisco Switch Port Security** in Packet Tracer to restrict access to a switch port based on MAC addresses.

Port security is enabled on an access port connected to a client device. The switch uses **sticky MAC address learning** to dynamically learn and secure the connected device's MAC address.

The port is configured to allow a maximum of one secure MAC address and uses the **shutdown** violation mode.

## Objectives

- Configure a switch interface as an access port
- Enable switch port security
- Configure sticky MAC address learning
- Limit the number of allowed MAC addresses
- Understand port-security violation modes
- Verify secure MAC address learning
- Examine the security status of a switch interface

## Network Topology

![Switch Port Security Topology](topology.png)

The topology contains:

- 1 Cisco 2960 switch
- 2 client PCs
- 1 server

PC3 is connected to the secured FastEthernet0/1 interface.

Server0 is connected through FastEthernet0/2.

PC4 is available as an additional endpoint for testing changes in device connectivity.

## Port Security Configuration

Port security was configured on FastEthernet0/1:

```text
interface FastEthernet0/1
 switchport mode access
 switchport port-security
 switchport port-security mac-address sticky