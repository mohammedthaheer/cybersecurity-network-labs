# Extended Numbered ACL — Protocol & Service Filtering Lab

## Overview

This lab demonstrates the configuration and application of a **numbered Extended Access Control List (ACL)** using Cisco Packet Tracer.

Extended ACLs provide granular traffic filtering by allowing network administrators to match traffic based on source address, destination address, protocol, and application port.

In this lab, Extended ACL `120` is used to restrict selected ICMP and HTTP traffic while allowing other IP traffic.

## Objectives

- Configure a numbered Extended ACL
- Filter traffic based on source and destination networks
- Restrict ICMP echo traffic
- Restrict HTTP traffic from a specific host
- Apply an ACL to a router interface
- Understand first-match ACL processing
- Verify ACL configuration using Cisco IOS commands

## Network Topology

![Extended Numbered ACL Network Topology](topology.png)

The topology consists of multiple client networks connected through routers to a destination network.

Router2 applies the Extended ACL to traffic leaving the interface toward the `10.0.0.0/8` destination network.

## ACL Configuration

Extended ACL `120` was configured on Router2.

```text
access-list 120 deny icmp 192.168.10.0 0.0.0.255 10.0.0.0 0.255.255.255 echo
access-list 120 deny tcp host 192.168.20.1 10.0.0.0 0.255.255.255 eq www
access-list 120 permit ip any any