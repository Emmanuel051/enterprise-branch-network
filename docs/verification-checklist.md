# Verification Checklist

- [x] VLANs created and assigned to the correct access ports
- [x] Static trunks use 802.1Q, native VLAN 1000, DTP disabled
- [x] LACP EtherChannels operational
- [x] Rapid PVST+ enabled; DIST-SW is root for production VLANs
- [x] PortFast/BPDU Guard enabled on end-host ports
- [x] SVIs up/up and inter-VLAN routing operational
- [x] DHCP relay points to `10.10.40.10`
- [x] DHCP clients receive correct addresses/gateways/DNS
- [x] DNS resolves `www.emmanuel.com` to `10.10.40.10`
- [x] R1 and DIST-SW OSPF adjacency is FULL
- [x] R1 learns/advertises required routes and default information
- [x] PAT translates inside clients to `203.0.113.2`
- [x] Both Cisco 7960 phones register to CME as 1001/1002
- [x] NTP synchronization verified
- [x] SALES_TO_FINANCE ACL behavior verified
- [x] Port Security learns one sticky MAC on selected access ports
- [x] SSH allowed from IT VLAN and denied from non-IT VLANs
- [x] DHCP Snooping/DAI tested; simulator limitation documented
