# DNS Server Configuration

Cisco Packet Tracer lab where I configured a DNS server and tested hostname resolution from client devices.

## Topology

The network consists of:

- 1 DNS server
- 1 switch
- 3 PCs
- 3 laptops

All devices are connected within the same LAN.

## DNS Configuration

The server was configured with:

- IP address: `192.168.1.10`
- Subnet mask: `255.255.255.0`
- DNS service enabled

An A record was created:

| Name | Type | Address |
|------|------|---------|
| www.google.com | A Record | 192.168.1.10 |

This allows clients to resolve `www.google.com` to the server IP address.

## Client Configuration

Client devices were configured to use:

`192.168.1.10`

as their DNS server.

## Verification

DNS resolution was tested from a client using:

```cmd
ping www.google.com