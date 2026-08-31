# NAT/PAT Configuration

Cisco Packet Tracer lab where I configured NAT with overload (PAT) to allow devices from a private network to communicate with an outside network using a translated public IP address.

## Topology

The network consists of:

- 3 PCs on the inside network
- 1 switch
- 2 routers
- 1 server on the outside network

## Configuration

The inside network uses the `192.168.10.0/24` network.

Router1 was configured with:

- `FastEthernet0/0` as the NAT inside interface
- `Serial0/2/0` as the NAT outside interface
- An ACL to match the `192.168.10.0/24` network
- NAT pool `test1` using `50.0.0.15`
- NAT overload to allow multiple inside devices to share the translated address

Main NAT configuration:

```cisco
access-list test permit 192.168.10.0 0.0.0.255

ip nat pool test1 50.0.0.15 50.0.0.15 netmask 255.0.0.0

ip nat inside source list test pool test1 overload