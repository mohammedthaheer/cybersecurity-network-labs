# Extended Named ACL — Protocol & Service Filtering Lab

## Overview

This lab demonstrates the configuration and application of a **named Extended Access Control List (ACL)** using Cisco Packet Tracer.

Unlike Standard ACLs, Extended ACLs can filter traffic based on multiple criteria including source address, destination address, protocol, and application port.

The lab uses an Extended ACL named `ben` to control ICMP and TCP traffic travelling toward the destination network.

## Objectives

- Configure a named Extended ACL
- Filter traffic based on source and destination addresses
- Control ICMP echo traffic
- Apply protocol-specific access-control rules
- Apply an ACL to a router interface
- Understand ACL rule ordering and first-match processing
- Verify ACL configuration using Cisco IOS commands

## Network Topology

![Extended Named ACL Network Topology](topology.png)

The topology consists of multiple client networks connected through routers to a destination network.

The Extended ACL is configured on Router2 and applied to the interface leading toward the destination network.

## ACL Configuration

A named Extended ACL called `ben` was configured on Router2.

```text
ip access-list extended ben
 10 deny icmp 192.168.20.0 0.0.0.255 10.0.0.0 0.255.255.255 echo
 20 deny icmp host 192.168.10.2 10.0.0.0 0.255.255.255 echo
 30 permit ip any any
 40 deny tcp host 192.168.10.1 10.0.0.0 0.255.255.255 eq www