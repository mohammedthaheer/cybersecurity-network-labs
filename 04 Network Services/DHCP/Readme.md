# DHCP Configuration

This lab demonstrates DHCP configuration using a Cisco router as the DHCP server.

## Configuration

The router was configured with a DHCP pool for the `192.168.1.0/24` network.

- Default gateway: `192.168.1.1`
- DHCP pool: `ben`
- Router address `192.168.1.1` was excluded from DHCP assignment

The PCs and laptops were configured to obtain their IP addresses automatically using DHCP.

## Verification

The DHCP configuration was verified using:

- `show ip dhcp pool`
- `show ip dhcp binding`
- `show running-config | section dhcp`

All 6 end devices successfully received IP addresses from the DHCP server.