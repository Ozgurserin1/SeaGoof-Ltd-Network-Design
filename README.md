# SeaGoof Ltd — Enterprise Network Design

### Cisco Packet Tracer | Network Administration | Bath Spa University

A three-floor enterprise network design and evaluation project developed using Cisco Packet Tracer. The project demonstrates VLAN segmentation, inter-VLAN routing, dynamic IP addressing, wireless connectivity, internal business services, and network security verification.

## 1. Project Overview

SeaGoof Ltd is a medium-sized company relocating to a new office in Ulverston, Cumbria, United Kingdom.

The network is designed to support 100 employees across three floors, with separate staff and guest networks, wired infrastructure, and centrally managed network services.

The project evaluates the implementation, documents its strengths and limitations, and proposes improvements for production deployment.

## 2. Network Architecture

The Cisco Packet Tracer v12 implementation uses a hierarchical star topology.

- Cisco 2911 router for inter-VLAN routing and DHCP
- Central core switch for VLAN trunk aggregation
- Eight Cisco 2960 access switches
- Separate staff and guest wireless networks
- Internal DNS, web, SMTP and POP3 services
- Router-based access control lists for guest network segmentation

The current simulation uses separate physical employee and guest access points. The proposed production design consolidates these into one multi-SSID enterprise access point per floor, in accordance with the assessment requirements.

## 3. VLAN and IP Addressing

| VLAN | Network | Purpose |
|---|---|---|
| 10 | 192.168.10.0/24 | Basement Staff |
| 20 | 192.168.20.0/24 | Ground Floor Staff |
| 30 | 192.168.30.0/24 | First Floor Staff |
| 40 | 192.168.40.0/24 | Basement Guests |
| 50 | 192.168.50.0/24 | Ground Floor Guests |
| 60 | 192.168.60.0/24 | First Floor Guests |
| 99 | 192.168.99.0/24 | Network Management |

Each network uses a /24 subnet mask. Router subinterfaces provide gateway addresses ending in .1.

## 4. Network Services

The implementation demonstrates:

- DHCP address allocation across six client VLANs
- DNS resolution for www.seagoof.com
- Internally hosted SeaGoof Ltd website
- SMTP and POP3 email communication
- Wired connectivity between employee networks
- Wireless connectivity for staff and visitors

The internal business-services host uses IP address `192.168.10.10`.

## 5. Cybersecurity

Security features evaluated in the project include:

- VLAN-based staff and guest separation
- Inbound guest ACLs on router subinterfaces
- WPA2-PSK with AES for tested wireless clients
- Restricted ICMP access from guest networks to internal resources
- Separate management VLAN

Additional production recommendations include stronger wireless authentication, controlled administrative access, central logging, configuration backups, and improved equipment resilience.

## 6. Testing and Verification

The project report includes 15 key verification tests and an extended evidence catalogue.

Documented tests include:

- DHCP address and gateway assignment
- Gateway and server connectivity
- DNS name resolution
- Corporate website accessibility
- Bidirectional email communication
- Guest network ICMP isolation
- ACL attachment verification
- DHCP conflict-register inspection
- Router configuration saving

Recorded successful tests apply to the specific devices and conditions examined. They do not establish complete production readiness or verified external Internet connectivity.

## 7. Project Documentation

The repository is intended to contain:

- Final Cisco Packet Tracer simulation
- Network topology diagrams
- Network design and evaluation report
- Selected configuration and testing evidence
- Troubleshooting and corrective-action records

## 8. Cost Evaluation

The assessment report presents an illustrative production deployment budget:

| Category | Estimated Cost |
|---|---:|
| One-off capital and installation | £20,400 |
| Annual support allowance | £1,200/year |

These figures are planning assumptions, not verified supplier quotations.

## 9. Educational Security Notice

This repository documents an educational network simulation created using Cisco Packet Tracer.

Any demonstration credentials included in the project are intended exclusively for simulated systems and must not be reused in real-world or production environments.

## 10. Project Status

**Version:** v12  
**Environment:** Cisco Packet Tracer  
**Assessment:** Network Administration — Network Design Task  
**Institution:** Bath Spa University

The documented simulation tests demonstrate core network functionality. Wireless hardware consolidation, production resilience and live ISP connectivity remain outside the verified implementation.

---

*SeaGoof Ltd — Network Design and Evaluation Project*
