# Standard ACL — Network Access Control Lab

## Overview

This lab demonstrates the configuration and application of a **named Standard Access Control List (ACL)** in Cisco Packet Tracer.

The ACL is used to control access to a destination network by filtering traffic based on source IPv4 addresses.

## Objectives

- Configure a named Standard ACL on a Cisco router
- Permit and deny traffic based on source IP networks
- Apply an ACL to a router interface
- Understand outbound ACL placement
- Observe top-down ACL processing and first-match behavior
- Verify ACL operation using Cisco IOS commands

## Network Topology

![Standard ACL Network Topology](topology.png)

The topology consists of:

- 2 Cisco 2811 routers
- 2 Cisco 2960 switches
- 4 client PCs
- 1 server
- Multiple LAN segments connected through Router0
- A routed connection between Router0 and Router1

Router1 provides connectivity toward the server network and is responsible for applying the Standard ACL.

## ACL Configuration

A named Standard ACL called `ben` was configured on Router1.

```text
ip access-list standard ben
 10 deny 192.168.10.0 0.0.0.255
 20 deny host 192.168.10.2
 30 permit 192.168.10.0 0.0.0.255
 40 deny 192.168.20.0 0.0.0.255
 50 permit any