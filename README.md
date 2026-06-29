# SecureNet Enterprise Network Design

This repository contains the Cisco Packet Tracer implementation for the **SecureNet Technologies Enterprise Network Design and Implementation** coursework project. The topology demonstrates a secure, scalable, and monitored enterprise network for a headquarters and branch office environment.

## Project Overview

The project demonstrates an enterprise network built in Cisco Packet Tracer. It includes a three-tier architecture, departmental VLAN segmentation, routing, redundancy, firewall protection, DMZ services, centralized monitoring, secure guest wireless access, and site-to-site IPsec VPN configuration evidence.

The main goal is to show how an enterprise network can be designed to support security, reliability, scalability, and future expansion.

## Network Features

- Three-tier network architecture: Core, Distribution, and Access layers
- Headquarters and branch office connectivity
- VLAN segmentation for departments and services
- 802.1Q trunking between switches
- VTP for VLAN management
- STP and BPDU Guard for loop prevention and rogue switch protection
- EtherChannel for link aggregation and redundancy
- HSRP demonstration for first-hop gateway redundancy
- DHCP with multiple pools for different VLANs
- Inter-VLAN routing
- Static and default routing
- Cisco ASA firewall with inside, outside, and DMZ zones
- DMZ services for public-facing servers
- ACL and firewall-zone based traffic control
- Site-to-site IPsec VPN configuration evidence
- Guest wireless network using WLC/wireless infrastructure
- AAA/RADIUS authentication configuration
- Centralized services:
  - DHCP
  - DNS
  - FTP
  - Email using SMTP/POP3
  - Web server
  - NTP
  - Syslog
  - SNMP

## Topology Summary

| Area | Purpose |
| --- | --- |
| Headquarters | Main enterprise network with users, servers, firewall, and monitoring |
| Branch Office | Remote site connected through WAN/ISP infrastructure |
| Core Layer | Handles inter-VLAN routing and main network forwarding |
| Distribution Layer | Provides aggregation, trunking, EtherChannel, and redundancy |
| Access Layer | Connects PCs, laptops, wireless clients, and end devices |
| DMZ | Hosts public-facing services such as web, FTP, DNS, and email |
| Guest Wireless | Provides separated wireless access for visitors |
| WAN/ISP | Simulates external connectivity and branch communication |

## VLAN and Addressing Overview

| VLAN | Network | Purpose |
| --- | --- | --- |
| VLAN 10 | 10.0.10.0/24 | Management |
| VLAN 20 | 10.0.20.0/24 | Finance |
| VLAN 30 | 10.0.30.0/24 | Human Resources |
| VLAN 40 | 10.0.40.0/24 | IT / Internal Services |
| VLAN 50 | 10.0.50.0/24 | Guest WiFi |
| VLAN 60 | 10.0.60.0/24 | DMZ Services |
| Branch VLANs | 10.110.x.0/24 | Branch departments |

## Key Services

| Service | Device | IP Address |
| --- | --- | --- |
| DHCP | HO-DHCP-SRV | 10.0.40.50 |
| NTP | HO-NTP-SRV | 10.0.40.20 |
| Syslog | HO-SYSLOG-SRV | 10.0.40.40 |
| AAA/RADIUS | HO-AAA-SRV / HO-RADIUS-SRV | 10.0.40.60 / 10.0.40.61 |
| DNS | HO-DNS-SRV | 10.0.60.10 |
| Web | HO-WEB-SRV | 10.0.60.20 |
| FTP | HO-FTP-SRV | 10.0.60.30 |
| Email | HO-EMAIL-SRV | 10.0.60.40 |

## Security Design

Security is implemented using multiple layers of protection. VLANs separate departments to reduce unnecessary broadcast traffic and limit access between user groups. The ASA firewall separates trusted internal traffic from the DMZ and outside networks. ACLs and firewall security zones are used to control traffic flow, with NAT discussed as part of the firewall design.

The guest wireless network is placed in a separate VLAN to prevent visitors from accessing internal company systems. AAA/RADIUS is used for centralized authentication, while Syslog and SNMP support monitoring, auditing, and troubleshooting.

## Services Demonstrated

The project includes Packet Tracer server services for DHCP, DNS, web hosting, FTP, email, NTP, Syslog, SNMP, and AAA/RADIUS. DHCP assigns IP addresses to clients, DNS resolves internal service names, the web server hosts a SecureNet portal, FTP supports file transfer, and email is configured for SMTP/POP3 communication. NTP synchronizes device time, while Syslog and SNMP provide centralized monitoring evidence.

## How to Open the Project

1. Install Cisco Packet Tracer.
2. Open the `.pkt` file in Cisco Packet Tracer.
3. Wait for the network devices to fully load.
4. Use the topology labels to explore devices and services.
5. Test connectivity using ping, web browser, email, FTP, and device CLI commands.

## Useful Verification Commands

```cisco
show ip interface brief
show ip route
show vlan brief
show interfaces trunk
show spanning-tree
show etherchannel summary
show standby brief
show running-config
show access-list
show running-config | include crypto
show running-config | include tunnel-group
show crypto ipsec sa
show running-config | include logging
show running-config | include snmp
```

## Testing Suggestions

Use the following checks to verify the implementation:

- PCs receive IP addresses through DHCP.
- VLANs are correctly assigned.
- Trunk links are active.
- Inter-VLAN routing works.
- HSRP virtual gateway configuration is visible.
- EtherChannel links are bundled.
- DMZ servers are reachable.
- DNS resolves service names.
- Web and FTP services work from client devices.
- Email SMTP/POP3 settings are configured and tested where Packet Tracer allows.
- Syslog receives device logs.
- SNMP communities are configured.
- Guest wireless clients connect successfully.
- ASA firewall zones and ACLs are configured.
- VPN-related crypto maps, tunnel groups, and ACLs are present.

## Notes on Routing and VPN

The final tested topology mainly uses static routes, default routes, and inter-VLAN routing because the WAN path is small and predictable. OSPF and BGP are discussed in the coursework report as scalable routing alternatives for larger enterprise or ISP environments.

The site-to-site IPsec VPN parameters are configured on both ASA firewalls using matching crypto ACLs, transform sets, tunnel groups, and pre-shared keys. Packet Tracer ASA limitations may prevent full IPsec SA formation, so the report includes VPN configuration evidence and WAN reachability tests.

## Tools Used

- Cisco Packet Tracer
- Cisco routers
- Cisco switches
- Cisco ASA firewall
- Wireless LAN Controller / wireless router
- Packet Tracer servers and end devices

## Project Purpose

This project was created for the **ST5064CEM Networking** coursework scenario. It demonstrates practical understanding of enterprise network design, routing, switching, security, monitoring, services, and governance using Cisco Packet Tracer.

## Disclaimer

This project is for educational and demonstration purposes only. It is built in Cisco Packet Tracer and may not include every control, hardening step, or production-grade configuration required for a real enterprise network.
