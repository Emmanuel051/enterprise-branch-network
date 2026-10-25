# Troubleshooting Notes

## DHCP clients received APIPA addresses

### Symptom
Multiple PCs received `169.254.x.x/16` addresses with no usable default gateway after access-layer security features were introduced.

### Evidence
- Layer 3 SVIs on DIST-SW remained up/up.
- DHCP helper configuration remained present.
- The DHCP/DNS server retained `10.10.40.10/24` and gateway `10.10.40.1`.
- DHCP Snooping was enabled on the access switches.
- `show ip dhcp snooping binding` returned zero bindings.
- Disabling DHCP Snooping allowed clients to immediately receive normal `10.10.x.x` leases.

### Root Cause
In this Packet Tracer topology, DHCP Snooping did not behave reliably with the EtherChannel-based uplink path. Legitimate DHCP exchanges failed even though the physical member ports were configured as trusted.

### Resolution
DHCP Snooping and DAI were disabled in the final stable simulation. Other security controls remained in place.

### Key Takeaway
When multiple VLANs simultaneously lose DHCP, investigate shared DHCP infrastructure and newly introduced security controls before assuming the problem is an SVI, default gateway, or endpoint issue. APIPA (`169.254.0.0/16`) is an immediate clue that DHCP negotiation failed.

## SSH Management Validation

A standard ACL was applied to VTY lines to permit remote management only from IT VLAN 10. SSH from an IT host succeeded, while an attempt from a non-IT user network was rejected/closed.

## OSPF Validation

R1 and DIST-SW reached FULL adjacency across `10.10.254.0/30`. Internal VLANs were advertised from DIST-SW, and R1 originated the default route toward the internal network.
